Topic: 4G LTE<br>
Sub-Topic: NB-IoT<br>
Date Written: 2019/10/16<br>
Date Edited: 2022/03/22<br>

---

#### Calculate DL N-SF from DCI

Conversion table form <mark>ISF to N-SF</mark> refer [1]

<br>
<img src="\lte_nbiot\img\lte_nbiot_nsf.png" width=100% height=100% />
<br>

Based on this, <mark>N-SF utilization</mark> can be calculated. [5]

---

#### Calculate UL N-RU from DCI

Conversion table form <mark>IRU to N-RU</mark> refer [2]

Conversion table form <mark>ISC to Number of UL Slots</mark> refer [3]

<br>
<img src="\lte_nbiot\img\lte_nbiot_nru.png" width=100% height=100% />
<br>

Based on this, <mark>N-RU utilization</mark> can be calculated. [6]

---

#### Calculate NPDCCH Utilization

NPDCCH repetitions is limited based on <mark>Rmax</mark> value. From Rmax, actual NPDCCH repetition can be converted.

<br>
<img src="\lte_nbiot\img\lte_nbiot_npdcchutil.png" width=100% height=100% />
<br>

<br>
<img src="\lte_nbiot\img\lte_nbiot_npdcchutil2.png" width=100% height=100% />
<br>

---

#### Check eDRX Settings 

***PTW Settings Index:*** [4]

<mark>For M1</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_ptwm1.png" width=70% height=70% />
<br>

<mark>For NB1</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_ptwnb1.png" width=70% height=70% />
<br>

***eDRX Cycle:*** [4]

<br>
<img src="\lte_nbiot\img\lte_nbiot_edrxcycle.png" width=70% height=70% />
<br>

***Check eDRX settings from <mark>'Attach Request'</mark> message:***

<br>
<img src="\lte_nbiot\img\lte_nbiot_attach.png" width=70% height=70% />
<br>

<mark>eDRX Turn On:</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_edrxturnon.png" width=100% height=100% />
<br>

<mark>eDRX Turn Off:</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_edrxturnoff.png" width=100% height=100% />
<br>

***UE Wake Up in each eDRX Cycles***

<br>
<img src="\lte_nbiot\img\lte_nbiot_edrxcycle2.png" width=100% height=100% />
<br>

---

#### References

1. 3GPP TS 36.213 Section 16.4.1.3
2. 3GPP TS 36.213 Section 16.5.1.1
3. 3GPP TS 36.211 Section 10.1.2.3
4. 3GPP TS 24.008
5. [Github](https://github.com/zulfadlizainal/4G-NB-IoT-Resource-Utilization/tree/master/DL%20NSF%20Resource%20Utilization)
6. [Github](https://github.com/zulfadlizainal/4G-NB-IoT-Resource-Utilization/tree/master/UL%20NRU%20Resource%20Utilization)
