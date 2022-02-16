Topic: 4G LTE<br>
Sub-Topic: eMTC<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/02/16<br>

---

#### DL Frame Structure

1. eMTC using same OFDMA frame structure as LTE as it is implemented within LTE system. 
2. However, not all RE can be used for eMTC resources as some RE is dedicated for common UE. 
3. eMTC Cat M1 UE can only be operated in 6 consecutive PRBs, cannot read LTE control region as it is spread across the PRB. 
4. LTE control channel region defined by CFI and LTE CRS/DMSRS/SRS cannot be read by Cat M1-1 UE. 

<br>
<img src="\lte_emtc\img\lte_emtc_dlframe.png" width=70% height=70% />
<br>

---

#### UL Frame Structure

<br>
<img src="\lte_emtc\img\lte_emtc_ulframe.png" width=70% height=70% />
<br>

---

#### eMTC vs NB-IoT Frame Structure 

1. Both eMTC and NB-IoT using the same frame structure as LTE. 
2. NB-IoT uplink introducing a new concept of single tone transmission. 
3. NB-IoT uplink introducing a new unit for resource called RU (Resource Unit).  


<br>
<img src="\lte_emtc\img\lte_emtc_emtcnbframe.png" width=70% height=70% />
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
<img src="\lte_emtc\img\lte_emtc_lteframe.png" width=100% height=100% />
<br>

---

#### References

1. N/A