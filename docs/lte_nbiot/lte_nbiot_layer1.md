Topic: 4G LTE<br>
Sub-Topic: NB-IoT<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/03/18<br>

---

#### Physical Channel Mapping

New physical channels is being defined for NB-IoT despite the same functionality with LTE. [1]

?> For downlink, new channel defined are NPBCH, NPDSCH, and NPDCCH. No equivalent to PCFICH and PHICH in LTE defined due to change in control channel mechanism. 

?> For uplink, new channel defined are NPRACH and NPUSCH. All transmission in uplink except for RACH are sent over NPUSCH.  

<br>
<img src="\lte_nbiot\img\lte_nbiot_phymapdl.png" width=100% height=100% />
<br>

Downlink Physical Channels:

    NPBH: Narrowband Physical Broadcast Channel
    NPDCCH: Narrowband Physical Downlink Control Channel
    NPDSCH: Narrowband Physical Downlink Shared Channel

Downlink Physical Signals:

    NPSS: Narrowband Primary Synchronization Signals
    NSSS: Narrowband Secondary Synchronization Signals
    NRS: Narrowband Reference Signals


<br>
<img src="\lte_nbiot\img\lte_nbiot_phymapul.png" width=100% height=100% />
<br>

Uplink Physical Channels:

    NPUSCH: Narrowband Physical Uplink Shared Channel
    NPRACH: Narrowband Physical Random Access Channel

Uplink Physical Signals:

    DMRS: Demodulation Reference Signal

---

#### NPSS and NSSS

Key Concept: [1]

1. For a first synchronization in frame and subframe and in order to determine the Narrowband Cell ID (NCellID), the LTE concept of Primary Synchronization Signal (PSS) and Secondary Synchronization Signal (SSS) is reused.
2. NPSS and NSSS is being defined to determine PCI for NB-IoT.
3. Like in LTE, each cell has an assigned physical cell ID (PCI), the Narrowband physical cell ID (NCellID). Totally 504 different values for NCellID are defined.

Table from [2]

| Signal | Subframe    | Periodicity | Purpose                       |
|--------|-------------|-------------|-------------------------------|
| NPSS   | Subframe #5 | 10ms        | Time and Freq Synchronization |
| NSSS   | Subframe #9 | 20ms        | PCI Information               |

***Subframe Allocation for NPSS and NSSS***

<br>
<img src="\lte_nbiot\img\lte_nbiot_npssnssssuballoc.png" width=100% height=100% />
<br>

---

#### References

1. [Rohde & Schwarz](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma266/1MA266_0e_NB_IoT.pdf)
2. Intel, CIoT Presentation for IEEE Globecom 2016