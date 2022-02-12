Topic: 4G LTE<br>
Sub-Topic: eMTC<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/02/12<br>

---

#### Coverage Level (CE Level)

1. Coverage enhancement (CE) are introduced to adapt to the coverage depth and capacity performance requirements of eMTC UE. 
2. Dividing the coverage allowing UE/eNB to selects an appropriate coverage level based on the signal strength to provide reliable transmission in poor RF without trading off good performance in good RF. 
3. Four CE Level available in eMTC defined based on RSRP range. 
4. To achieve deep coverage, number of repetitions can be set separately for different coverage areas. 

<br>
<img src="\lte_emtc\img\lte_emtc_cel.png" width=100% height=100% />
<br>

---

#### Coverage Enhancement Mode (CE Mode) 

1. Coverage enhancement (CE) are introduced to adapt to the coverage depth and capacity performance requirements of eMTC UE. 
2. Dividing the coverage allowing UE/eNB to selects an appropriate coverage level based on the signal strength to provide reliable transmission in poor RF without trading off good performance in good RF. 
3. Two CE Modes in connected mode are defined by 3GPP in regards for different motivations.  

<br>
<img src="\lte_emtc\img\lte_emtc_cem.png" width=100% height=100% />
<br>

---

#### Physical Channel Repetitions Structures

1. Other important features adapted in eMTC is physical channel repetitions. 
2. Repetition is a technique consisting on repeating the same data transmission several times to ensure its reliability. 
3. In areas with good coverage, high data rates can be reached using a few repetitions or even without repetition. In areas with poor coverage, coverage performance can be ensured by using more repetitions. 
4. These repetitions settings can be divided based on Coverage Enhancement Level (CEL) concept, meet objective to extend coverage.   

<br>
<img src="\lte_emtc\img\lte_emtc_repstruct.png" width=100% height=100% />
<br>

Parameter mapping for physical channel repititions:

| L3 Msg | Phy Channel Repetition        | L3 Parameter Name                                                                 | CE Level 0 | CE Level 1 | CE Level 2 |
|--------|-------------------------------|-----------------------------------------------------------------------------------|------------|------------|------------|
| SIB2   | ① MPDCCH for Paging           | mpdcch-NumRepetition-Paging-r13                                                   | X          | X          | X          |
| SIB2   | ② MPDCCH for RA               | mpdcch-NumRepetition-RA-r13                                                       | X          | X          | X          |
| SIB2   | ③ PUCCH (ACK/NACK for MSG4)   | pucch-NumRepetitionCE-Msg4-Level0-r13 <br/>pucch-NumRepetitionCE-Msg4-Level1-r13  | X          | X          | X          |
| SIB2   | ④ PRACH (Preamble)            | numRepetitionPerPreambleAttempt-r13                                               | X          | X          | X          |
| Setup  | ⑤ MPDCCH (DCI Format)         | mpdcch-NumRepetition-r13                                                          | X          | X          | X          |
| Setup  | ⑥ PUCCH (ACK/NACK,Format1/2)  | pucch-NumRepetitionCE-format1-r13 <br/>pucch-NumRepetitionCE-format2-r13          | X          | X          | X          |
| SIB2   | ⑦ PDSCH                       | pdsch-maxNumRepetitionCEmodeA-r13                                                 | X          | X          | X          |
| SIB2   | ⑧ PUSCH                       | pusch-maxNumRepetitionCEmodeA-r13                                                 | X          | X          | X          |
|        | ⑨ PDSCH for Paging            |                                                                                   | X          | X          | X          |

---

#### References

1. N/A