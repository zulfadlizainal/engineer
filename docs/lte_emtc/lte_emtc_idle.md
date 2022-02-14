Topic: 4G LTE<br>
Sub-Topic: eMTC<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/02/14<br>

---

#### Features to 3GPP Mapping

Up to Rel 13. #TODO Need to update.

| Features                               | eMTC Cat-M1                     | NB-IoT Cat NB-1                 |
|----------------------------------------|---------------------------------|---------------------------------|
| Intra Frequency Cell Reselection       | 3GPP TS 36.133 Sec 4.7.2.1.1-2  | 3GPP TS 36.133 Sec 4.6.2.1.1-2  |
| Inter Frequency Cell Reselection       | 3GPP TS 36.133 Sec 4.7.2.1.3    | 3GPP TS 36.133 Sec 4.6.2.1.5    |
| RSRP-based Measurement and Evaluation  | 3GPP TS 36.133 Sec 4.7.2.1.1-3  | 3GPP TS 36.133 Sec 4.6.2.1.1-5  |
| RSRQ-based Measurement and Evaluation  | 3GPP TS 36.133 Sec 4.7.2.1.1-3  |                                 |
| Cell Reselection Priority              | 3GPP TS 36.133 Sec 4.7.2.1.1-3  |                                 |

#### Important Parameter Addition

Important addition of eMTC parameter up to Rel 13.

***SIB 1 BR***
    
    q-RxLevMinCE-r13 
    q-QualMinRSRQ-CE-r13 

***SIB 3***
    
    q-RxLevMinCE-r13 
    q-QualMinRSRQ-CE-r13 
    t-ReselectionEUTRA-CE-r13 

***SIB 5***
    
    q-RxLevMinCE-r13 
    q-QualMinRSRQ-CE-r13 
    t-ReselectionEUTRA-CE-r13 


***Full Table List of Idle Mode Parameter + Rel 13***

| Technology  | eMTC                       |
|-------------|----------------------------|
| SIB1        | q-RxLevMin                 |
| SIB1        | q-QualMin-r9               |
| SIB1        | q-RxLevMinCE-r13           |
| SIB1        | q-QualMinRSRQ-CE-r13       |
| SIB3        | q-RxLevMin                 |
| SIB3        | q-QualMin-r9               |
| SIB3        | q-RxLevMinCE-r13           |
| SIB3        | q-QualMinRSRQ-CE-r13       |
| SIB3        | q-Hyst                     |
| SIB3        | t-ReselectionEUTRA         |
| SIB3        | t-ReselectionEUTRA-CE-r13  |
| SIB3        | s-IntraSearchP-r9          |
| SIB3        | s-IntraSearchQ-r9          |
| SIB3        | s-NonIntraSearch           |
| SIB3        | s-NonIntraSearchP-r9       |
| SIB3        | s-NonIntraSearchQ-r9       |
| SIB3        | threshServingLow           |
| SIB3        | threshServingLowQ-r9       |
| SIB3        | cellReselectionPriority    |
| SIB5        | q-RxLevMin                 |
| SIB5        | q-QualMin-r9               |
| SIB5        | q-RxLevMinCE-r13           |
| SIB5        | q-QualMinRSRQ-CE-r13       |
| SIB5        | q-OffsetFreq               |
| SIB5        | t-ReselectionEUTRA         |
| SIB5        | t-ReselectionEUTRA-CE-r13  |
| SIB5        | threshX-High               |
| SIB5        | threshX-Low                |
| SIB5        | cellReselectionPriority    |

---

#### References

1. 3GPP