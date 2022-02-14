Topic: 4G LTE<br>
Sub-Topic: eMTC<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/02/12<br>

---

#### MIB Repetitions

Refer [1] [2]

1. The MIB is intended for both eMTC Cat M1 UE and common UE. 
2. A preserved field in the MIB is used to indicate the SIB1-BR scheduling information. 

***Basic Concepts***

1. The MIB scheduling period is always 40ms. 
2. During a scheduling period, the MIB is repeatedly sent in subframes 0 and 9 of each frame [In Case of FDD], 0 and 5 [In Case of TDD]. 
3. MIB repetitions made within 40 ms. 
4. The first transmission of the MIB is scheduled in subframe #0 of radio frames for which the SFN mod 4 = 0. 
5. MIB repetitions are scheduled in subframe #0 of all other radio frames.  
6. For TDD/FDD system with a bandwidth larger than 1.4 MHz that supports BL UEs or UEs in CE, MIB transmission may be repeated   in subframe #9 of the previous radio frame for    FDD and subframe  #5 of the same radio frame for TDD. 

<br>
<img src="\lte_emtc\img\lte_emtc_mibrep.png" width=100% height=100% />
<br>

<br>
<img src="\lte_emtc\img\lte_emtc_mibrep.png" width=100% height=100% />
<br>

---

#### SIB 1 BR Repetitions

Refer [3] [4] [5]

1. schedulingInfoSIB1-BR is specified in MIB. 
2. The scheduling period of SIB1-BR is 80ms. SIB 1 BR carry cell selection Info and scheduling for other SIBs. 
3. Pre defined table is being used to determine the location of frequency domain & time domain for SIB 1 BR. 
4. Pre defined table will determine number of PDSCH repetitions for SIB 1 BR, TBS Index for PDSCH SIB 1 BR, and resource location of SIB 1 BR. 

<br>
<img src="\lte_emtc\img\lte_emtc_sib1br.png" width=100% height=100% />
<br>

Table for easy copy:

| schedulingInfoSIB1-BR-r13  | PDSCH repetitions  |
|----------------------------|--------------------|
| 0                          | N/A                |
| 1                          | 4                  |
| 2                          | 8                  |
| 3                          | 16                 |
| 4                          | 4                  |
| 5                          | 8                  |
| 6                          | 16                 |
| 7                          | 4                  |
| 8                          | 8                  |
| 9                          | 16                 |
| 10                         | 4                  |
| 11                         | 8                  |
| 12                         | 16                 |
| 13                         | 4                  |
| 14                         | 8                  |
| 15                         | 16                 |
| 16                         | 4                  |
| 17                         | 8                  |
| 18                         | 16                 |
| 19-31                      | Reserved           |


| ITBS  | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | 10   | 11   | 12   | 13   | 14   | 15   | 16   | 17   | 18   | 19        | 20        | 21        | 22        | 23        | 24        | 25        | 26        | 27        | 28        | 29        | 30        | 31       |
|-------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|----------|
| TBS   | N/A  | 208  | 208  | 208  | 256  | 256  | 256  | 328  | 328  | 328  | 504  | 504  | 504  | 712  | 712  | 712  | 936  | 936  | 936  | Reserved  | Reserved  | Reserved  | Reserved  | Reserved  | Reserved  | Reserved  | Reserved  | Reserved  | Reserved  | Reserved  | Reserved  | Reserved |

---

#### CE Level Selection Criteria

The important thing is how UE consider itself to be in specific CE based on RSRP measurement. Based on 3GPP, UE shall consider to be in the designated CE Level when measured RSRP is < than Threshold in Higher Layer. It means if your index value translated into table range, when UE RSRP is less than the range, UE should consider itself to be in lower CE Level. [6] 

<br>
<img src="\lte_emtc\img\lte_emtc_ceselect.png" width=100% height=100% />
<br>

---

#### CE Level Conversion 

Based on 3GPP, RSRP threshold for CE level is mapped into RSRP range information element table. [7]

<br>
<img src="\lte_emtc\img\lte_emtc_ceconv.png" width=100% height=100% />
<br>

<br>
<img src="\lte_emtc\img\lte_emtc_ceconv2.png" width=100% height=100% />
<br>

In some cases, vendors and UE might have different understanding on how to covert this value to a CE level value. For example, in this case TEMS using lower limit in their tool while XCAP using upper limit. 3GPP only define a range of RSRP for each index, maybe to save some index space. [8]

<br>
<img src="\lte_emtc\img\lte_emtc_ceconv3.png" width=100% height=100% />
<br>

***Easy Tips***

If SIB 2 Threshold says 15, Change CE Level when RSRP < -126dBm 

| CE Level Change Value  | SIB 2 IE  |
|------------------------|-----------|
| -126  <= X < -125      | (15)      |

---

#### CE Level Switching in Connected Mode

1. CE Level can only be change if UE have a chance to do RACH. 
2. In Rel 13, handover is not supported in eMTC, hence the only way to select CE Level is during Initial Access RACH. 
3. In Rel 14, handover is supported in eMTC. 
4. In Rel 14, few handover concepts has been introduces for eMTC as follows. This section focus only on CE Mode Switching. 


    - Handover within same cell (CE Level/Mode Switching Concept) 
    - Intra Frequency Handover Between Cells 
    - Inter Frequency Handover Between Cells 
    - Emergency Inter Frequency Blind Redirection Between Cells 
    - Emergency Inter RAT Blind Redirection Between Cells 

***CE Level/Mode Switching Concept***

Handover within the same cells. Whether it is between CE Modes, between CE Levels, or between CE Modes and Levels depending on vendor/device support. 

***CE Level Switching Procedure***

Similar like normal handover: 

1. UE needs to report MR based on triggering threshold. Triggering event is based on vendor. 
2. After eNB received that event has been triggered, eNB will send RRC Connection Reconfiguration containing Mobility Control Info. 
3. UE will accept handover within same cells (CE Level switching) by sending RRC Connection Reconfiguration Complete. 

Example from logfiles:

<br>
<img src="\lte_emtc\img\lte_emtc_ceswitch.png" width=100% height=100% />
<br>

***Connected vs Idle Mode***

<br>
<img src="\lte_emtc\img\lte_emtc_ceswitch.png" width=100% height=100% />
<br>

***Triggering Threshold for CE Level Switching***

Different vendor might use different measurement event or no measurement event at all for same operation. Some vendor even utilize UL SINR to support the operation.

<br>
<img src="\lte_emtc\img\lte_emtc_ceswitch3.png" width=100% height=100% />
<br>

<br>
<img src="\lte_emtc\img\lte_emtc_ceswitch4.png" width=100% height=100% />
<br>


---

#### References

1. 3GPP TS 36.331 Section 5.2.1.2 
2. 3GPP TS 36.213 Section 7.1.6 
3. 3GPP TS 36.213 Section 7.1.6 
4. 3GPP TS 36.213 Section 7.1.7.2.7 
5. 3GPP TS 36.211 Section 6.4.1
6. 3GPP TS 36.321 Section 5.1.1
7. 3GPP TS 36.331
8. 3GPP TS 36.133 Section 9.1.4