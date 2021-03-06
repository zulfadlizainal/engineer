Topic: 4G LTE<br>
Sub-Topic: NB-IoT<br>
Date Written: 2019/05/18<br>
Date Edited: 2022/03/23<br>

---

#### MIB-NB Repetitions

1. NPBCH carries the Narrowband Master Information Block (MIB-NB). MIB-NB is being transmitted over 64 radio frame with 8 repetitions pattern.
2. A preserved field in the MIB is used to indicate the SIB1-NB scheduling information.

Key Concepts: [1]

    The MIB scheduling period is always 640ms.
    MIB repetitions made within 640 ms.
    The first transmission of the MIB is scheduled in subframe #0 of radio frames for which the SFN mod 64 = 0.
    MIB repetitions are scheduled in subframe #0 of all other radio frames.
    The transmissions are arranged in 8 independently decodable blocks of 80ms duration.

<mark>Content of MIB-NB:</mark> Have Scheduling for SIB1-NB [2]

<br>
<img src="\lte_nbiot\img\lte_nbiot_mibnb.png" width=100% height=100% />
<br>


<mark>MIB Repetitions:</mark> [3]

<br>
<img src="\lte_nbiot\img\lte_nbiot_mibnbrep.png" width=100% height=100% />
<br>

---

#### SIB1-NB Repetitions

1. schedulingInfoSIB1-NB is specified in MIB-NB.
2. The scheduling period of SIB1-NB is 2560ms. SIB 1-NB carry cell selection Info and scheduling for other SIBs-NB.
3. Pre defined table is being used to determine the location of frequency domain & time domain for SIB 1-NB.
4. Pre defined table will determine number of NPDSCH repetitions for SIB 1-NB, TBS Index for NPDSCH SIB 1-NB, and resource location of SIB 1-NB.

<mark>SIB 1-NB Repetitions</mark> from [2]

<br>
<img src="\lte_nbiot\img\lte_nbiot_sib1nbrep.png" width=100% height=100% />
<br>

Table for easy copy:

| schedulingInfoSIB1-NB-r13 | NPDSCH repetitions |
|---------------------------|--------------------|
| 0                         | 4                  |
| 1                         | 8                  |
| 2                         | 16                 |
| 3                         | 4                  |
| 4                         | 8                  |
| 5                         | 16                 |
| 6                         | 4                  |
| 7                         | 8                  |
| 8                         | 16                 |
| 9                         | 4                  |
| 10                        | 8                  |
| 11                        | 16                 |
| 12 to 15                  | Reserved           |

<mark>SIB 1-NB TBS</mark> from [4]

<br>
<img src="\lte_nbiot\img\lte_nbiot_sib1nbtbs.png" width=100% height=100% />
<br>

Table for easy copy:

| ITBS | TBS      |
|------|----------|
| 0    | 208      |
| 1    | 208      |
| 2    | 208      |
| 3    | 328      |
| 4    | 328      |
| 5    | 328      |
| 6    | 440      |
| 7    | 440      |
| 8    | 440      |
| 9    | 680      |
| 10   | 680      |
| 11   | 680      |
| 12   | Reserved |
| 13   | Reserved |
| 14   | Reserved |
| 15   | Reserved |

<mark>SIB 1-NB Location</mark> from [2]

The starting radio frame for the first transmission of the NPDSCH carrying SystemInformationBlockType1-NB is determined according to Table 16.4.1.3-4.

<br>
<img src="\lte_nbiot\img\lte_nbiot_sib1nbloc.png" width=100% height=100% />
<br>

Table for easy copy:

| Number of NPDSCH repetitions | PCI           | Starting radio frame number for NB-SIB1 repetitions (nf mod 256) |
|------------------------------|---------------|------------------------------------------------------------------|
| 4                            | PCI Mod 4 = 0 | 0                                                                |
| 4                            | PCI Mod 4 = 1 | 16                                                               |
| 4                            | PCI Mod 4 = 2 | 32                                                               |
| 4                            | PCI Mod 4 = 3 | 48                                                               |
| 8                            | PCI Mod 2 = 0 | 0                                                                |
| 8                            | PCI Mod 2 = 1 | 16                                                               |
| 16                           | PCI Mod 2 = 0 | 0                                                                |
| 16                           | PCI Mod 2 = 1 | 1                                                                |

---

#### CE Level Selection Criteria

The important thing is how UE consider itself to be in specific CE based on RSRP measurement. Based on 3GPP, UE shall consider to be in the designated CE Level when measured RSRP is < than Threshold in Higher Layer. It means if your index value translated into table range, when UE RSRP is less than the range, UE should consider itself to be in lower CE Level. [5] 

<br>
<img src="\lte_nbiot\img\lte_nbiot_ceselect.png" width=100% height=100% />
<br>

---

#### CE Level Conversion 

Based on 3GPP, RSRP threshold for CE level is mapped into RSRP range information element table. [6]

<br>
<img src="\lte_nbiot\img\lte_nbiot_ceconv.png" width=100% height=100% />
<br>

<br>
<img src="\lte_nbiot\img\lte_nbiot_ceconv2.png" width=100% height=100% />
<br>

!> In some cases, vendors and UE might have different understanding on how to covert this value to a CE level value. For example, in this case TEMS using lower limit in their tool while XCAP using upper limit. 3GPP only define a range of RSRP for each index, maybe to save some index space. [7]

<br>
<img src="\lte_nbiot\img\lte_nbiot_ceconv3.png" width=100% height=100% />
<br>

?> Easy Tips: If SIB 2 Threshold says 15, Change CE Level when RSRP < -126dBm 

| CE Level Change Value?? | SIB 2 IE?? |
|------------------------|-----------|
| -126?? <= X < -125????    | (15)      |

---

#### RACH MSG3 Multi Tone Decision

When UE Sending NPRACH, <mark>the subcarrier index used by the UE to send NPRACH will indicates whether UE support MSG multitone or not.</mark> This is decided by <mark>'nprach-subcarrierMSG3-RangeStart-r13'</mark> parameter provided by SIB2.

***How This Parameter Works?***

1. eNB will send a range of preamble that can be used by the UE to send NPRACH.
2. nprach-NumCBRA-StartSubcarriers (SIB2) - This parameter will tell UE the range.
3. After UE know this range UE will read another parameter in SIB2 to know whether this range is being partition or not.
4. nprach-SubcarrierMSG3-RangeStart (SIB2) - This parameter will tell UE whether the range is being partitioned or not.
5. So, <mark>if UE support multitone in MSG3, UE will send NPRACH using multitone partition.</mark> If UE not support multitone in MSG3, UE will send NPRACH using single tone partition.
6. This partition does not mean anything for NPRACH. It is just an indication to eNB that UE support Multitone in MSG3 transmission.

<br>
<img src="\lte_nbiot\img\lte_nbiot_npuschmsg3.png" width=100% height=100% />
<br>

<br>
<img src="\lte_nbiot\img\lte_nbiot_npuschmsg32.png" width=100% height=100% />
<br>

<br>
<img src="\lte_nbiot\img\lte_nbiot_npuschmsg33.png" width=100% height=100% />
<br>

<mark>3GPP Snapshot:</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_npuschmsg34.png" width=100% height=100% />
<br>

<br>
<img src="\lte_nbiot\img\lte_nbiot_npuschmsg35.png" width=100% height=100% />
<br>

---

#### Paging

<mark>Paging</mark> - A process where network is telling the UE that there is something for the UE. [8]

1. UE will decode the paging message (paging cause).
2. UE will then initiate the appropriate procedure.
3. Most cases paging process happen in Idle Mode.
4. UE have to wake up and monitor whether there is a paging being scheduled.
5. Always monitor this paging is a waste of energy.  

<mark>To solve this:</mark>

6. In Network side -> Network will not send paging continuously. However, only transmit paging in burst mode using certain interval.
7. In UE Side -> UE will go sleep when network not transmitting Paging and UE will just wake up exactly at the time you are transmitting the paging message. <mark>This method is called Discontinues Reception (DRX) -  where UE receive info from network discontinuously.</mark>
8. Paging messages are sent by a MME to all eNodeBs in a Tracking Area and those eNodeBs in a Tracking Area is transmitting the same paging message.
9. Each eNodeB can contain cells belonging to different tracking areas but each cell can only belong to one Tracking Area.

***Types of Paging***

1. Core Initiated paging (Incoming call, SMS, Incoming data).
2. eNB initiated paging (Change of SI, Emergency notifications, Earthquake or Tsunami Warning).

<br>
<img src="\lte_nbiot\img\lte_nbiot_pagingtype.png" width=100% height=100% />
<br>

***Paging Mechanism***

1. During the idle mode, UE gets into and stay in sleeping mode defined in DRX cycle (Discontinuous Receive Cycle). (This DRX is cycle is defined in SIB2).
2. UE periodically wake up and monitor PDCCH in order to check for the presence of a paging message (UE looks for???any information encrypted by P-RNTI).
3. If the PDCCH indicates that a paging message is transmitted in the subframe, then UE needs to demodulate the PCH to see if the paging message is directed to it.

<br>
<img src="\lte_nbiot\img\lte_nbiot_pagingsignaling.png" width=100% height=100% />
<br>

?> Note: UE dont know whether the paging message (PDSCH) contain his TMSI or not. He just decode the paging message (PDSCH) if he observed any PDCCH with P-RNTI.

<mark>Sample paging parameter in SIB2:</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_pagingparam.png" width=70% height=70% />
<br>

***Paging Occasion & Paging Frame***

Refer [9]

<mark>Paging Occasion (PO)</mark> is a subframe where there may be P-RNTI transmitted on PDCCH addressing the paging message.

<mark>Paging Frame (PF)</mark> is one Radio Frame which may contain one or multiple Paging Occasion(s).

***Paging Frame Formula:***

Paging frame is derived from below formula: [9]

    PF = SFN mod T = (T div N) x (UE_ID mod N) 

<mark>T Derivation:</mark>

T = DRX Cycle of the UE  

T can be received by 3 different source: (2 if NB-IoT)

1. SIB2: IE defaultPagingCycle-r13.
2. Upper Layer: Use this value if provided (Through Attach Request or TAU).
3. UE specify own DRX value - Not supported in NB-IoT.

<mark>N and nB Derivation:</mark>

    N = min (T, nB) -->> Which means the smaller one among T and nB. 
    nB = paging frame, can be received from SIB2 IE nB-r13.

    Where:
    nB value can be -> 4T, 2T, T, T/2, T/4, T/8, T/16, T/32, T/64, T/128, and T/256, and for NB-IoT also T/512, and T/1024.  

N based on T and nB:

| nB?? | 4T?? | 2T?? | T?? | 1/2 T?? | 1/4 T?? | 1/8 T?? | 1/16 T?? | 1/32 T?? |
|-----|-----|-----|----|--------|--------|--------|---------|---------|
| N??  | 1??  | 1??  | 1?? | 1/2??   | 1/4??   | 1/8??   | 1/16??   | 1/32    |


<mark>UE ID Derivation:</mark>

UE_ID = IMSI mod XXX, where IMSI should be used in Decimal format and is stored in USIM. 

> IMSI mod 1024, if P-RNTI is monitored on PDCCH.  

> IMSI mod 4096, if P-RNTI is monitored on NPDCCH.  

> IMSI mod 16384, if P-RNTI is monitored on MPDCCH or if P-RNTI is monitored on NPDCCH and the UE supports paging on a non-anchor carrier, and if paging configuration for non-anchor carrier is provided in system information.  

***Paging Occasion Formula:***

    PO = Based on Tables

    Where:
    Ns = Number of paging occasions. 
    Ns = max(1, nB/T), which means that Ns is the larger value between 1 and NB/T. 

Ns based on T and nB:

| nB?? | 4T?? | 2T?? | T?? | 1/2 T?? | 1/4 T?? | 1/8 T?? | 1/16 T?? | 1/32 T?? |
|-----|-----|-----|----|--------|--------|--------|---------|---------|
| Ns?? | 4??  | 2??  | 1?? | 1??     | 1??     | 1??     | 1??      | 1       |


<mark>Scenario:</mark>

1. When Ns = 1, there can be only one paging occation (only one subframe where paging message is carried) within a Paging Frame and the subframe number is 9.
2. When Ns = 2, there can be two???paging occations (two subframes where paging message is carried) within a Paging Frame and the subframe number is 4 and 9.
3. When Ns = 4, there can be four???paging occations (four subframes where paging message is carried) within a Paging Frame and the subframe number is 0,4,5 and 9.

<mark>3GPP Table for PO subframe number:</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_pagingsubframe.png" width=100% height=100% />
<br>

---

#### References

1. 3GPP TS 36.331 Section 5.2.1.2
2. 3GPP TS 36.213 Section 16.4.1.3
3. [Rohde & Schwarz](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma266/1MA266_0e_NB_IoT.pdf)
4. 3GPP TS 36.213 Section 16.4.1.5.2
5. 3GPP TS 36.321 Section 5.1.1
6. 3GPP TS 36.331
7. 3GPP TS 36.133 Section 9.1.4
8. [Sharetechnote](https://www.sharetechnote.com/html/Paging_LTE.html)
9. 3GPP TS 36.304