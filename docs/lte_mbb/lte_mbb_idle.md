Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2020/01/26<br>
Date Edited: 2022/02/11<br>

---

#### Inter Frequency Cell Reselection

In LTE, reselection to other inter frequency band is handled using priority band mechanism. Below are simplified formula for easy understanding. [1]

<br>
<img src="\lte_mbb\img\lte_mbb_idleformula.png" width=100% height=100% />
<br>

Table format for easy copy:

| Priority    | Measure                                              | Decision                                                                                                |
|-------------|------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Equal       | RP (Serv) < SIB1_q-RxLevMin + SIB3_s-NonIntraSearchP | RP (Nbr) - SIB5_q-OffsetFreq > RP(Serv) + SIB3_q-Hyst                                                   |
| Low to High | Always Measure                                       | RP (Nbr) > SIB5_q-RxLevMin + SIB5_threshX-HighP                                                         |
| High to Low | RP (Serv) < SIB1_q-RxLevMin + SIB3_s-NonIntraSearchP | RP (Serv) < SIB1_q-RxLevMin + SIB3_threshServingLowP<br/>RP (Nbr) > SIB5_q-RxLevMin + SIB5_threshX-LowP |

Key note:

?>Priority: Each band can set own cell priority and the priority to other band.

?>Measure: Serving band start to measure the other band.

?>Decision: UE start to move (reselect) from serving band to other band.

The parameter from the formula can be extracted form network parameters (3GPP ASN SIB1, SIB3, and SIB5). Below are conversion method as defined in the specs. [1]

| Parameter                    | Band A | Band B | Formula | 3GPP IE Range                                                                                                                                                                            |
|------------------------------|--------|--------|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SIB1_q-RxLevMin              | -130   | -130   | IE x 2  | -60..-13                                                                                                                                                                                 |
| SIB1_q-QualMin               | -22    | -22    | IE      | -34..-3                                                                                                                                                                                  |
| SIB3_q-RxLevMin              | -124   | -124   | IE x 2  | -60..-13                                                                                                                                                                                 |
| SIB3_q-QualMin               | -22    | -22    | IE      | -34..-3                                                                                                                                                                                  |
| SIB3_q-Hyst                  | 2      | 2      | IE      | dB0, dB1, dB2, dB3, dB4, dB5, dB6, dB8, dB10, dB12, dB14, dB16, dB18, dB20, dB22, dB24                                                                                                   |
| SIB3_t-ReselectionEUTRA      | 1      | 1      | IE      | 0..7                                                                                                                                                                                     |
| SIB3_s-IntraSearchP          | 54     | 54     | IE x 2  | 0..31                                                                                                                                                                                    |
| SIB3_s-IntraSearchQ          | 13     | 13     | IE      | 0..31                                                                                                                                                                                    |
| SIB3_s-NonIntraSearchP       | 30     | 50     | IE x 2  | 0..31                                                                                                                                                                                    |
| SIB3_s-NonIntraSearchQ       | 10     | 12     | IE      | 0..31                                                                                                                                                                                    |
| SIB3_threshServingLowP       | 10     | 10     | IE x 2  | 0..31                                                                                                                                                                                    |
| SIB3_threshServingLowQ       |        |        | IE      | 0..31                                                                                                                                                                                    |
| SIB3_cellReselectionPriority | 5      | 5      | IE      | 0..7                                                                                                                                                                                     |
| SIB5_q-RxLevMin              | -124   | -124   | IE x 2  | -60..-13                                                                                                                                                                                 |
| SIB5_q-QualMin               | -22    | -22    | IE      | -34..-3                                                                                                                                                                                  |
| SIB5_q-OffsetFreq            | 0      | 0      | IE      | dB-24, dB-22, dB-20, dB-18, dB-16, dB-14, dB-12, dB-10, dB-8, dB-6, dB-5, dB-4, dB-3, dB-2, dB-1, dB0, dB1, dB2, dB3, dB4, dB5, dB6, dB8, dB10, dB12, dB14, dB16, dB18, dB20, dB22, dB24 |
| SIB5_t-ReselectionEUTRA      | 1      | 1      | IE      | 0..7                                                                                                                                                                                     |
| SIB5_threshX-HighP           | 14     | 14     | IE x 2  | 0..31                                                                                                                                                                                    |
| SIB5_threshX-HighQ           |        |        | IE      | 0..31                                                                                                                                                                                    |
| SIB5_threshX-LowP            | 6      | 6      | IE x 2  | 0..31                                                                                                                                                                                    |
| SIB5_threshX-LowQ            |        |        | IE      | 0..31                                                                                                                                                                                    |
| SIB5_cellReselectionPriority | 4      | 5      | IE      | 0..7                                                                                                                                                                                     |


Reference from 3GPP, 36.304. Starts from chapter 5. [1]

<br>
<img src="\lte_mbb\img\lte_mbb_idle3gpp.png" width=100% height=100% />
<br>

Simulation already being made to estimate load balance using idle mode parameters in this [repository](https://github.com/zulfadlizainal/4G-LTE-Idle-Mode-Load-Balance/tree/master/Inter%20Frequency%20-%20Reselection). This simulation requires drive test data for multiple band in same location.

---

#### References

1. 3GPP TS 36.304