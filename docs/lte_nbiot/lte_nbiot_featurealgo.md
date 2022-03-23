Topic: 4G LTE<br>
Sub-Topic: NB-IoT<br>
Date Written: 2019/05/18<br>
Date Edited: 2022/03/22<br>

---

#### NRS Signal Boost

1. NB-IoT support NB-IoT power boosting at least 6dB.
2. Incase of LTE in band deployment, LTE RE power is being trade off to achieve NRS boost.

<mark>3GPP Minimum Requirements:</mark> [1]

?> NB-IoT power dynamic range shall be larger than or equal to +6dB except for guard band operation with E-UTRA 5 MHz channel bandwidth signal.

?> The +6 dB power dynamic range is only required for one NB-IoT RB for both in-band and guard band operation modes.

Table form [2]

| System BW  | RBG Size  |
|------------|-----------|
| 1.4        | 1         |
| 3          | 2         |
| 5          | 2         |
| 10         | 3         |
| 15         | 4         |
| 20         | 4         |

<br>
<img src="\lte_nbiot\img\lte_nbiot_nrsboost.png" width=100% height=100% />
<br>

?> Note: All RE in NB-IoT PRB is 6dB boost from common LTE. This include NRS and also Non-NRS RE.

    Eg:
    LTE CRS RE = 20dBm, so LTE NRS RE = 26dBm
    LTE Non CRS RE = 17dBm, so LTE Non NRS RE = 23dBm

---

#### Coverage Level (CE Level)

1. Coverage enhancement (CE) are introduced to adapt to the coverage depth and capacity performance requirements of NB-IoT UE.
2. Dividing the coverage allowing UE to selects an appropriate coverage level based on the signal strength to provide reliable transmission in poor RF without trading off good performance in good RF.
3. NB-IoT supports three CE levels: 0, 1, and 2.
4. To achieve deep coverage, number of repetitions can be set separately for different coverage areas.

<br>
<img src="\lte_nbiot\img\lte_nbiot_cel.png" width=100% height=100% />
<br>

---

#### Physical Channel Repetitions Structures

1. Physical channel repetitions is also one important features in NB-IoT.
2. Repetition is a technique consisting on repeating the same data transmission several times to ensure its reliability.
3. In areas with good coverage, high data rates can be reached using a few repetitions or even without repetition. In areas with poor coverage, coverage performance can be ensured by using more repetitions.
4. These repetitions settings can be divided based on Coverage Level concept, meet objective to extend coverage.

<br>
<img src="\lte_nbiot\img\lte_nbiot_repstruct.png" width=100% height=100% />
<br>

| L3 Msg | Phy Channel Repetition       | L3 Parameter Name | CE Level 0 | CE Level 1 | CE Level 2 |
|--------|------------------------------|-------------------|------------|------------|------------|
| SIB2   | ① NPDCCH for Paging          |                   | X          | X          | X          |
| SIB2   | ② NPDCCH for RA              |                   | X          | X          | X          |
| SIB2   | ③ NPUSCH (ACK/NACK for MSG4) |                   | X          | X          | X          |
| SIB2   | ④ NPRACH (Preamble)          |                   | X          | X          | X          |
| Setup  | ⑤ NPDCCH (DCI Format N0, N1) |                   | X          | X          | X          |
| Setup  | ⑥ NPUSCH (ACK/NACK)          |                   | X          | X          | X          |
|        | ⑦ NPDSCH                     |                   | X          | X          | X          |
| SIB2   | ⑧ NPUSCH (Format 1)          |                   | X          | X          | X          |
|        | ⑨ NPDSCH for Paging          |                   | X          | X          | X          |

---

#### NPDSCH Scheduling Rules

1. NPDSCH is always scheduled 4ms after received NPDCCH (DCI).
2. NPUSCH ACK/NACK for NPDSCH is sent 12ms after all NPDSCH received.
3. Next NPDCCH (DCI) for next transmission is 3ms after NPUSCH ACK/NACK.

<br>
<img src="\lte_nbiot\img\lte_nbiot_npdschsch.png" width=100% height=100% />
<br>

<br>
<img src="\lte_nbiot\img\lte_nbiot_npdschsch2.png" width=100% height=100% />
<br>

---

#### NPUSCH Scheduling Rules

1. NPUSCH is always scheduled 8ms after received NPDCCH (DCI).
2. ACK/NACK for NPUSCH is sent inside NPDCCH because NB-IoT does not have PHICH like LTE.
3. Next NPDCCH (DCI) for next transmission is 3ms after NPUSCH. Same NPDCCH is used for ACK/NACK for NPUSCH.

<br>
<img src="\lte_nbiot\img\lte_nbiot_npuschsch.png" width=100% height=100% />
<br>

---

#### Anchor and Non Anchor Carrier

1. NB-IoT have a features to support more than 1 PRB. It is called Multi Carrier Mode for NB-IoT.
2. The main PRB is called <mark>Anchor</mark>, the additional PRB is called <mark>Non Anchor</mark>. 

?> Anchor: Initial Connection Setup + Data transfer (NRS, NPSS, NSS, NPBCH, NPDSCH, NPDCCH) 

?> Non Anchor: Data Transfer (NRS, NPDCCH, NPDSCH) 

When NB-IoT is operating in <mark>'inband' mode</mark>, only a specific PRB within the legacy LTE System Band can be configured as Anchor carrier. The PRB index within LTE System BW are as follows. [3]

| LTE System BW  | LTE PRB indices for NB-IoT synchronization                           |
|----------------|----------------------------------------------------------------------|
| 3 Mhz          | 2, 12                                                                |
| 5 Mhz          | 2, 7, 17, 22                                                         |
| 10 Mhz         | 4, 9, 14, 19, 30, 35, 40, 45                                         |
| 15 Mhz         | 2, 7, 12, 17, 22, 27, 32, 42, 47, 52, 57, 62, 67, 72                 |
| 20 Mhz         | 4, 9, 14, 19, 24, 29, 34, 39, 44, 55, 60, 65, 70, 75, 80, 85, 90, 95 |


***Anchor & Non Anchor Deployment Scenario Combinations*** based on [4]

<br>
<img src="\lte_nbiot\img\lte_nbiot_nonanchdep.png" width=100% height=100% />
<br>


***Benefit of having Non Anchor Carrier***

<mark>Capacity increase when:</mark>

1. Number of Non Anchor Carriers Increase – Non Anchor being used for NRS + Control Channel + Data Transfer Only.
2. Number of Multicarrier UE – If more UE support multi carrier, more UE can be assigned to Non Anchor Carrier. If proportion of non multi carrier UE in the network, most of them will be assigned to Anchor carrier and non-anchor carrier not being used.
3. NRS Power difference between Anchor and Non Anchor <mark>(nrs-PowerOffsetNonAnchor)</mark> – More power for NPDSCH in Non Anchor will increase more capacity.

***UE Operation***

>UE go to Non Anchor Carrier when ENodeB instruct UE to do so in RRC Connection Setup/Reconfiguration/Resume/Reestablishment (MSG4). 

>ENodeB decides which UE go to Non Anchor carrier (Based on Vendor Algorithm – for example Load Estimation). 

>UE will be release when UE go to Idle Mode by sending RRC Connection Release. 

>In Idle Mode UE only listen to MIB/SIB from Anchor Carrier. 

***Procedure: Assignmnet to Non Anchor***

<br>
<img src="\lte_nbiot\img\lte_nbiot_nonanchsig.png" width=100% height=100% />
<br>

| Procedure    | Channel/Signal  | Direction  | Information                                           |
|--------------|-----------------|------------|-------------------------------------------------------|
| Cell Search  | NPSS/NSSS       | eNB -> UE  | UE know Anchor DL EARFCN                              |
| MIB          | NPBCH           | eNB -> UE  | UE know SIB1 Scheduling/NB-IoT Operation Mode         |
| SIB1         | NPDSCH          | eNB -> UE  | UE know Cell Selection Parameter                      |
| SIB2         | NPDSCH          | eNB -> UE  | UE know Initial Access Parameter, Anchor UL EARFCN    |
| SIB3/5       | NPDSCH          | eNB -> UE  | UE know intra freq, inter freq reselection parameter  |
| MSG1         | NPRACH          | UE -> eNB  | UE send preamble to eNB                               |
| MSG2         | NPDCCH, NPDSCH  | eNB -> UE  | UE receive RAR and UL Grant for MSG 3                 |
| MSG3         | NPUSCH          | UE -> eNB  | UE tell eNB for Multi-Carrier Operation Support       |
| MSG4         | NPDCCH, NPDSCH  | eNB -> UE  | UE know eNB assign UE to Anchor/Non Anchor Carrier    |
| MSG5         | NPUSCH          | UE -> eNB  | UE acknowledge eNB to operate in Anchor/NonAnchor     |

<br>
<img src="\lte_nbiot\img\lte_nbiot_nonanchsig2.png" width=100% height=100% />
<br>

<br>
<img src="\lte_nbiot\img\lte_nbiot_nonanchsig3.png" width=70% height=70% />
<br>

<mark>Scheduling Example</mark> based on [5]

1. UE1 is configured with the anchor carrier.  
2. UE2 with other carrier in DL and UL 
3. UE3 with a different carrier only on DL.  
4. For simplicity, this diagram neither considers the NPDCCH period. 

<br>
<img src="\lte_nbiot\img\lte_nbiot_nonanchsch.png" width=100% height=100% />
<br>

!> Restrictions: UE cannot use both Anchor and Non Anchor carrier simultaneously like CA. That is why it is important for UE to only have 1 Tx/Rx element operating only within 180kHz BW.

---

#### References

1. 3GPP TS 36.104 Section 6.3.3
2. 3GPP TS 36.213 Section 7.1.6
3. [Sharetechnote](http://www.sharetechnote.com/html/Handbook_LTE_NB_MultiCarrier.html)
4. 3GPP TS 36.300 Section 5.5a
5. [Rohde & Schwarz](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma266/1MA266_0e_NB_IoT.pdf)


