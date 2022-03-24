Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/08/31<br>
Date Edited: 2022/03/24<br>

---

#### Concept and Target

***Motivations***

3 main targets for 5G NR is to fulfill these motivations: [1]

1. eMBB 
2. URLLC 
3. mMTC 

Picture from [2]

<br>
<img src="\nr_embb\img\nr_embb_focus.png" width=100% height=100% />
<br>

***3PPP Requirements and Targets***

1. To achieve these targets, requirements guidelines has been made by standard bodies.
2. These target will not be achieved immediately in the initial implementation but slowly adapted by the industry players.

Refer [1] [3] [4]

<br>
<img src="\nr_embb\img\nr_embb_requirements.png" width=100% height=100% />
<br>

Comparison from [5]

<br>
<img src="\nr_embb\img\nr_embb_requirements2.png" width=100% height=100% />
<br>

***Use Cases Imagination***

Imagination of 5G NR use cases based on target and motivations.

Picture from [6]

<br>
<img src="\nr_embb\img\nr_embb_usecases.png" width=100% height=100% />
<br>

---

#### 3GPP Roadmap

1. 5G NR specifications are handled by 3GPP.
2. Specifications are contributed by patents from industrial players.
3. Once specifications are frozen, industrial players will develop the technology for commercialization.

Picture from [4]

<br>
<img src="\nr_embb\img\nr_embb_3gpproadmap.png" width=100% height=100% />
<br>

---

#### Key Technology Difference with LTE

Few key technologies that differentiate NR with LTE:

- High Bandwidth and mmWave
- Scalable Numerologies (SCS)
- Scalable TTI
- CORESET
- Dynamic TDD at Symbol Level
- Self Contained Slots in TDD
- Bandwidth Part (BWP)
- Beam Based Technology

***<mark>1. High Bandwidth and mmWave</mark>***

1. 5G NR able to enhance its radio technology to utilize higher bands (mmWave).
2. This allows the utilization of more bandwidth to support capacity and services need. 
3. In 4G, maximum bandwidth allowed is only 20MHz/EARFCN. However in 5G up to 400MHz is allowed.

<br>
<img src="\nr_embb\img\nr_embb_channelbw.png" width=100% height=100% />
<br>

Refer [7]

| Type         | Frequency Ranges      | Max Bandwidth |
|--------------|-----------------------|---------------|
| FR1 (Sub6)   | 410 MHz – 7125 MHz    | 100MHz        |
| FR2 (mmWave) | 24250 MHz – 52600 MHz | 400MHz        |

***<mark>2. Scalable Numerologies</mark>***

1. 5G NR still adopting OFDM as its waveform technology. This is similar like 4G LTE and Wi-Fi.
2. However, this OFDM waveform need to be tweaked to support higher 5G NR frequency and bandwidth.
3. Larger Numerology (µ) is introduced to reduce FFT signal processing complexity in higher bandwidth.

Picture modified from [4]

<br>
<img src="\nr_embb\img\nr_embb_scalablenum.png" width=100% height=100% />
<br>

***<mark>3. Scalable TTI</mark>***

1. OFDM waveform characteristics - When frequency domain properties change, time domain will change.
2. Multiple numerologies support in frequency domain also benefits flexibility in time domain.
3. Scalable TTI (Transmit Time Interval) is now supported when time domain becoming more flexible.

Picture from [4]

<br>
<img src="\nr_embb\img\nr_embb_scalabletti.png" width=100% height=100% />
<br>

***<mark>4. CORESET</mark>***

1. Control Region in 5G NR is known as CORESET (Control Resource Set).
2. In 4G LTE, frequency domain for Control Region occupied the whole channel bandwidth.
3. In 5G NR, CORESET allows Control Region size to be defined in frequency domain.

Picture from [8]

<br>
<img src="\nr_embb\img\nr_embb_coreset.png" width=100% height=100% />
<br>

***<mark>5. Dynamic TDD at Symbol Level</mark>***

1. 5G NR supports dynamic change of DL and UL symbols for TDD transmission system.
2. The flexible symbols can be configured semi statically via RRC or dynamically by PDCCH.
3. 5G NR supports symbol level TDD configuration instead of subframe level in 4G LTE.

Picture from [4]

<br>
<img src="\nr_embb\img\nr_embb_dynamictdd.png" width=100% height=100% />
<br>

***<mark>6. Self Contained Slots in TDD</mark>***

1. 5G NR allows scheduling (Grant), transmission (Data), and feedback (HARQ) to be done in one slot.
2. This feature is to support low latency requirements in 5G NR for TDD.

In FDD Cases:

    In 4G LTE FDD, Grant -> Data -> HARQ (-> = 4ms)
    In 5G NR FDD, Grant -> Data -> HARQ (-> = Slot Length)

In TDD Cases:

    In 4G LTE TDD, Grant -> Data -> HARQ (-> = Depends on TDD Subframe Config)
    In 5G NR TDD, Grant -> Data -> HARQ (-> = In Same Slot)

Picture modified from [4]

<br>
<img src="\nr_embb\img\nr_embb_selfcontainedslot.png" width=100% height=100% />
<br>

***<mark>7. Bandwidth Part</mark>***

1. BWP (Bandwidth Part) is introduced to allow UE to be configured with lower channel bandwidth.
2. This will enable multiple use cases in 5G NR target and motivations. 

Picture from [9]

<br>
<img src="\nr_embb\img\nr_embb_bwp.png" width=100% height=100% />
<br>

***<mark>8. Beam Based Technology</mark>***

1. 5G NR adopted beam based coverage for all its signals and channels.
2. This provide more gain to its coverage especially for high frequency signals that easily attenuated.
3. In 4G LTE, coverage is very limited since CRS and PDCCH coverage is based on fix beam.

<br>
<img src="\nr_embb\img\nr_embb_beam.png" width=100% height=100% />
<br>

---

#### References

1. 3GPP TR 38.913 Section 6
2. [Samsung](https://www.samsung.com/global/business/networks/insights/blog/5g-is-now-part-1-2018-the-year-of-5g/)
3. 3GPP TR 36.913  
4. [Qualcomm](https://www.qualcomm.com/media/documents/files/whitepaper-making-5g-nr-a-reality.pdf)
5. [Docomo](https://www.docomo.ne.jp/english/binary/pdf/corporate/technology/rd/technical_journal/bn/vol19_3/vol19_3_003en.pdf)
6. [ETSI](https://www.etsi.org/technologies/5G)
7. 3GPP TS 38.101
8. [Sharetechnote](https://www.sharetechnote.com/html/5G/5G_ResourceAllocationUnit.html)
9. [Keysight](https://www.3g4g.co.uk/5G/5Gtech_video0022_01.pdf)