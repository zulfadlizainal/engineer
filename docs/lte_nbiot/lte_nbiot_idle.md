Topic: 4G LTE<br>
Sub-Topic: NB-IoT<br>
Date Written: 2019/05/21<br>
Date Edited: 2022/03/22<br>

---

#### Cell Reselection Concept

In release 13, <mark>NB-IoT does not have any cell reselection priority concept.</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_cellresel.png" width=100% height=100% />
<br>

Table version for easy copy:

| L3 Msg                  | eMTC                      | NB-IoT               |
|-------------------------|---------------------------|----------------------|
| SIB1                    | q-RxLevMin                | q-RxLevMin-r13       |
|                         | q-QualMin-r9              | q-QualMin-r13        |
|                         | q-RxLevMinCE-r13          |                      |
|                         | q-QualMinRSRQ-CE-r13      |                      |
| SIB3                    | q-RxLevMin                | q-RxLevMin-r13       |
|                         | q-QualMin-r9              | q-QualMin-r13        |
|                         | q-RxLevMinCE-r13          |                      |
|                         | q-QualMinRSRQ-CE-r13      |                      |
|                         | q-Hyst                    | q-Hyst-r13           |
|                         | t-ReselectionEUTRA        | t-Reselection-r13    |
|                         | t-ReselectionEUTRA-CE-r13 |                      |
|                         | s-IntraSearchP-r9         | s-IntraSearchP-r13   |
|                         | s-IntraSearchQ-r9         |                      |
|                         | s-NonIntraSearch          | s-NonIntraSearch-r13 |
|                         | s-NonIntraSearchP-r9      |                      |
|                         | s-NonIntraSearchQ-r9      |                      |
|                         | threshServingLow          |                      |
|                         | threshServingLowQ-r9      |                      |
|                         | cellReselectionPriority   |                      |
| SIB5 (Band A to Band B) | q-RxLevMin                | q-RxLevMin-r13       |
|                         | q-QualMin-r9              | q-QualMin-r13        |
|                         | q-RxLevMinCE-r13          |                      |
|                         | q-QualMinRSRQ-CE-r13      |                      |
|                         | q-OffsetFreq              | q-OffsetFreq-r13     |
|                         | t-ReselectionEUTRA        | t-Reselection-r13    |
|                         | t-ReselectionEUTRA-CE-r13 |                      |
|                         | threshX-High              |                      |
|                         | threshX-Low               |                      |
|                         | cellReselectionPriority   |                      |


---

#### References

1. 