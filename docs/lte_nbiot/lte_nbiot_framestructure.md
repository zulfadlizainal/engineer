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

#### References

1. [Rohde & Schwarz](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma266/1MA266_0e_NB_IoT.pdf)
2. 