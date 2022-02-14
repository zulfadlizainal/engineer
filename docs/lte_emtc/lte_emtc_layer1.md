Topic: 4G LTE<br>
Sub-Topic: eMTC<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/02/14<br>

---

#### Physical Channel Mapping

Refer [1] [2]

1. Overall physical channel structure is not changed for uplink. 
2. Cat M1 UE unable to decode LTE PDCCH as it is spread across the entire PRB. Cat M1 UE only able to decode 6PRB. 
3. New design for downlink control channel is being introduced: MPDCCH which adapting ECCE aggregation from EPDCCH concept. 
4. New preserved field in MIB and SIB 1 BR is being adapted to provide information to Cat M1 UE.   

<br>
<img src="\lte_emtc\img\lte_emtc_dlchmap.png" width=100% height=100% />
<br>

<br>
<img src="\lte_emtc\img\lte_emtc_ulchmap.png" width=100% height=100% />
<br>

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

#### MPDCCH

1. MPDCCH stands for MTC physical downlink control channel. 
2. It is a special type of PDCCH designed for eMTC operation. 
3. MPDCCH using a very similar concept as EPDCCH in LTE. 

***Basic Concept*** [3]

1. MPDCCH using same concept as EPDCCH in LTE.
2. MPDCCH are formed by the aggregation of ECCEs. 
3. MPDCCH can be transmitted single time or transmitted with the repetition (the number of repetition is configured by RRC).
4. BL/CE UE unable to read LTE normal PDCCH, hence MPDCCH is specified just for eMTC.
5. Since BL/CE UE unable to read LTE PDCCCH, SIB scheduling is designed based on a predefined table and indicator is informed in MIB.
6. Common UE should not monitor MPDCCH.
7. MPDCCH can be transmitted in different set of NB Index if frequency hopping is enabled. Otherwise, it is always transmitted in the same narrowband index. 
8. MPDCCH support both same subframe scheduling and cross subframe scheduling.

***MPDCCH Format*** [4]

| DCI Format   | Purpose                                 |
|--------------|-----------------------------------------|
| Format 6-0A  | UL Grant                                |
| Format 6-0B  | UL Grant                                |
| Format 6-1A  | DL Scheduling                           |
|              | RA by PDCCH Order                       |
| Format 6-1B  | DL Scheduling                           |
| Format 6-2   | Paging and Direct Indication Scheduling |

***Enhanced Control Channel Element (ECCE)*** [5]

1. Type of resource allocation for control channel. 
2. Developed for EPDCCH 
3. Starting Rel 11, CCE unable to accommodate with maximum PCFICH  is 3 symbol per subframe 
4. Hence, ECCE is formed using available REs for PDSCH 

<br>
<img src="\lte_emtc\img\lte_emtc_ecce.png" width=100% height=100% />
<br>

***How M1 UE know size of MPDCCH*** [6] [7]

1. MPDCCH in eMTC using the same concept as ECCE where the MPDCCH is formed using the PDSCH RE. 
2. Since there is no PCFICH in eMTC, Cat M1 UE need an indication to know the size of MPDCCH for the UE to monitor. 
3. What is the mechanism used by Cat M1 UE to decode MPDCCH?  
4. How the UE know the size and location of MPDCCH?  
    - MPDCCH can be 2, 4, or 6 PRB. 
    - For Common Search Space (CSS) in MPDCCH, no indication for the UE on which PRB to search for MPDCCH. 
    - For UE Specific Search Space (USS) in MPDCCH, PRB pairs information is provided in Higher Layers (RRC Conn Setup) - 2 PRB, or 4PRB, or 2+4PRB 

---

#### Channel to RB Mapping

Picture from [8]

<br>
<img src="\lte_emtc\img\lte_emtc_chrbmap.png" width=100% height=100% />
<br>

---

#### Narrowband Index

Refer [9]

1. Narrowband index is a division of 6 PRB sets (1.4Mhz each) from a wider LTE bandwidth. 
2. The reason of having Narrowband Index to schedule specific sets of consecutive PRBs that can be use by eMTC Cat M1 UE.  
3. This is due to eMTC Cat M1 UE can only operate with 1.4MHz bandwidth. 

<br>
<img src="\lte_emtc\img\lte_emtc_nbi.png" width=100% height=100% />
<br>

Table for easy copy:

| Bandwidth                                    | 1.4  | 3   | 5   | 10  | 15  | 20   |
|----------------------------------------------|------|-----|-----|-----|-----|------|
| Number of Sys PRB (NRB)                      | 6    | 15  | 25  | 50  | 75  | 100  |
| Number of Narrowband Sets (NNB)              | 1    | 2   | 4   | 8   | 12  | 16   |
| Initial PRB (i0)                             | 0    | 1   | 0   | 1   | 1   | 2    |
| Spacing between Narrowband Sets (NRB mod 2)  | 0    | 1   | 1   | 0   | 1   | 0    |

<br>
<img src="\lte_emtc\img\lte_emtc_nbi2.png" width=100% height=100% />
<br>

---

#### No HARQ for UL PUSCH

Refer [10] [11]

1. In eMTC UL, eNB does not send HARQ ACK/NACK for PUSCH. 
2. Why? Because there is no PHICH in eMTC. 

***If no PUSCH ACK/NACK, how can eNB handle reception fail?***

1. Simply, UE will send PUSCH in all allocated repetition subframe until the end even eNB success to decode.
2. eNB will judge whether to adjust PUSCH repetition on the next allocation. (If vendor support dynamic allocations).
3. If all fail, eNB will schedule retransmit (Using same NDI). 

***Key point:***

1. No ACK/NACK transmission for PUSCH in eMTC.
2. Retransmission of PUSCH is supported in PUSCH eMTC. 

<br>
<img src="\lte_emtc\img\lte_emtc_ulharq.png" width=100% height=100% />
<br>

---

#### References

1. 3GPP TS 36.331 Section 6.2
2. 3GPP TS 36.211 Section 6.8B
3. 3GPP TS 36.300 Section 5.1.3
4. 3GPP TS 36.212 Section 5.3.3
5. [Rohde & Schwarz](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma266/1MA266_0e_NB_IoT.pdf)
6. 3GPP TS 36.213 Section 9.1.5 
7. 3GPP TS 36.213 Section 9.1.4.4
8. [Docomo](https://www.nttdocomo.co.jp/english/binary/pdf/corporate/technology/rd/technical_journal/bn/vol18_2/vol18_2_008en.pdf)
9. 3GPP TS 36.211 Section 5.2.4 
10. 3GPP TS 36.321 Section 5.4.2.1, 5.4.2.2, 7.7 
11. [Sharetechnote](https://www.sharetechnote.com/html/Handbook_LTE_BL_CE_HARQ.html)