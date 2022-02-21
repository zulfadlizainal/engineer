Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2019/03/03<br>
Date Edited: 2022/02/16<br>

---

#### MIB 

MIB contains below information. From this, UE know how to operate for next step <mark>(PHICH -> PDCCH for SIB -> SIB -> RACH -> Connected Mode)</mark>.

1. DL Bandwidth
2. Number of Transmit Antenna
3. System Frame Number (SFN)
4. PHICH Configuration

***Frequency x Time Domain:***

    Frequency: LTE always use 6 PRB for MIB in the middle of the bandwidth (center frequency).
    Time: Transmit every 40 ms , repeat every 10 ms

Picture form [1]

<br>
<img src="\lte_mbb\img\lte_mbb_mib.png" width=100% height=100% />
<br>

---

#### SIB

SIB information table for LTE:

| SIB    | Content                                                       |
|--------|---------------------------------------------------------------|
| SIB 1  |  Cell Selection, Cell Access, SI Scheduling                   |
| SIB 2  |  RACH, Access Barring, UL frequency Information, MBSFN Config |
| SIB 3  |  Intra Frequency Cell Reselection                             |
| SIB 4  |  Intra Frequency Neighbour Cell                               |
| SIB 5  |  Inter Frequency Neighbour Cell                               |
| SIB 6  |  UTRAN Neighbour Cell                                         |
| SIB 7  |  GERAN Neighbour Cell                                         |
| SIB 8  |  CDMA Neighbour Cell                                          |
| SIB 9  |  Home eNB Name for femtocell application                      |
| SIB 10 |  ETWS                                                         |
| SIB 11 |  ETWS                                                         |
| SIB 12 |  CMAS                                                         |
| SIB 13 |  MBMS                                                         |
| SIB 14 |  Extended Access Barring                                      |
| SIB 15 |  MBMS                                                         |
| SIB 16 |  GPS                                                          |
| SIB 17 |  WLAN                                                         |
| SIB 18 |  Sidelink                                                     |
| SIB 19 |  Sidelink                                                     |
| SIB 20 |  MBMS                                                         |
| SIB 21 |  Sidelink                                                     |
| SIB 24 |  NR Neighbour Cell                                            |

---

#### References

1. [Sharetechnote](https://www.sharetechnote.com/html/Handbook_LTE_MIB.html)
