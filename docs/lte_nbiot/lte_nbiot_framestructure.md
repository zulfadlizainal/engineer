Topic: 4G LTE<br>
Sub-Topic: NB-IoT<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/03/18<br>

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

#### References

1. 
2. 