Topic: 4G LTE<br>
Sub-Topic: NB-IoT<br>
Date Written: 2019/02/26<br>
Date Edited: 2022/03/18<br>

---

#### 3GPP Roadmap

References: [1]

Picture from [2]

<br>
<img src="\lte_nbiot\img\lte_nbiot_3gpproadmap.png" width=100% height=100% />
<br>

---

#### UE Category

IoT UE category so far from Rel 13 to Rel 14. 

<br>
<img src="\lte_nbiot\img\lte_nbiot_uecatiot.png" width=100% height=100% />
<br>

Table version for easy copy:

| Device Category     | Cat-4                | Cat-1                | MTC Cat-0            | eMTC Cat-M1          | NB-IoT Cat-NB1     |
|---------------------|----------------------|----------------------|----------------------|----------------------|--------------------|
| 3GPP Release        | Release 8            | Release 8            | Release 12           | Release 13           | Release 13         |
| Device Bandwidth    | 20MHz                | 20MHz                | 20MHz                | 1.08MHz              | 180KHz             |
| Downlink Peak Rate  | 150Mbps              | 10Mbps               | *1Mbps               | *1Mbps               | <100kbps           |
| Uplink Peak Rate    | 50Mbps               | 5Mbps                | *1Mbps               | *1Mbps               | <100Kbps           |
| Device Duplex Mode  | Full Duplex          | Full Duplex          | Full or Half Duplex  | Full or Half Duplex  | Half Duplex        |
| Duplex              | FDD/TDD              | FDD/TDD              | FDD/TDD              | FDD/TDD              | FDD                |
| Modem Complexity    | Very High            | High                 | Medium               | Low                  | Very low           |
| Coverage Gain       | Base (MCL>140.7 dB)  | Base (MCL>140.7 dB)  | Base (MCL>140.7 dB)  | 15dB (MCL>155.7 dB)  | 23dB (MCL>164 dB)  |
| Battery Life        | Varies               | Varies               | Varies               | > 10 Years           | > 10 Years         |

<br>

***Cat NB UE category info:***

<br>
<img src="\lte_nbiot\img\lte_nbiot_uecatnb.png" width=50% height=50% />
<br>

Table version for easy copy:

| Device Category    | Cat NB1    | Cat NB2    |
|--------------------|------------|------------|
| 3GPP Release       | Release 13 | Release 14 |
| Device Bandwidth   | 180kHz     | 180kHz     |
| Downlink Peak Rate | 26kbps     | 127kbps    |
| Uplink Peak Rate   | 62kbps     | 159kbps    |
| Max Downlink TBS   | 680bits    | 2536bits   |
| Max Uplink TBS     | 1000bits   | 2536bits   |

---

#### Redefined Air Interface

Since R8, 3GPP has define lower complexity UE categories to compliment IoT vision. However, since R13, not only UE complexity is being reduced but even the air interface is being modified to suits specific needs of IoT. [3]

<mark>Why is it necessary to introduce specific architecture for IoT in air interface?</mark>

>The first main focus of the new air interface is changing the operating bandwidth of eMTC and NB-IoT. IoT UE does not need to monitor or decode any PRB outside the IoT system bandwidth. With this Bandwidth Low reduction, extra saving of power consumption can be achieved hence battery life savings can be up to 10 years. 

>The other reason is IoT technology requires to support deeper coverage. Deeper coverage means coverage gain compared to normal LTE should be increased by enabling certain IoT features such as Physical Channel Repetitions. eMTC able to support Maximum Coupling Loss (MCL) more than 155dB while NB-IoT able to support MCL more than 164dB.  

---

#### Cellular IoT Network Architecture

Currently no changes required in EPS to deploy eMTC and NB IoT in LTE system. Implementation of both eMTC and NB IoT can be done in the LTE carrier.

<br>
<img src="\lte_nbiot\img\lte_nbiot_iotnetarc.png" width=100% height=100% />
<br>

---

#### Carrier Deployment Mode

Key Concept:

1. Operating Bandwidth required for NB-IoT Cat NB1 UE: 200KHz
2. Can be deployed either in LTE band or even stand alone 
3. 1 PRB needed (1x180KHz): 180kHz
4. The position of the PRB depending on the configuration
5. 1 PRB cannot be shared with Cat-M1 UE and Common UE
6. Use same frame structure and waveform as LTE: DL OFDMA & UL SC-FDMA

<mark>Whats new?</mark> [2]

1. Transmit own MIB and SIBs
2. Transmit own Synchronization Signals – Can be different PCI
3. Transmit own Reference Signals
4. Transmit own physical channel in downlink and uplink
5. New type of uplink frame structure compared to LTE

<br>
<img src="\lte_nbiot\img\lte_nbiot_depinband.png" width=50% height=50% />
<br>

<br>
<img src="\lte_nbiot\img\lte_nbiot_depguardband.png" width=50% height=50% />
<br>

<br>
<img src="\lte_nbiot\img\lte_nbiot_depstandalone.png" width=50% height=50% />
<br>

***Note:***

    Bandwidth = 180 kHz
    1 PRB = 12 subcarriers separated 15 kHz
    1 Frame = 10 subframes (1024 SFN)
    1 subframe = 2 slots (1ms)
    1 slot = 0.5ms (7 OFDM symbols)
    1 HyperSFN = 1024 x 1024 radio frames

***Merit of Standalone NB-IoT compared to In Band NB-IoT***

>Implementing NB-IoT in a standalone mode would benefit LTE network operator in terms of not sacrificing 1 LTE PRB in their LTE network for NB-IoT. This would also mean that LTE network performance will not be a tradeoff.

>More RE Resource can be utilize by NB-IoT as the technology does not need to compromises with LTE PDCCH symbol and LTE CRS. All REs that is being used for LTE in In Band implementation can be used by NB-IoT.

>Also in capacity point of view, maximum MCS for downlink in standalone mode can support up to MCS 12 compared to MCS 10 in in band deployment mode. This will ensure more resource allocation bits and capacity improvement for NB-IoT.

>Having less risk of inter cell interference from LTE cell that does not implement NB-IoT PRB.

---

#### References

1. 3GPP TR 21.914
2. [Qualcomm](https://www.qualcomm.com/media/documents/files/leading-the-lte-iot-evolution-to-connect-the-massive-internet-of-things.pdf)