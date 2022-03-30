Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/08/31<br>
Date Edited: 2022/03/30<br>

---

#### Resource Grid and Waveform

1. Resource in NR are layout as a grid consist of 2 main components 1) <mark>Freq Domain Resource</mark> 2) <mark>Time Domain Resource.</mark>
2. Data propagated in air interface (Uu) through waveforms.

Refer [1]

<br>
<img src="\nr_embb\img\nr_embb_resourcegrid.png" width=100% height=100% />
<br>

Terminology:

    FFT: Fast Fourier Transform
    RB: Resource Block
    RE: Resource Element
    SCS: Sub Carrier Spacing
    OFDM: Orthogonal Frequency Division Multiplexing


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
<img src="\nr_embb\img\nr_embb_numerology2.png" width=100% height=100% />
<br>

?> Note: Number of RBs within the channel bandwidth will reduced when numerology (µ) is higher. 

<br>
<img src="\nr_embb\img\nr_embb_rbnumber.png" width=100% height=100% />
<br>

***NR Frequency Ranges (FR)***

Operating bands are separated into 2 categories in NR: 1) <mark>FR1 (Sub 6)</mark> 2) <mark>FR2 (mmWave).</mark> [6]

<br>
<img src="\nr_embb\img\nr_embb_fr.png" width=70% height=70% />
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

#### References

1. 3GPP TR 38.802
2. [Rohde & schwarz](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma271/1MA271_0e_5G_waveform_candidates.pdf)
3. 3GPP TS 38.211
4. 3GPP TS 38.300
5. [Sharetechnote](https://www.sharetechnote.com/html/5G/5G_Phy_Numerology.html)
6. 3GPP TS 38.101
7. [5G NR by Sassan Ahmadi](https://www.sciencedirect.com/book/9780081022672/5g-nr)