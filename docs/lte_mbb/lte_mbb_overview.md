Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2019/06/14<br>
Date Edited: 2022/02/08<br>

---

#### UE Category

Category information is used to allow the eNB to communicate effectively with all the UEs connected to it.  The ue-Category defines a combined uplink and downlink capability as specified in 3GPP. [1] [2]

>DL-SCH = Downlink shared channel<br>
>UL-SCH = Uplink shared channel<br>
>TTI = Transmission Time Interval<br>

***Downlink physical layer parameter values set by the field ue-Category:*** [1]

<br>
<img src="\lte_mbb\img\lte_mbb_dluecat.png" width=100% height=100% />
<br>

***Uplink physical layer parameter values set by the field ue-Category:*** [2]

<br>
<img src="\lte_mbb\img\lte_mbb_uluecat.png" width=100% height=100% />
<br>

---

#### Operating Bands

LTE Operating Bands [3] [4]

<br>
<img src="\lte_mbb\img\lte_mbb_operband.png" width=100% height=100% />
<br>

and continued in a long table list in 3GPP.

---

#### Supported Bandwidths

The bandwidths defined by the standard are <mark>1.4, 3, 5, 10, 15, and 20 MHz</mark>. The table below shows how many subcarriers and resource blocks there are in each bandwidth for uplink and downlink. 

| Bandwidth  | Resource Blocks  | Subcarriers (downlink)  | Subcarriers (uplink)  |
|------------|------------------|-------------------------|-----------------------|
| 1.4 MHz    | 6                | 73                      | 72                    |
| 3 MHz      | 15               | 181                     | 180                   |
| 5 MHz      | 25               | 301                     | 300                   |
| 10 MHz     | 50               | 601                     | 600                   |
| 15 MHz     | 75               | 901                     | 900                   |
| 20 MHz     | 100              | 1201                    | 1200                  |

---

#### CA Band Combinations

It's too long to list, refer specifications for full list.

?> Specs to refer: 3GPP TS 36.306

---

#### References

1. 3GPP TS 36.306 table 4.1-1
2. 3GPP TS 36.306 table 4.1-2
3. 3GPP TS 36.306 table 5.5-1
4. [Sqimway](https://www.sqimway.com/lte_band.php)