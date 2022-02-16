Topic: 4G LTE<br>
Sub-Topic: eMTC<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/02/16<br>

---

#### Optimize Accessibility Performance

To verify IoT UE attach limitation to understand Attach performance and Out of Coverage (OOC) recovery performance. 

Requirements: 

1. To consider fluctuating fading conditions for static UE.
2. To check bottleneck of OOC recovery limitation. 

<br>
<img src="\lte_emtc\img\lte_emtc_access.png" width=100% height=100% />
<br>

<br>
<img src="\lte_emtc\img\lte_emtc_access2.png" width=100% height=100% />
<br>

<br>
<img src="\lte_emtc\img\lte_emtc_access3.png" width=100% height=100% />
<br>

---

#### Optimize Throughput Performance

***Actual Throughput Performance***

To determine single UE throughput performance, static test is more suitable for IoT device since most IoT device is static or low mobility UE. 

<br>
<img src="\lte_emtc\img\lte_emtc_tput.png" width=100% height=100% />
<br>

<br>
<img src="\lte_emtc\img\lte_emtc_tput2.png" width=100% height=100% />
<br>


***Specific CE Throughput Performance***

To determine specific CE Level throughput performance, mobility throughput test can be done. Verification can be done when UE that perform RACH in specific CE is moved to another CE. This kind of performance verification allow to check the cross points and distinguish better optimized CE Level threshold.

- <mark>If CE level switching in connected mode is not supported, start RACH in specific CE and perform test.</mark>

- <mark>If CE level switching in connected mode is supported, try to remove other CE level from system and test each CE level performance.</mark>

Purpose of this test is to get crosspoints, so we can decide where is the best CE level threshold.

?> This method of testing can also be done for other type of performances like accessibility.

<br>
<img src="\lte_emtc\img\lte_emtc_tput3.png" width=100% height=100% />
<br>

<br>
<img src="\lte_emtc\img\lte_emtc_tput4.png" width=100% height=100% />
<br>

Example: CE level change affect the movement of throughput because each CE have different PHY channel repetition set.

<br>
<img src="\lte_emtc\img\lte_emtc_tput5.png" width=100% height=100% />
<br>

---

#### Optimize Repetition Number & CE Level Threshold

1. Changing repetition number & CEL threshold should be weighted between accessibility performance and throughput performance.
2. Understanding bottleneck and crosspoints is necessary for every CEL threshold & repetition number design. Shown above.

?> High repetition number come with a cost of higher resource utilization.

!> Confirm which channel is bottleneck before changing any repetition number

Recap: <mark>PHY channel repetition parameter that can be changed, there are more in vendor perspective.</mark>

| L3 Msg | Phy Channel Repetition        | L3 Parameter Name                                                                 | CE Level 0 | CE Level 1 | CE Level 2 |
|--------|-------------------------------|-----------------------------------------------------------------------------------|------------|------------|------------|
| SIB2   | ① MPDCCH for Paging           | mpdcch-NumRepetition-Paging-r13                                                   | X          | X          | X          |
| SIB2   | ② MPDCCH for RA               | mpdcch-NumRepetition-RA-r13                                                       | X          | X          | X          |
| SIB2   | ③ PUCCH (ACK/NACK for MSG4)   | pucch-NumRepetitionCE-Msg4-Level0-r13 <br/>pucch-NumRepetitionCE-Msg4-Level1-r13  | X          | X          | X          |
| SIB2   | ④ PRACH (Preamble)            | numRepetitionPerPreambleAttempt-r13                                               | X          | X          | X          |
| Setup  | ⑤ MPDCCH (DCI Format)         | mpdcch-NumRepetition-r13                                                          | X          | X          | X          |
| Setup  | ⑥ PUCCH (ACK/NACK,Format1/2)  | pucch-NumRepetitionCE-format1-r13 <br/>pucch-NumRepetitionCE-format2-r13          | X          | X          | X          |
| SIB2   | ⑦ PDSCH                       | pdsch-maxNumRepetitionCEmodeA-r13                                                 | X          | X          | X          |
| SIB2   | ⑧ PUSCH                       | pusch-maxNumRepetitionCEmodeA-r13                                                 | X          | X          | X          |
|        | ⑨ PDSCH for Paging            |                                                                                   | X          | X          | X          |

Example of repetition parameter change method based on try and error:

<br>
<img src="\lte_emtc\img\lte_emtc_repchange.png" width=100% height=100% />
<br>

---

#### Calculate PUSCH Repetitions & Retransmission

Refer [1] [2]

1. In eMTC UL, eNB does not send HARQ ACK/NACK for PUSCH. 
2. Why? Because there is no PHICH in eMTC. 

***If no PUSCH ACK/NACK, how can eNB handle reception fail?***

1. Simply, UE will send PUSCH in all allocated repetition subframe until the end even eNB success to decode.
2. eNB will judge whether to adjust PUSCH repetition on the next allocation. (If vendor support dynamic allocations).
3. If all fail, eNB will schedule retransmit (Using same NDI). 

***Key point:***

1. No ACK/NACK transmission for PUSCH in eMTC.
2. Retransmission of PUSCH is supported in PUSCH eMTC. 

Picture from [1]

<br>
<img src="\lte_emtc\img\lte_emtc_ulharq.png" width=100% height=100% />
<br>

<mark>Logfile analysis</mark> [3]

***Repetition (Direct IE)***

If only consider repetition allocation (Not TTI Based): Direct IE is sufficient 
Because: Only eNB can know whether it is decoded or not. 

<br>
<img src="\lte_emtc\img\lte_emtc_puschrepret.png" width=50% height=50% />
<br>

***Retransmission (Direct IE)***

If need to consider number of retransmission, we can count the average number of retransmission needed in each RF and Map with average repetition (Non TTI Based).

?>This will give some idea whether the allocated repetition is enough or not -> If not enough, retransmission needed. 

<br>
<img src="\lte_emtc\img\lte_emtc_puschrepret2.png" width=50% height=50% />
<br>

***Retransmission (TTI Based)***

<mark>Based on PDCCH - DCI</mark>

<br>
<img src="\lte_emtc\img\lte_emtc_puschrepret3.png" width=50% height=50% />
<br>

<mark>Based on PUSCH - Tx Report (Best Method)</mark>

<br>
<img src="\lte_emtc\img\lte_emtc_puschrepret4.png" width=50% height=50% />
<br>

Example 1: Notice how repetition is calculated.

<br>
<img src="\lte_emtc\img\lte_emtc_puschrepret5.png" width=100% height=100% />
<br>

Example 2: Notice how Retransmission is calculated.

<br>
<img src="\lte_emtc\img\lte_emtc_puschrepret6.png" width=100% height=100% />
<br>

Example 3: Retransmission Idx Definition.

<br>
<img src="\lte_emtc\img\lte_emtc_puschrepret7.png" width=100% height=100% />
<br>

---

#### Check eDRX Settings 

***PTW Settings Index:*** [4]

<mark>For M1</mark>

<br>
<img src="\lte_emtc\img\lte_emtc_ptwm1.png" width=70% height=70% />
<br>

<mark>For NB1</mark>

<br>
<img src="\lte_emtc\img\lte_emtc_ptwnb1.png" width=70% height=70% />
<br>

***eDRX Cycle:*** [4]

<br>
<img src="\lte_emtc\img\lte_emtc_edrxcycle.png" width=70% height=70% />
<br>

***Check eDRX settings from <mark>'Attach Request'</mark> message:***

<br>
<img src="\lte_emtc\img\lte_emtc_attach.png" width=70% height=70% />
<br>

<mark>eDRX Turn On:</mark>

<br>
<img src="\lte_emtc\img\lte_emtc_edrxturnon.png" width=100% height=100% />
<br>

<mark>eDRX Turn Off:</mark>

<br>
<img src="\lte_emtc\img\lte_emtc_edrxturnoff.png" width=100% height=100% />
<br>

***UE Wake Up in each eDRX Cycles***

<br>
<img src="\lte_emtc\img\lte_emtc_edrxcycle2.png" width=100% height=100% />
<br>


---

#### References

1. 3GPP TS 36.321 Section 5.4.2.1, 5.4.2.2, 7.7 
2. [Sharetechnote](https://www.sharetechnote.com/html/Handbook_LTE_BL_CE_HARQ.html)
3. XCAP
4. 3GPP TS 24.008