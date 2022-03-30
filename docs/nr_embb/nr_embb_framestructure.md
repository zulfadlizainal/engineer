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

---

#### References

1. 3GPP TR 38.802