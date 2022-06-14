Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/06/02<br>
Date Edited: 2022/06/14<br>

---

#### SCS for SSB

Refer [1]

<mark>Single SSB SCS</mark> is defined for most of frequency band to reduce UE blind search.

!> Few bands use 2 SCS due to having coexistence with LTE. LTE use 15kHz SCS. Eg: Band n5

Table from [2]

***<mark>Sub 6 (FR1): 15kHz or 30kHz</mark>***

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


***<mark>mmWave (FR2): 120kHz or 240kHz</mark>***

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

?> Why there is No Tx subcarriers besides PSS and SSS? Answer: To ease sync signal detection.

---

#### SSB Frequency Domain Resource

1. N(ssb,crb) = SIB1_offsetToPointA = RB offset between CRB0 and the CRB that overlap with the start of SSB.
2. k(ssb) = MIB_ssb-SubcarrierOffset = subcarrier offset from subcarrier 0 of the CRB identified by offsetToPointA to subcarrier 0 of SSB.

Picture from [4]

<br>
<img src="\nr_embb\img\nr_embb_ssbfreq.png" width=100% height=100% />
<br>

!> SSB need to be defined in sycronization raster for UE to be able to do cell search and find the SSB. In case of NSA ENDC, UE will find the SSB through embedded 5G MIB and SIB1 since cell search procedure not required.

---

#### SSB Time Domain Resource

Multiple SSB can be scheduled in a cell - typically used for beamsweeping.

?> Simple logic: Higher frequency -> Narrower beam -> More steps of beam sweeping -> more SSB needed.

***<mark>Number of Max SSB in one SS Burst Set:</mark>***

<br>
<img src="\nr_embb\img\nr_embb_maxssb.png" width=60% height=60% />
<br>


| Carrier          | SCS      | Max No of SSB (L) |
|------------------|----------|-------------------|
| f <= 3GHz        | 15, 30   | 4                 |
| 3GHz < f <= 6GHz | 15, 30   | 8                 |
| f > 6GHz         | 120, 240 | 64                |


***<mark>Good summary on start symbol candidate for SSB: </mark>*** 

Refer [4]

<br>
<img src="\nr_embb\img\nr_embb_ssb startsymbol.png" width=100% height=100% />
<br>

---

#### SSB Burst Set and Periodicity

1. SS Burst Set = <mark>Collection of SSB broadcast in a cell.</mark>
2. SS Burst Set = <mark>Contain 1 or more SSB.</mark>
3. Max number of SSB (L) in a SS Burst Set based on carrier frequency. 


| Carrier          | SCS      | Max No of SSB (L) |
|------------------|----------|-------------------|
| f <= 3GHz        | 15, 30   | 4                 |
| 3GHz < f <= 6GHz | 15, 30   | 8                 |
| f > 6GHz         | 120, 240 | 64                |


Picture from [1]

<br>
<img src="\nr_embb\img\nr_embb_ssburstperiodicity.png" width=100% height=100% />
<br>

?> SSB Periodicity is Configurable = 5 to 160 ms

Refer [1]

SSB Periodicity for Initial Acquisition: <mark>20ms.</mark><br>
SSB Periodicity for Idle/Connected Mode: <mark>10ms.</mark> ---> Is this compulsory??

---

#### PRACH Preamble Format

1. Based on Zadoff-Chu sequence. Same like LTE.
2. <mark>64 Preambles</mark> defined in each time-frequency PRACH occasion.
3. 2 type of preamble: <mark>Long and Short</mark>

<br>
<img src="\nr_embb\img\nr_embb_preambleformattype.png" width=70% height=70% />
<br>

***<mark>Structures of Preamble</mark>***

1. Cyclic Prefix (CP)
2. Preamble (SEQ)
3. Guard Time (GT)

Picture from [1]

<br>
<img src="\nr_embb\img\nr_embb_preamblestructure.png" width=50% height=50% />
<br>

***<mark>Long Preamble Format</mark>***

| Format | SCS      | SEQ Length | BW       | CP Dur    | SEQ Dur    | GT Dur    | Total Dur | Cell Radius | Use Cases        |
|--------|----------|------------|----------|-----------|------------|-----------|-----------|-------------|------------------|
| 0      | 1.25 kHz | 839        | 1.08 MHz | 103.13 μs | 1 x 800 μs | 96.88 μs  | 1 ms      | 14.5 km     | LTE Re-Farming   |
| 1      | 1.25 kHz | 839        | 1.08 MHz | 684.38 μs | 2 x 800 μs | 715.63 μs | 3 ms      | 100.2 km    | Large Cells      |
| 2      | 1.25 kHz | 839        | 1.08 MHz | 152.60 μs | 4 x 800 μs | 647.40 μs | 4 ms      | 22.1 km     | Large Cells / CE |
| 3      | 5 kHz    | 839        | 4.32 MHz | 103.13 μs | 4 x 200 μs | 96.88 μs  | 1 ms      | 14.5 km     | High Speed       |

<br>
<img src="\nr_embb\img\nr_embb_longpreamble.png" width=50% height=50% />
<br>

---

#### References

1. [Qualcomm](https://www.qualcommwirelessacademy.com/)
2. 3GPP TS 38.104
3. [Anritsu](https://dl.cdn-anritsu.com/ja-jp/test-measurement/reffiles/About-Anritsu/R_D/Technical/95/95-01.pdf)
4. [5G NR Bullets by Chris Johnson](https://www.amazon.co.jp/-/en/Chris-Johnson/dp/1081444592)