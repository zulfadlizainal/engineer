Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/06/02<br>
Date Edited: 2022/06/13<br>

---

#### SCS for SSB

Refer [1]

<mark>Single SSB SCS</mark> is defined for most of frequency band to reduce UE blind search.

!> Few bands use 2 SCS due to having coexistence with LTE. LTE use 15kHz SCS. Eg: Band n5

Table from [2]

***<mark>Sub 6 (FR1):</mark>***

| Band | SSB SCS (Freq) | SSB Pattern (Time) | GSCN (First – Step Size – Last) |
|------|----------------|--------------------|---------------------------------|
| n1   | 15 kHz         | Case A             | 5279 – <1> – 5419               |
| n2   | 15 kHz         | Case A             | 4829 – <1> – 4969               |
| n3   | 15 kHz         | Case A             | 4517 – <1> – 4693               |
| n5   | 15 kHz         | Case A             | 2177 – <1> – 2230               |
| n5   | 30 kHz         | Case B             | 2183 – <1> – 2224               |
| n7   | 15 kHz         | Case A             | 6554 – <1> – 6718               |
| n8   | 15 kHz         | Case A             | 2318 – <1> – 2395               |
| n12  | 15 kHz         | Case A             | 1828 – <1> – 1858               |
| n20  | 15 kHz         | Case A             | 1982 – <1> – 2047               |
| n25  | 15 kHz         | Case A             | 4829 – <1> – 4981               |
| n28  | 15 kHz         | Case A             | 1901 – <1> – 2002               |
| n34  | 15 kHz         | Case A             | 5030 – <1> – 5056               |
| n38  | 15 kHz         | Case A             | 6431 – <1> – 6544               |
| n39  | 15 kHz         | Case A             | 4706 – <1> – 4795               |
| n40  | 15 kHz         | Case A             | 5756 – <1> – 5995               |
| n41  | 15 kHz         | Case A             | 6246 – <3> – 6717               |
| n41  | 30 kHz         | Case C             | 6252 – <3> – 6714               |
| n50  | 15 kHz         | Case A             | 3584 – <1> – 3787               |
| n51  | 15 kHz         | Case A             | 3572 – <1> – 3574               |
| n65  | 15 kHz         | Case A             | 5279 – <1> – 5494               |
| n66  | 15 kHz         | Case A             | 5279 – <1> – 5494               |
| n66  | 30 kHz         | Case B             | 5285 – <1> – 5488               |
| n70  | 15 kHz         | Case A             | 4993 – <1> – 5044               |
| n71  | 15 kHz         | Case A             | 1547 – <1> – 1624               |
| n74  | 15 kHz         | Case A             | 3692 – <1> – 3790               |
| n75  | 15 kHz         | Case A             | 3584 – <1> – 3787               |
| n76  | 15 kHz         | Case A             | 3572 – <1> – 3574               |
| n77  | 30 kHz         | Case C             | 7711 – <1> – 8329               |
| n78  | 30 kHz         | Case C             | 7711 – <1> – 8051               |
| n79  | 30 kHz         | Case C             | 8480 – <16> – 8880              |


***<mark>mmWave (FR2):</mark>***

| Band  | SSB SCS (Freq) | SSB Pattern (Time) | GSCN (First – Step Size – Last) |
|-------|----------------|--------------------|---------------------------------|
| n257  | 120 kHz        | Case D             | 22388 – <1> – 22558             |
| n257  | 240 kHz        | Case E             | 22390 – <2> – 22556             |
| n258  | 120 kHz        | Case D             | 22257 – <1> – 22443             |
| n258  | 240 kHz        | Case E             | 22258 – <2> – 22442             |
| n260  | 120 kHz        | Case D             | 22995 – <1> – 23166             |
| n260  | 240 kHz        | Case E             | 22996 – <2> – 23164             |
| n261  | 120 kHz        | Case D             | 22446 – <1> – 22492             |
| n261  | 240 kHz        | Case E             | 22446 – <2> – 22490             |

> Note: SSB Pattern (Time) should be explained in SSB Position Section (If I make it LOL)

---

#### SSB

1. PSS, SSS, and PBCH is encapsulated in 4 consecutive symbols.
2. SCS is same within SSB.

Picture from [3]

<br>
<img src="\nr_embb\img\nr_embb_ssb.png" width=100% height=100% />
<br>

?> Why there is No Tx subcarriers besides PSS and SSS? Answer: To ease sync sgnal detection.

---

#### References

1. [Qualcomm](https://www.qualcommwirelessacademy.com/)
2. 3GPP TS 38.104
3. [Anritsu](https://dl.cdn-anritsu.com/ja-jp/test-measurement/reffiles/About-Anritsu/R_D/Technical/95/95-01.pdf)