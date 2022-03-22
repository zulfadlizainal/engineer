Topic: 4G LTE<br>
Sub-Topic: NB-IoT<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/03/22<br>

---

#### eMTC vs NB-IoT Frame Structure

1. Both eMTC and NB-IoT using the same frame structure as LTE.
2. NB-IoT uplink introducing a new concept of single tone transmission.
3. NB-IoT uplink introducing a new unit for resource called RU (Resource Unit).

<br>
<img src="\lte_nbiot\img\lte_nbiot_emtcvsnb.png" width=70% height=70% />
<br>

Table version for easy copy:

| Element                | eMTC     | NB-IoT                        |
|------------------------|----------|-------------------------------|
| DL Waveform            | OFDMA    | OFDMA                         |
| UL Waveform            | SC-FDMA  | SC-FDMA (Support Single Tone) |
| DL Subcarrier Spacing  | 15kHz    | 15KHz                         |
| UL Subcarrier Spacing  | 15KHz    | 15KHz, 3.75KHz                |
| DL Resource Size       | PRB      | PRB                           |
| UL Resource Size       | PRB      | RU                            |

<br>
<img src="\lte_nbiot\img\lte_nbiot_lteframestruct.png" width=100% height=100% />
<br>

---

#### DL RE Mapping

Refer [1]

1. NB-IoT still adapting same OFDMA frame structure as LTE.
2. However, not all RE can be used for NB-IoT resources if NB-IoT is being deployed inside an LTE band.
3. More RE resource can be utilized in standalone NB-IoT deployment.
4. LTE control channel region defined by CFI and LTE CRS cannot be read by Cat NB-1 UE.

<mark>Standalone NB-IoT Deployment</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_dlframesa.png" width=100% height=100% />
<br>


<mark>LTE In-Band NB-IoT Deployment</mark>

Assuming, LTE FDD DL having CF1 Format 3 for PDCCH, using 4 antenna port for CRS, and NB-IoT implementing 2 antenna port for NRS (In Band Different PCI Mode).

<br>
<img src="\lte_nbiot\img\lte_nbiot_dlframeinband.png" width=100% height=100% />
<br>

---

#### UL Subcarrier Spacing

1. For NB-IoT uplink, while maintaining the SC-FDMA waveform as LTE, new frequency domain concept is introduced.
2. 2 types of uplink frame structure is being introduced based on subcarrier spacing.
3. Instead of using PRB, a smaller unit called Resource Unit (RU) is being introduced.

***2 Types of Subcarrier Spacing for NB-IoT UL***

Refer [2] Picture from [3]

<br>
<img src="\lte_nbiot\img\lte_nbiot_ulscs.png" width=100% height=100% />
<br>

<br>
<img src="\lte_nbiot\img\lte_nbiot_ulscs2.png" width=100% height=100% />
<br>

<br>
<img src="\lte_nbiot\img\lte_nbiot_ulscs3.png" width=100% height=100% />
<br>

Table version for easy copy.

| Subcarrier Spacing | No of UL Subcarrier | Timeslot | No of Timeslot/Radio Frame |
|--------------------|---------------------|----------|----------------------------|
| 15 kHz             | 12                  | 0.5 ms   | 20 -> {0,1,…,19}           |
| 3.75 kHz           | 48                  | 2 ms     | 5 -> {0,1,…,4}             |


<mark>Narration form the picture:</mark>

>Subcarrier spacing in 3.75 Khz became narrower by 4 times comparing to 15 Khz resource grid
>Symbol length in 3.75 Khz resource grid became longer by 4 times comparing to 15 Khz resource  grid
>Length of a Radio Frame is defined to be same (10 ms) in both 3.75 Khz resource grid and 15 Khz resource grid
>The number of slots within a radio frame in 3.75 Khz resource grid became smaller by 4 times comparing to 15 Khz resource grid.
>The number of OFDM symbols within a slot is same (7) in both 3.75 Khz resource grid and 15 Khz.

---

#### References

1. [Rohde & Schwarz](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma266/1MA266_0e_NB_IoT.pdf)
2. 3GPP TS 36.211 Section 10.1
3. [Sharetechnote](https://www.sharetechnote.com/html/Handbook_LTE_NB_LTE.html)
