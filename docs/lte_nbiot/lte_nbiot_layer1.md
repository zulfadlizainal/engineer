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

<mark>Table from</mark> [2]

| Signal | Subframe    | Periodicity | Purpose                       |
|--------|-------------|-------------|-------------------------------|
| NPSS   | Subframe #5 | 10ms        | Time and Freq Synchronization |
| NSSS   | Subframe #9 | 20ms        | PCI Information               |



***Subframe Allocation for NPSS and NSSS***

<mark>Assuming In Band Deployment with LTE FDD DL having CF1 Format 3 for PDCCH and using 4 Antenna port for CRS.</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_npssnssssuballoc.png" width=100% height=100% />
<br>

---

#### NRS

Key Concept: [1]

1. The narrowband reference signal (NRS) is transmitted in all subframes which may be used for broadcast or dedicated DL transmission, no matter if data is actually transmitted or not.
2. There are two NB-IoT downlink transmission schemes defined in all operation modes: Single ant port (port 0) or Two ant port (port 0 and 1 transmit diversity).
3. NRS is always present without any condition for every subframe carrying  NPDCCH or NPDSCH.
4. NRS is not present whenever the subframe is carrying NPSS and NSSS.


***Subframe carrying NPSS or NSSS – NRS not present***

<mark>Assuming In Band Deployment with LTE FDD DL having CF1 Format 3 for PDCCH and using 4 Antenna port for CRS.</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_nrsnotpresent.png" width=100% height=100% />
<br>


***Subframe carrying NPDCCH or NPDSCH – NRS present***

<mark>Assuming In Band Deployment with LTE FDD DL having CF1 Format 3 for PDCCH and using 4 Antenna port for CRS.</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_nrspresent.png" width=100% height=100% />
<br>

---

#### NPBCH

Key Concept: [1]

1. NPBCH carries the Narrowband Master Information Block (MIB-NB).
2. The MIB-NB contains 34 bits and is transmitted over a time period of 640ms, i.e. 64 radio frames.

!> Transmission of Master Information Block (MIB-NB)

!> Uses Subframe #0 of every radio frame

!> MIB-NB TTI is 640 ms

***Subframe carrying NPBCH - Transmitted in Subframe #0 every 640ms***

<br>
<img src="\lte_nbiot\img\lte_nbiot_npbch.png" width=100% height=100% />
<br>

---

#### References

1. [Rohde & Schwarz](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma266/1MA266_0e_NB_IoT.pdf)
2. Intel, CIoT Presentation for IEEE Globecom 2016