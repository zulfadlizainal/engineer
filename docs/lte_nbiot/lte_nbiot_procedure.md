Topic: 4G LTE<br>
Sub-Topic: NB-IoT<br>
Date Written: 2019/05/18<br>
Date Edited: 2022/03/22<br>

---

#### MIB-NB Repetitions

1. NPBCH carries the Narrowband Master Information Block (MIB-NB). MIB-NB is being transmitted over 64 radio frame with 8 repetitions pattern.
2. A preserved field in the MIB is used to indicate the SIB1-NB scheduling information.

Key Concepts: [1]

?> The MIB scheduling period is always 640ms.

?> MIB repetitions made within 640 ms.

?> The first transmission of the MIB is scheduled in subframe #0 of radio frames for which the SFN mod 64 = 0.

?> MIB repetitions are scheduled in subframe #0 of all other radio frames.

?> The transmissions are arranged in 8 independently decodable blocks of 80ms duration.

<mark>Content of MIB-NB:</mark> Have Scheduling for SIB1-NB [2]

<br>
<img src="\lte_nbiot\img\lte_nbiot_mibnb.png" width=100% height=100% />
<br>


<mark>MIB Repetitions:</mark> [3]

<br>
<img src="\lte_nbiot\img\lte_nbiot_mibnbrep.png" width=100% height=100% />
<br>

---

#### References

1. 3GPP TS 36.331 Section 5.2.1.2
2. 3GPP TS 36.213 Section 16.4.1.3
3. [Rohde & Schwarz](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma266/1MA266_0e_NB_IoT.pdf)

