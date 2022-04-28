Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/08/31<br>
Date Edited: 2022/03/31<br>

---

#### Resource Grid and Waveform

1. Resource in NR are layout as a grid consist of 2 main components 1) <mark>Freq Domain Resource</mark> 2) <mark>Time Domain Resource.</mark>
2. Data propagated in air interface (Uu) through waveforms.

Refer [1]

<br>
<img src="\nr_embb\img\nr_embb_resourcegrid.png" width=100% height=100% />
<br>

Some important terminologies:

    FFT: Fast Fourier Transform
    RB: Resource Block
    RE: Resource Element
    SCS: Sub Carrier Spacing
    OFDM: Orthogonal Frequency Division Multiplexing
    CP: Cyclic Prefix
    ISI: Inter-Symbol Interference


***NR Resource Structure*** 

1. In frequency domain, 12 OFDM subcarriers separated with SCS will form 1 RB.
2. In time domain, 14 OFDM symbols will form 1 Slot.

<br>
<img src="\nr_embb\img\nr_embb_resourcegrid2.png" width=100% height=100% />
<br>


***OFDM Waveform Properties*** 

1. Similar like LTE and Wi-Fi, OFDM is selected as waveform for NR air interface.
2. In OFDM, frequency domain subcarrier length are inversely proportion to time domain symbol length.  

<br>
<img src="\nr_embb\img\nr_embb_ofdmwaveform.png" width=100% height=100% />
<br>

More reading in [2] regarding waveform candidate analysis for 5G. However, at the end, OFDMA is chosen as 5G standard waveform.

---

#### Frequency Domain

***<mark>Numerology</mark> vs <mark>Subcarrier Spacing</mark>*** 

Key Concepts [3] [4] [5]

1. In frequency domain, numerology is mapped with SCS. <mark>NR supported up to 5 numerologies (µ).</mark>
2. In LTE, only 1 SCS is supported which is 15kHz.
3. Specs also define numerology supported by physical channels and signals.

SCS Formula:

>SCS = (2^µ)*15kHz

<br>
<img src="\nr_embb\img\nr_embb_numerology.png" width=100% height=100% />
<br>

Table for easy copy:

| Numerology (µ) | SCS (kHz) | CP Type (Time Domain) | Supported for Data (PDSCH, PUSCH) | Supported for Sync (PSS,SSS,PBCH) |
|----------------|-----------|-----------------------|-----------------------------------|-----------------------------------|
| 0              | 15        | Normal                | Yes                               | Yes                               |
| 1              | 30        | Normal                | Yes                               | Yes                               |
| 2              | 60        | Normal, Extended      | Yes                               | No                                |
| 3              | 120       | Normal                | Yes                               | Yes                               |
| 4              | 240       | Normal                | No                                | Yes                               |

<br>
<img src="\nr_embb\img\nr_embb_numerology2.png" width=70% height=70% />
<br>

?> Note: Number of RBs within the channel bandwidth will reduced when numerology (µ) is higher. 

<br>
<img src="\nr_embb\img\nr_embb_rbnumber.png" width=100% height=100% />
<br>

***NR Frequency Ranges (FR)***

Operating bands are separated into 2 categories in NR: 1) <mark>FR1 (Sub 6)</mark> 2) <mark>FR2 (mmWave).</mark> [6]

<br>
<img src="\nr_embb\img\nr_embb_fr.png" width=100% height=100% />
<br>

Table for easy copy:

| Ranges Name | Initial | Frequency Ranges      | Maximum Bandwidth |
|-------------|---------|-----------------------|-------------------|
| FR1         | Sub6    | 450 MHz – 6000 MHz    | 100MHz            |
| FR2         | mmWave  | 24250 MHz – 52600 MHz | 400MHz            |

Operating bands based on 3GPP: [5]

<br>
<img src="\nr_embb\img\nr_embb_operatingbands.png" width=100% height=100% />
<br>

***Supported <mark>Bandwidth</mark> vs <mark>RB Number</mark>*** 

RB number that has been specified by 3GPP based on channel bandwidth and SCS. [5]

<br>
<img src="\nr_embb\img\nr_embb_supportedbw.png" width=100% height=100% />
<br>

Table for easy copy: [FR1]

| SCS (kHz) | 5MHz | 10MHz | 15MHz | 20 MHz | 25 MHz | 30 MHz | 40 MHz | 50MHz | 60 MHz | 80 MHz | 100 MHz |
|-----------|------|-------|-------|--------|--------|--------|--------|-------|--------|--------|---------|
|           | NRB  | NRB   | NRB   | NRB    | NRB    | NRB    | NRB    | NRB   | NRB    | NRB    | NRB     |
| 15        | 25   | 52    | 79    | 106    | 133    | 160    | 216    | 270   | N/A    | N/A    | N/A     |
| 30        | 11   | 24    | 38    | 51     | 65     | 78     | 106    | 133   | 162    | 217    | 273     |
| 60        | N/A  | 11    | 18    | 24     | 31     | 38     | 51     | 65    | 79     | 107    | 135     |

Table for easy copy: [FR2]

| SCS (kHz) | 50MHz | 100MHz | 200MHz | 400 MHz |
|-----------|-------|--------|--------|---------|
|           | NRB   | NRB    | NRB    | NRB     |
| 60        | 66    | 132    | 264    | N/A     |
| 120       | 32    | 66     | 132    | 264     |

***Minimum Guard Band***

In NR, the guard band is standardized based on channel bandwidth, number of RB, and SCS. [5]

<mark>Minimum Guard band Calculation:</mark>

    The minimum guard bands have been calculated using the following equation: 

    “(Channel Bandwidth x 1000 (kHz) - RB value x SCS x 12) / 2 - SCS/2”

    Taking example for 5MHz channel BW with 25 NRB & 15kHz Subcarrier Spacing

    >> (5 x 1000 – 25 x 15 x 12) / 2 – 15 / 2
    >> (5000kHz – 4500kHz) / 2 – 15kHz / 2
    >> 500kHz / 2 – 7.5kHz
    >> 242.5 kHz

<br>
<img src="\nr_embb\img\nr_embb_minguardband.png" width=100% height=100% />
<br>

Table for easy copy: [FR1]

| SCS (kHz) | 5MHz  | 10MHz | 15MHz | 20 MHz | 25 MHz | 30 MHz | 40 MHz | 50MHz | 60 MHz | 80 MHz | 100 MHz |
|-----------|-------|-------|-------|--------|--------|--------|--------|-------|--------|--------|---------|
|           | kHz   | kHz   | kHz   | kHz    | kHz    | kHz    | kHz    | kHz   | kHz    | kHz    | kHz     |
| 15        | 242.5 | 312.5 | 382.5 | 452.5  | 522.5  | 592.5  | 552.5  | 692.5 | N/A    | N/A    | N/A     |
| 30        | 505   | 665   | 645   | 805    | 785    | 945    | 905    | 1045  | 825    | 925    | 845     |
| 60        | N/A   | 1010  | 990   | 1330   | 1310   | 1290   | 1610   | 1570  | 1530   | 1450   | 1370    |

Table for easy copy: [FR2]

| SCS (kHz) | 50MHz | 100MHz | 200MHz | 400 MHz |
|-----------|-------|--------|--------|---------|
|           | kHz   | kHz    | kHz    | kHz     |
| 60        | 1210  | 2450   | 4930   | N/A     |
| 120       | 1900  | 2420   | 4900   | 9860    |

<mark>Numerology Design</mark>

Based on design and service requirements, numerology implementation can be estimated. However, the designation will always be up to certain limitations. [7]

?> Tips 1: If cell range is high, using higher SCS is not advisable because TTI length becoming shorter. High inter symbol interference might occur.

?> Tips 2: In high frequency, usually only high SCS is supported to allow lower FFT processing complexity in transmitter/receiver.

!> Note: Use higher SCS can result to lower latency as TTI length become shorter.

<br>
<img src="\nr_embb\img\nr_embb_numerologydesign.png" width=100% height=100% />
<br>

---

#### Time Domain

Key Concept: [5]

1. NR slot length changes depending on the SCS used in frequency domain.
2. The definition of <mark>Radio Frame = 10ms</mark> and <mark>Subframe = 1ms</mark> is still similar with LTE.

<br>
<img src="\nr_embb\img\nr_embb_radioframe.png" width=100% height=100% />
<br>

***Slot Length*** [1] [3]

1. Slot Length in NR is measured based on how many slot can be fit inside 1ms Subframe.
2. Slot Length is affected based on the numerology (µ) used in frequency domain.
3. Slot Length is will not be affected by CP config, only symbol number is changed based on CP config.

<br>
<img src="\nr_embb\img\nr_embb_slotlength.png" width=100% height=100% />
<br>

<br>
<img src="\nr_embb\img\nr_embb_slotlength2.png" width=100% height=100% />
<br>

***Scalable TTI*** [8]

1. In LTE, TTI is always fixed which is every 1ms Subframe.
2. NR allows the options to choose whether to use a Slot based TTI or Non Slot based TTI (Mini Slot).
3. Mini Slot concepts allows for more lower TTI to adopt low latency scheduling.

<br>
<img src="\nr_embb\img\nr_embb_scalabletti2.png" width=100% height=100% />
<br>

***<mark>5G Frame Structure Summary</mark>***

NR frame structure overall overview in time domain. [7]

<br>
<img src="\nr_embb\img\nr_embb_timedomain.png" width=100% height=100% />
<br>

***Slot Format*** [3] [9] [8]

1. Slot Format in NR indicates the types of direction (DL, UL, Flexible) for symbol transmission in a slot.
2. Flexible symbol have 2 purpose 1) DL-UL Transmission Gap 2) Semi Static & Dynamic TDD.

Legend:

    D: Downlink
    U: Uplink
    F: Flexible 

<br>
<img src="\nr_embb\img\nr_embb_slotformat.png" width=100% height=100% />
<br>

---

#### TDD Structures

NR TDD frame structure are designed to be flexible in terms DL and UL allocation compared to LTE that dependent on predefined table. NR starts supporting Dynamic and Semi Static TDD configuration on symbol level by using Dedicated RRC Signaling and DCI carrying SFI-RNTI. [8] [10]

<br>
<img src="\nr_embb\img\nr_embb_tddframe.png" width=100% height=100% />
<br>

<mark>Different characteristics between NR and LTE:</mark>

<br>
<img src="\nr_embb\img\nr_embb_tddnrlte.png" width=70% height=70% />
<br>

| Parameter              | NR                           | LTE      |
|------------------------|------------------------------|----------|
| Time Domain Level      | Slot, Symbol                 | Subframe |
| Operation Flexibility  | Static, Semi-Static, Dynamic | Static   |
| Predefined Table       | No                           | Yes      |

***<mark>Static TDD Configuration (via RMSI SIB1)</mark>***

Key concept: [9] [11]

1. UE will be provided with TDD slot patterns (Pattern 2 is optional) via RMSI (SIB1).
2. UE will sets the slot configuration based on Pattern 1 followed by Pattern 2 if provided.

<br>
<img src="\nr_embb\img\nr_embb_statictddconfig.png" width=100% height=100% />
<br>

?> RMSI: Required Minimum System Information (SIB1)

***Eg: TDD Pattern Illustration***

In Example below, TDD slot format translates to <mark>DL = 74.4% UL = 22.8% Flex = 2.8%.</mark>

<br>
<img src="\nr_embb\img\nr_embb_tddpatternexample.png" width=100% height=100% />
<br>

Eg: SIB 1 parameters:

| tdd-UL-DL-ConfigurationCommon       | Pattern1 | Pattern2 |
|-------------------------------------|----------|----------|
| dl-UL-TransmissionPeriodicity       | ms2      | ms2      |
| nrofDownlinkSlots                   | 3        | 4        |
| nrofDownlinkSymbols                 | 6        | 0        |
| nrofUplinkSlots                     | 2        | 0        |
| nrofUplinkSymbols                   | 4        | 0        |
| dl-UL-TransmissionPeriodicity-v1530 | ms3      | -        |

***<mark>Semi-Static TDD Configuration (via RRC Configuration)</mark>***

If the UE is additionally provided tdd-UL-DL-ConfigurationDedicated, the parameter tdd-UL-DLConfigurationDedicated overrides only flexible symbols per slot over the number of slots as provided by tdd-UL-DLConfigurationCommon. [9] [11]

?> Semi-Static TDD Configuration is provided to dedicated UE via RRC. Only flexible symbols are entitled to be overridden by this configuration

<br>
<img src="\nr_embb\img\nr_embb_semistatictddconfig.png" width=100% height=100% />
<br>

!> Note: Reference SCS will always follow Static configuration SCS

!> Note: Static and Semi-Static configuration will be common for each configured BWP

***<mark>Dynamic TDD Configuration (via PDCCH DCI Format 2_0)</mark>***

Dynamic TDD introduces scheduling based TDD configuration changed by instructing config via PDCCH DCI Format 2_0. [9] [11]

?> From RRC, UE will understand on which PDCCH to be monitored. If PDCCH contains SFI-RNTI (DCI Format 2_0), UE will change it slots based on SFI.

<br>
<img src="\nr_embb\img\nr_embb_dynamictddconfig.png" width=100% height=100% />
<br>

---

#### References

1. 3GPP TR 38.802
2. [Rohde & schwarz](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma271/1MA271_0e_5G_waveform_candidates.pdf)
3. 3GPP TS 38.211
4. 3GPP TS 38.300
5. [Sharetechnote](https://www.sharetechnote.com/html/5G/5G_Phy_Numerology.html)
6. 3GPP TS 38.101
7. [5G NR by Sassan Ahmadi](https://www.sciencedirect.com/book/9780081022672/5g-nr)
8. [Keysight](https://www.3g4g.co.uk/5G/5Gtech_video0022_01.pdf)
9. 3GPP TS 38.213
10. [Qualcomm](https://www.qualcomm.com/media/documents/files/whitepaper-making-5g-nr-a-reality.pdf)
11. 3GPP TS 38.331