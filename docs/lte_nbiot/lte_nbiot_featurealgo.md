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

| System BW  | RBS Size  |
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

---

#### References

1. 3GPP TS 36.104 Section 6.3.3
2. 3GPP TS 36.213 Section 7.1.6


