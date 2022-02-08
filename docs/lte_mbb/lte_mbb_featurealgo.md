Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2019/08/13<br>
Date Edited: 2022/02/08<br>

---

#### MIMO Concept

MIMO stands for Multiple Input Multiple Output. Simply, it is a technique to increase the data throughput by using multiple transmitter antenna and multiple receiver antenna. [1]

***DL MIMO***

<br>
<img src="\lte_mbb\img\lte_mbb_dlmimo.png" width=100% height=100% />
<br>

Usually in industry standard, when engineer say Tx x Rx MIMO, they are referring to DL MIMO.

1. 2 x 2 means: 2 TX in eNB, 2 RX in UE 

<br>
<img src="\lte_mbb\img\lte_mbb_dlmimo2x2.png" width=100% height=100% />
<br>

2. 4 x 2 means: 4 TX in eNB, 2 RX in UE 

<br>
<img src="\lte_mbb\img\lte_mbb_dlmimo4x2.png" width=100% height=100% />
<br>

3. 4 x 4 means: 4 TX in eNB, 4 RX in UE 

<br>
<img src="\lte_mbb\img\lte_mbb_dlmimo4x4.png" width=100% height=100% />
<br>

***UL MIMO***

<br>
<img src="\lte_mbb\img\lte_mbb_ulmimo.png" width=100% height=100% />
<br>

Not many devices in LTE support UL MIMO. UL MIMO requires a lot of energy usage and demand for UL data is not as high as DL. 

1. 4 x 4 means: 4 TX in UE, 4 RX in eNB 

<br>
<img src="\lte_mbb\img\lte_mbb_ulmimo4x4.png" width=100% height=100% />
<br>

***MIMO with CA***

On higher level, CA and MIMO have same purposes. To increase throughput/capacity. Below are example representation of MIMO with combination of CA.

1. 2CC CA with 2 x 2 MIMO on both PCell and SCell

<br>
<img src="\lte_mbb\img\lte_mbb_dlmimo2ca2x2.png" width=100% height=100% />
<br>

---

#### References

1. [Sharetechnote](https://www.sharetechnote.com/html/BasicProcedure_LTE_MIMO.html)