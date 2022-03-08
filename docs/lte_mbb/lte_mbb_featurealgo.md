Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2019/08/13<br>
Date Edited: 2022/03/08<br>

---

#### MIMO Concept

MIMO stands for Multiple Input Multiple Output. Simply, <mark>it is a technique to increase the data throughput by using multiple transmitter antenna and multiple receiver antenna.</mark> [1]

***DL MIMO***

<br>
<img src="\lte_mbb\img\lte_mbb_dlmimo.png" width=100% height=100% />
<br>

?>Usually in industry standard, when engineer say TX x RX MIMO, they are referring to DL MIMO.

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

?>Not many devices in LTE support UL MIMO. UL MIMO requires a lot of energy usage and demand for UL data is not as high as DL. 

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

#### UL Power Control for PRACH

Simulation is built in [2].

Simplified formula from 3GPP: [4]

    P_PRACH (n1)   = min{p-max, preambleInitialReceivedTargetPower + Path Loss}
    P_PRACH (>n1)  = min{p-max, preambleInitialReceivedTargetPower + Path Loss + powerRampingStep}

Where:

    Path Loss = referenceSignalPower - RSRP
    n = preambleTransMax

Important parameters:

    referenceSignalPower                       # From SIB2 in dBm
    preambleInitialReceivedTargetPower         # From SIB2 in dBm
    powerRampingStep                           # From SIB2 in dB
    preambleTransMax                           # From SIB2 in count
    p-max                                      # From SIB1 in dBm

?>MSG3 Tx Power can be derived based on MSG1 TxPower. 

Simplified formula from 3GPP: [5]

    P_PUSCH_MSG3 = min{p-max, P_PRACH + deltaPreambleMsg3}

Important parameters:

    deltaPreambleMsg3 = 4                      # From SIB2 in dB (IE x 2)

***Example simulation result:***

<br>
<img src="\lte_mbb\img\lte_mbb_prachmsg3pc.png" width=100% height=100% />
<br>

Note for MSG3 Tx Power:

!>n1 = Success MSG2 in n1, start MSG3<br>
n2 = Fail MSG2 in n1, success MSG2 in n2, start MSG3<br>
…<br>
…<br>
n10 = Fail MSG2 in n1 to n9, success MSG2 in n10, start MSG3

----

#### UL Power Control for PUSCH

Simulation is built in [3].

Simplified formula from 3GPP: [5]

<br>
<img src="\lte_mbb\img\lte_mbb_puschpcformula.png" width=100% height=100% />
<br>

    P_PUSCH: PUSXH TX Power
    P_CMAX: Maximum UE Allowable TX Power
    M_PUSCH: Number of scheduled PRB
    P0_PUSCH: Target UL Rx Power (Minimum UL Rx Power eNB can recognize the UL signal)
    alpha (α): Fraction of path loss

?>In 3GPP, only P0-Based PUSCH Power Control algorithm is being specified. To further enhance close loop power control based on UL SINR, UL SINR-Based PUSCH Power Control is usually introduced by eNB vendors.

<mark>To calculate UL SINR:</mark>

1. UL Rx Power = UL Tx Power - UL Path Loss
2. UL SINR = UL Rx Power / UL RSSI 

?>UL SINR-Based PUSCH Power Control will define the target SINR to be met. Different with p0-based where target received power is set as target.

***Example simulation result: p0 based and UL SINR based***

<br>
<img src="\lte_mbb\img\lte_mbb_puschpcsim.png" width=100% height=100% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_puschpcsim2.png" width=100% height=100% />
<br>

---

#### References

1. [Sharetechnote](https://www.sharetechnote.com/html/BasicProcedure_LTE_MIMO.html)
2. [Github](https://github.com/zulfadlizainal/4G-LTE-UL-Power-Control/tree/master/PRACH%20Power%20Control) 
3. [Github](https://github.com/zulfadlizainal/4G-LTE-UL-Power-Control/tree/master/PUSCH%20Power%20Control)
4. 3GPP TS 36.321
5. 3GPP TS 36.213
