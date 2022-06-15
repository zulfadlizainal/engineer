Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/08/31<br>
Date Edited: 2022/06/15<br>

---

#### Initial Access: Synchronization Establishment

Synchronization is the fist step before establishing any connections between Tx & Rx.<br>
Sync happen in DL (SSB Sync) and UL (RACH Process), and this overall process is called <mark>Initial Access.</mark>

***<mark>High level Process:</mark>***

<br>
<img src="\nr_embb\img\nr_embb_initaccesssync.png" width=70% height=70% />
<br>

<br>
<img src="\nr_embb\img\nr_embb_initaccesssync2.png" width=70% height=70% />
<br>

***<mark>Types of Syncronization</mark>***

1. Sync Establishment for Initial Access.
2. Sync Maintenance for Idle & Connected.

<br>
<img src="\nr_embb\img\nr_embb_synctype.png" width=70% height=70% />
<br>

***<mark>Key Procedure:</mark>***

***1> 2-Step Synchronization Process (Similar with LTE)***

1. UE sync with PSS
2. UE sync with SSS (And acquire PCI)

***2> Time and Freq domain resources are pre-defined***

1. Different Time domain patterns for Sync Establishment (Initial Access) and Sync Maintenance (Idle & Connected)
2. SCS for SSB is dependent on frequency band

---

#### Initial Access: Synchronization Raster

Synchronization Raster = Set of allowed center frequencies for SSB.<br> 

!> Why need Sync Raster -> To allow faster cell acquisition time. Since the raster is defined wider, UE will only seacrh in possible center frequency. Fast cell search!

***<mark>Global Freq Raster Division:</mark>***

Table form [4]

| Frequency Range     | Sync Raster Frequency Position      |
|---------------------|-------------------------------------|
| 0 - 3000 MHz        | Multiple of 1.2 MHz + offset factor |
| 3000 - 24250 MHz    | Multiple of 1.44 MHz                |
| 242450 - 100000 MHz | Multiple of 17.82 MHz               |

The SSB is used by the UE during the initial cell search procedure. The <mark>center frequency</mark> of the SSB is defined as the frequency of subcarrier 0 belonging to RB 10. [5]

<br>
<img src="\nr_embb\img\nr_embb_centerfreq.png" width=100% height=100% />
<br>

?> Center Frequency of SSB = GSCN = NR ARFCN

---

#### MIB and SIB Acquisition

***<mark>MIB</mark>***

1. MIB is decoded from PBCH that is being carried by SSB.
2. Identical MIB (same & different SSB) is transmitted 4 times in 80ms -> <mark>Ease decoding using soft combining.</mark>

Picture from [4]

<br>
<img src="\nr_embb\img\nr_embb_mibperiodicity.png" width=100% height=100% />
<br>

***<mark>SIB</mark>***

LTE vs NR: 

1. In LTE: SI is always broadcasted.
2. In NR: Minimum SI can be delivered, and remaining information can be set upon request.
3. In NR: NR SI support for beam sweeping.

SIB Numbering Differences: [6] [7]

| No | Item                            | LTE          | NR      |
|----|---------------------------------|--------------|---------|
| 1  | Cell Access, Cell Selection     | SIB 1        | SIB 1   |
| 2  | RACH, PC, Timer, Access Barring | SIB 2        | SIB 1   |
| 3  | Intra Freq Reselection          | SIB 3        | SIB 2   |
| 4  | Intra Freq Ncell                | SIB 4        | SIB 3   |
| 5  | Inter Freq Ncell                | SIB 5        | SIB 4   |
| 6  | EUTRA Freq Ncell                |              | SIB 5   |
| 7  | UTRAN Freq Ncell                | SIB 6        |         |
| 8  | GERAN Freq Ncell                | SIB 7        |         |
| 9  | CDMA Freq Ncell                 | SIB 8        |         |
| 10 | Femtocell Name                  | SIB 9        |         |
| 11 | ETWS                            | SIB 10/11    | SIB 6/7 |
| 12 | CMAS                            | SIB 12       | SIB 8   |
| 13 | MBMS                            | SIB 13/15/20 |         |
| 14 | Extended Access Barring         | SIB 14       |         |
| 15 | GPS                             | SIB 16       | SIB 9   |
| 16 | WLAN                            | SIB 17       |         |
| 17 | Sidelink                        | SIB 18/19/21 |         |
| 18 | NR Ncell                        | SIB 24       |         |

***<mark>SI Acquisition SA vs NSA</mark>***

Picture from [4]

<br>
<img src="\nr_embb\img\nr_embb_siacquisitionsansa.png" width=100% height=100% />
<br>

?> NSA operation does not need RMSI and SIB to be OTA broadcast. MIB still needed to get some timing information.

---

#### RACH Procedure

***<mark>Comparison: LTE vs NR</mark>***

| No | Similarities                                   | Differences                          |
|----|------------------------------------------------|--------------------------------------|
| 1  | RACH Procedure (MSG1-4).                       |                                      |
| 2  | Preamble Based on Zadoff Chu Sequence.         |                                      |
| 3  | Two types: Contention Free & Contention Based. |                                      |
| 4  |                                                | RACH Config in SIB 1 (LTE in SIB 2). |
| 5  |                                                | Beam correspondences.                |
| 6  |                                                | Preamble formats.                    |
| 7  |                                                | New RACH reasons.                    |

***<mark>New RACH Reasons in NR</mark>***

1. Beam failure recovery.
2. SCG cell add and change failure.
3. Request for other SI.
4. Transition from RRC_INACTIVE.

***<mark>Random Access Triggers: SA vs NSA</mark>***

Refer [4]

| RACH Trigger                                       | NSA | SA  | Initiated by?   | New? |
|----------------------------------------------------|-----|-----|-----------------|------|
| NR Initial Access                                  | YES | YES | RRC             |      |
| Transition from NR RRC_INACTIVE                    | NO  | YES | RRC             | YES  |
| NR Scell Change                                    | YES | NO  | RRC             |      |
| NR Handover                                        | NO  | YES | RRC             |      |
| RRC Connection Re-establishment Following RLF      | YES | YES | RRC             |      |
| To Establish Time Alignment at Scell Addition      | YES | YES | RRC             |      |
| DL/UL Data Arrival with UE Out of UL Sync          | YES | YES | PDCCH Order/MAC |      |
| Request for Other System Information (OSI)         | NO  | YES | RRC             | YES  |
| Beam Failure Recovery                              | YES | YES | MAC             | YES  |
| Maximum Number of Scheduling Request Transmissions | YES | YES | MAC             |      |

<br>
<img src="\nr_embb\img\nr_embb_rachtrigger.png" width=100% height=100% />
<br>

***<mark>General RACH Procedure</mark>***

Procedure are similar with LTE. [5]

<br>
<img src="\nr_embb\img\nr_embb_rachprocedure.png" width=100% height=100% />
<br>

***<mark>Associating RACH with Beams</mark>***

1. RACH configuration is given in RMSI (SIB1).
2. Association between SSB and RACH preamble is given given in RMSI.
3. UE will perform RACH Msg 1 by sending preamble for specific SSB id.

Eg: SIB 1 (RMSI) SSB Relation with Preamble [8]

<br>
<img src="\nr_embb\img\nr_embb_ssbpreamblerelation.png" width=100% height=100% />
<br>

Picture from [5]

<br>
<img src="\nr_embb\img\nr_embb_ssbpreamblerelation2.png" width=100% height=100% />
<br>

Eg: RACH MSG1 (Preamble) is sent on selected SSB

<br>
<img src="\nr_embb\img\nr_embb_msg1ssbid.png" width=50% height=50% />
<br>

***<mark>PRACH MSG 1 Procedure</mark>***

!> Beam based preamble selection is not available in LTE

<br>
<img src="\nr_embb\img\nr_embb_prachprocedure2.png" width=100% height=100% />
<br>

3GPP detailed flow: [5]

<br>
<img src="\nr_embb\img\nr_embb_prachprocedure.png" width=100% height=100% />
<br>

---

#### RRC State

Refer [1] [2] [3]

Overview of RRC State difference in Mobility Management based on implementation.

<br>
<img src="\nr_embb\img\nr_embb_rrcstate.png" width=100% height=100% />
<br>

---

#### References

1. [5G NR by Sassan Ahmadi](https://www.sciencedirect.com/book/9780081022672/5g-nr)
2. 3GPP TS 38.300
3. 3GPP TS 38.804
4. [Qualcomm](https://www.qualcommwirelessacademy.com/)
5. [5G NR Bullets by Chris Johnson](https://www.amazon.co.jp/-/en/Chris-Johnson/dp/1081444592)
6. [Sharetechnote 1](https://sharetechnote.com/html/Handbook_LTE_SIB.html)
7. [Sharetechnote 2](https://www.sharetechnote.com/html/5G/5G_Mib_Sib.html)
8. 3GPP TS 38.331