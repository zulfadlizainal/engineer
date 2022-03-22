Topic: 4G LTE<br>
Sub-Topic: NB-IoT<br>
Date Written: 2019/05/18<br>
Date Edited: 2022/03/22<br>

---

#### MIB-NB Repetitions

1. NPBCH carries the Narrowband Master Information Block (MIB-NB). MIB-NB is being transmitted over 64 radio frame with 8 repetitions pattern.
2. A preserved field in the MIB is used to indicate the SIB1-NB scheduling information.

Key Concepts: [1]

>The MIB scheduling period is always 640ms.

>MIB repetitions made within 640 ms.

>The first transmission of the MIB is scheduled in subframe #0 of radio frames for which the SFN mod 64 = 0.

>MIB repetitions are scheduled in subframe #0 of all other radio frames.

>The transmissions are arranged in 8 independently decodable blocks of 80ms duration.

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

***SIB 1-NB Repetitions*** from [2]

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

***SIB 1-NB TBS*** from [4]

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

***SIB 1-NB Location*** from [2]

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

#### References

1. 3GPP TS 36.331 Section 5.2.1.2
2. 3GPP TS 36.213 Section 16.4.1.3
3. [Rohde & Schwarz](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma266/1MA266_0e_NB_IoT.pdf)
4. 3GPP TS 36.213 Section 16.4.1.5.2

