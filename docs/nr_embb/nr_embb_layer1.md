Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/06/02<br>
Date Edited: 2022/07/06<br>

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
<img src="\nr_embb\img\nr_embb_preamblestructure.png" width=70% height=70% />
<br>

***<mark>Long Preamble Format</mark>***

| Format | SCS      | SEQ Length | BW       | CP Dur    | SEQ Dur    | GT Dur    | Total Dur | Cell Radius | Use Cases        |
|--------|----------|------------|----------|-----------|------------|-----------|-----------|-------------|------------------|
| 0      | 1.25 kHz | 839        | 1.08 MHz | 103.13 μs | 1 x 800 μs | 96.88 μs  | 1 ms      | 14.5 km     | LTE Re-Farming   |
| 1      | 1.25 kHz | 839        | 1.08 MHz | 684.38 μs | 2 x 800 μs | 715.63 μs | 3 ms      | 100.2 km    | Large Cells      |
| 2      | 1.25 kHz | 839        | 1.08 MHz | 152.60 μs | 4 x 800 μs | 647.40 μs | 4 ms      | 22.1 km     | Large Cells / CE |
| 3      | 5 kHz    | 839        | 4.32 MHz | 103.13 μs | 4 x 200 μs | 96.88 μs  | 1 ms      | 14.5 km     | High Speed       |

<br>
<img src="\nr_embb\img\nr_embb_longpreamble2.png" width=100% height=100% />
<br>

Picture from [1]

<br>
<img src="\nr_embb\img\nr_embb_longpreamble.png" width=100% height=100% />
<br>

***<mark>Short Preamble Format</mark>***

Picture from [1]

| Format | SCS    | SEQ Length | BW | CP Dur | SEQ Dur | GT Dur    | Total Dur | Cell Radius | Use Cases   |
|--------|--------|------------|----|--------|---------|-----------|-----------|-------------|-------------|
| A1     | 15 kHz | 139        |    |        |         | 0 μs      |           | 0.9 km      | Small Cell  |
| A2     | 15 kHz | 139        |    |        |         | 0 μs      |           | 2.1 km      | Normal Cell |
| A3     | 15 kHz | 139        |    |        |         | 0 μs      |           | 3.5 km      | Normal Cell |
| B1     | 15 kHz | 139        |    |        |         | 2.344 μs  |           | 0.35 km     | Small Cell  |
| B2     | 15 kHz | 139        |    |        |         | 7.031 μs  |           | 1.1 km      | Normal Cell |
| B3     | 15 kHz | 139        |    |        |         | 11.719 μs |           | 1.8 km      | Normal Cell |
| B4     | 15 kHz | 139        |    |        |         | 25.781 μs |           | 3.9 km      | Normal Cell |
| C0     | 15 kHz | 139        |    |        |         | 35.677 μs |           | 5.3 km      | Normal Cell |
| C1     | 15 kHz | 139        |    |        |         | 94.922 μs |           | 14.2 km     | Normal Cell |

<br>
<img src="\nr_embb\img\nr_embb_shortpreamble.png" width=100% height=100% />
<br>

!> TODO: How to calculate short preamble SEQ length and total duration.

<br>
<img src="\nr_embb\img\nr_embb_shortpreamble2.png" width=100% height=100% />
<br>

?> Only 1 preamble format can be configured per cell

---

#### Reference Signal Map

Picture from [1]

<br>
<img src="\nr_embb\img\nr_embb_rsstructure.png" width=100% height=100% />
<br>

!> PTRS is only for mmWave.

***<mark>LTE vs NR</mark>***

| RS Use Case                  | LTE         | NR          |
|------------------------------|-------------|-------------|
| DL Channel State Information | CRS, CSI-RS | CSI-RS      |
| UL Channel State Information | SRS         | SRS         |
| Data Channel Demodulation    | CRS, DMRS   | DMRS        |
| Control Channel Demodulation | CRS         | DMRS        |
| Phase Tracking (mmWave)      | -           | PTRS        |
| Time & Freq Tracking         | CRS         | TRS         |
| Beam Management              | -           | SSB, CSI-RS |
| Radio Link Monitoring        | CRS         | SSB, CSI-RS |
| RRM Measurment               | CRS         | SSB, CSI-RS |

?> LTE CRS (Always ON) is replaced with multiple UE-Specific on demand RS signals in 5G NR

***<mark>RS Based on Channels Comparison</mark>***

| Type             | DMRS                             | PTRS         | CSI-RS            | SRS          |
|------------------|----------------------------------|--------------|-------------------|--------------|
| Direction        | UL/DL                            | UL/DL        | DL                | UL           |
| Frequency        | Sub6/mmWave                      | mmWave       | Sub6/mmWave       | Sub6/mmWave  |
| Channel          | PDSCH, PDCCH, PBCH, PUSCH, PUCCH | PDSCH, PUSCH | PDSCH, PDCCH, SSB | PUCCH, PUSCH |
| UE or Cell Level | UE, Cell for PBCH                | UE           | UE                | UE           |


---

#### CORESET

1. CORESET = Control Resource Set.
2. Semi statically configured by RRC - Size, Location, Periodicty.
3. In time domain can occupy - 1 to 3 symbols.
4. In frequency domain can occupy in sets of 6 PRBs - Min 6 PRBs, Max 270 PRBs.
5. Might not exist in all BWP - it is cell level config and UE specific.
6. PDSCH can be allocated in unused CORESET.

***<mark>LTE vs NR: Control Channel Resource Perspective</mark>***

| Item             | LTE                              | NR                              |
|------------------|----------------------------------|---------------------------------|
| Frequency Domain | Whole bandwidth                  | Can change (PRB Min 6, Max 270) |
| Time Domain      | 1 to 3 Symbol (Adaptive, by CFI) | 1 to 3 Symbol (Fix, no CFI)     |

Picture from [1]

<br>
<img src="\nr_embb\img\nr_embb_coreset2.png" width=100% height=100% />
<br>

?> Semi Static: RRC can change the configuration using RRC Connection Reconfiguration Message.

***Example of CORESET settings from RRC Connection Reconfiguration Message:***

<br>
<img src="\nr_embb\img\nr_embb_coresetsettings.png" width=100% height=100% />
<br>

***<mark>How CORESET is Utilized as PDCCH/DCI?</mark>***

1. 12 RE (12 Subcarriers x 1 Symbol) will form 1 REG.
2. 6 REG will form 1 CCE.
3. Depends on CCE aggregation level, CCE will combine to form PDCCH/DCI.
4. For example, <mark>if CCE aggregation level is = 4, means it needs 4 CCE to form 1 PDCCH/DCI.</mark>

<br>
<img src="\nr_embb\img\nr_embb_cceagg.png" width=70% height=70% />
<br>

?> Supported CCE Aggregation Level: 1, 2, 4, 8, 16. Usually it changes dynamically. If in poor RF, higher CCE aggregation level is used to give better chance of decoding / higher pdcch decoding success rate.

***Example from real data:***

<br>
<img src="\nr_embb\img\nr_embb_cceagg2.png" width=70% height=70% />
<br>


---

#### SFI

Refer [5] [6]

1. Slot format concept for 5G NR is almost similar concept to LTE TDD subframe configuration format.
2. However, slot format in NR is being used for both TDD and FDD and the assignment is at symbol level.
3. DL and UL assignment changes at a symbol level.
4. So many diverse slot format to allow flexible allocation in 5G NR.
5. Slot Format works for both  FDD and TDD (FDD: Use Format 0 and Format 1).
6. Slot aggregation is supported (Multiple slots in single data transmission).
7. Slot Format Indication informs the UE  whether an OFDM symbol is for Downlink (D), Uplink (U), or Flexible (U).
8. SFI can be sent through DCI Format 2_0 or higher layer (RRC).

***<mark>SFI Format Table</mark>***

?> Number 0 - 13 refer to symbols.

    D: Downlink
    U: Uplink
    F: Flexible

| Format | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |
|--------|---|---|---|---|---|---|---|---|---|---|----|----|----|----|
| 0      | D | D | D | D | D | D | D | D | D | D | D  | D  | D  | D  |
| 1      | U | U | U | U | U | U | U | U | U | U | U  | U  | U  | U  |
| 2      | F | F | F | F | F | F | F | F | F | F | F  | F  | F  | F  |
| 3      | D | D | D | D | D | D | D | D | D | D | D  | D  | D  | F  |
| 4      | D | D | D | D | D | D | D | D | D | D | D  | D  | F  | F  |
| 5      | D | D | D | D | D | D | D | D | D | D | D  | F  | F  | F  |
| 6      | D | D | D | D | D | D | D | D | D | D | F  | F  | F  | F  |
| 7      | D | D | D | D | D | D | D | D | D | F | F  | F  | F  | F  |
| 8      | F | F | F | F | F | F | F | F | F | F | F  | F  | F  | U  |
| 9      | F | F | F | F | F | F | F | F | F | F | F  | F  | U  | U  |
| 10     | F | U | U | U | U | U | U | U | U | U | U  | U  | U  | U  |
| 11     | F | F | U | U | U | U | U | U | U | U | U  | U  | U  | U  |
| 12     | F | F | F | U | U | U | U | U | U | U | U  | U  | U  | U  |
| 13     | F | F | F | F | U | U | U | U | U | U | U  | U  | U  | U  |
| 14     | F | F | F | F | F | U | U | U | U | U | U  | U  | U  | U  |
| 15     | F | F | F | F | F | F | U | U | U | U | U  | U  | U  | U  |
| 16     | D | F | F | F | F | F | F | F | F | F | F  | F  | F  | F  |
| 17     | D | D | F | F | F | F | F | F | F | F | F  | F  | F  | F  |
| 18     | D | D | D | F | F | F | F | F | F | F | F  | F  | F  | F  |
| 19     | D | F | F | F | F | F | F | F | F | F | F  | F  | F  | U  |
| 20     | D | D | F | F | F | F | F | F | F | F | F  | F  | F  | U  |
| 21     | D | D | D | F | F | F | F | F | F | F | F  | F  | F  | U  |
| 22     | D | F | F | F | F | F | F | F | F | F | F  | F  | U  | U  |
| 23     | D | D | F | F | F | F | F | F | F | F | F  | F  | U  | U  |
| 24     | D | D | D | F | F | F | F | F | F | F | F  | F  | U  | U  |
| 25     | D | F | F | F | F | F | F | F | F | F | F  | U  | U  | U  |
| 26     | D | D | F | F | F | F | F | F | F | F | F  | U  | U  | U  |
| 27     | D | D | D | F | F | F | F | F | F | F | F  | U  | U  | U  |
| 28     | D | D | D | D | D | D | D | D | D | D | D  | D  | F  | U  |
| 29     | D | D | D | D | D | D | D | D | D | D | D  | F  | F  | U  |
| 30     | D | D | D | D | D | D | D | D | D | D | F  | F  | F  | U  |
| 31     | D | D | D | D | D | D | D | D | D | D | D  | F  | U  | U  |
| 32     | D | D | D | D | D | D | D | D | D | D | F  | F  | U  | U  |
| 33     | D | D | D | D | D | D | D | D | D | F | F  | F  | U  | U  |
| 34     | D | F | U | U | U | U | U | U | U | U | U  | U  | U  | U  |
| 35     | D | D | F | U | U | U | U | U | U | U | U  | U  | U  | U  |
| 36     | D | D | D | F | U | U | U | U | U | U | U  | U  | U  | U  |
| 37     | D | F | F | U | U | U | U | U | U | U | U  | U  | U  | U  |
| 38     | D | D | F | F | U | U | U | U | U | U | U  | U  | U  | U  |
| 39     | D | D | D | F | F | U | U | U | U | U | U  | U  | U  | U  |
| 40     | D | F | F | F | U | U | U | U | U | U | U  | U  | U  | U  |
| 41     | D | D | F | F | F | U | U | U | U | U | U  | U  | U  | U  |
| 42     | D | D | D | F | F | F | U | U | U | U | U  | U  | U  | U  |
| 43     | D | D | D | D | D | D | D | D | D | F | F  | F  | F  | U  |
| 44     | D | D | D | D | D | D | F | F | F | F | F  | F  | U  | U  |
| 45     | D | D | D | D | D | D | F | F | U | U | U  | U  | U  | U  |
| 46     | D | D | D | D | D | F | U | D | D | D | D  | D  | F  | U  |
| 47     | D | D | F | U | U | U | U | D | D | F | U  | U  | U  | U  |
| 48     | D | F | U | U | U | U | U | D | F | U | U  | U  | U  | U  |
| 49     | D | D | D | D | F | F | U | D | D | D | D  | F  | F  | U  |
| 50     | D | D | F | F | U | U | U | D | D | F | F  | U  | U  | U  |
| 51     | D | F | F | U | U | U | U | D | F | F | U  | U  | U  | U  |
| 52     | D | F | F | F | F | F | U | D | F | F | F  | F  | F  | U  |
| 53     | D | D | F | F | F | F | U | D | D | F | F  | F  | F  | U  |
| 54     | F | F | F | F | F | F | F | D | D | D | D  | D  | D  | D  |
| 55     | D | D | F | F | F | U | U | U | D | D | D  | D  | D  | D  |

!> Format 64 - 254: Reserved.

!> Format 255: UE determines the slot format for the slot based on tdd-UL-DL-ConfigurationCommon, or tdd-ULDL-ConfigurationDedicated and, if any, on detected DCI formats.

***<mark>Eg: Slot Format Combination Through RRC & DCI Format 2-0</mark>***

Picture from [4]

<br>
<img src="\nr_embb\img\nr_embb_sficomb.png" width=100% height=100% />
<br>


---

#### DCI Format

1. DCI = Downlink Control information.
2. DCI is a format/information carried in PDCCH.
3. DCI contains info the UE needs to identify RBs in that subframe and decode it.
4. Information in DCI includes MCS, RV, HARQ, RNTI, CRC, and more.

Table from [7] [8]

| DCI Format | Usage                                                                                                                                             |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| 0_0        | Scheduling of PUSCH in one cell (fallback-mode)                                                                                                   |
| 0_1        | Scheduling of PUSCH in one cell (regular)                                                                                                         |
| 1_0        | Scheduling of PDSCH in one cell (fallback-mode)                                                                                                   |
| 1_1        | Scheduling of PDSCH in one cell (regular)                                                                                                         |
| 2_0        | Notifying a group of UEs of the slot format - Slot Fromat Indicator (SFI)                                                                         |
| 2_1        | Notifying a group of UEs of the PRB(s) and OFDM symbol(s) where UE may assume no transmission is intended for the UE - Preemption Indicators (PI) |
| 2_2        | Transmission of TPC commands for PUCCH and PUSCH                                                                                                  |
| 2_3        | Transmission of a group of TPC commands for SRS transmissions by one or more UEs                                                                  |
| 2_4        | Notifying the PRB(s) and OFDM symbol(s) where UE cancels the corresponding UL transmission from the UE                                            |
| 2_5        | Notifying the availability of soft resources                                                                                                      |
| 2_6        | Notifying the power saving information outside DRX Active Time for one or more Ues                                                                |
| 3_0        | Scheduling of NR sidelink in one cell                                                                                                             |
| 3_1        | Scheduling of LTE sidelink in one cell                                                                                                            |


?> Fallback-mode: Single layer transmission with RA type 1 supported


---

#### UCI (PUCCH Format)

1. PUCCH carries UCI.
2. UCI contains <mark>CSI, ACK/NACK, SR</mark>.

UCI carries:

    CSI: Channel State Infomation
    ACK/NACK: Acknowledgement Info - When no PUSCH grant available, use PUCCH
    SR: Scheduling Request

?> UCI can be carried by PUSCH too. [9]

<mark>PUCCH Format</mark> defined based on:

1. Short/Long Duration
2. Payload Size Ranges
3. Multiplexing Capabilities

Table form [1]

| PUCCH Format | OFDM Symbol # Length | UCI Bits | Waveform     | Description                                      |
|--------------|----------------------|----------|--------------|--------------------------------------------------|
| 0            | 1-2                  | <= 2     | CGS Sequence | Short PUCCH with 1-2 bits UCI                    |
| 1            | 4-14                 | <= 2     | CGS Sequence | Long PUCCH with 1-2 bits UCI                     |
| 2            | 1-2                  | > 2      | OFDM         | Short PUCCH with > 2 bits UCI                    |
| 3            | 4-14                 | > 2      | DFT-S-OFDM   | Long PUCCH with > 2 bits UCI (No multiplexing)   |
| 4            | 4-14                 | > 2      | DFT-S-OFDM   | Long PUCCH with > 2 bits UCI (With Multiplexing) |

!> Why in DL term 'DCI Format' is used but in UL term 'PUCCH Format is used'? Why not use term 'UCI Format'?: [Personal Guess] In DL, PDCCH always in the same physical form, but the information that it carries (DCI) defer based on type of scheduling or information that wanted to be sent to the UE. Hence, the DCI itself requires different format. In UL, the PUCCH physical form differs depending on how many bits of UCI needed to be carried by PUCCH.

---

#### PDSCH/PUSCH Channel Processing

General flow from [4]:

<br>
<img src="\nr_embb\img\nr_embb_chprocessflow.png" width=100% height=100% />
<br>

Detailed flow from [1]:

<br>
<img src="\nr_embb\img\nr_embb_chprocessflow2.png" width=100% height=100% />
<br>

---

#### References

1. [Qualcomm](https://www.qualcommwirelessacademy.com/)
2. 3GPP TS 38.104
3. [Anritsu](https://dl.cdn-anritsu.com/ja-jp/test-measurement/reffiles/About-Anritsu/R_D/Technical/95/95-01.pdf)
4. [5G NR Bullets by Chris Johnson](https://www.amazon.co.jp/-/en/Chris-Johnson/dp/1081444592)
5. 3GPP TS 38.211 Section 4.2
6. 3GPP TS 38.213 Section 11.1.1
7. [Sharetechnote](https://www.sharetechnote.com/html/5G/5G_DCI.html)
8. 3GPP TS 38.211 Section 7.3
9. [Sharetechnote 2](https://www.sharetechnote.com/html/5G/5G_UCI.html#Contents_of_UCI)