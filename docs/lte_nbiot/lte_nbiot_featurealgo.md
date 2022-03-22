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

<mark>Note:</mark> All RE in NB-IoT PRB is 6dB boost from common LTE. This include NRS and also Non-NRS RE.

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

---

#### References

1. 3GPP TS 36.104 Section 6.3.3
2. 3GPP TS 36.213 Section 7.1.6

