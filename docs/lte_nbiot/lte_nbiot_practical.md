Topic: 4G LTE<br>
Sub-Topic: NB-IoT<br>
Date Written: 2019/10/16<br>
Date Edited: 2022/03/23<br>

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

#### Design NPRACH Resource

To plan the NPRACH Resource, <mark>need to ensure that NPRACH resource not overlapped within CE Level.</mark> What it means is, every CE level have their own dedicated NPRACH resource with their own NPRACH repetition and periodicity settings. 

<br>
<img src="\lte_nbiot\img\lte_nbiot_nprachperiodicity.png" width=100% height=100% />
<br>

!> Note: UL NPRACH does not follow the the same time slot rules as NPUSCH. It uses different timing unit based on preamble transmission structure.

?> Timing reference is given using 2ms slot format because of UL NPRACH uses 3.75kHz SCS (devide 4 from 15kHz SCS in LTE). So, UL slots become 2ms (multiply 4 from 0.5ms timeslot in LTE).

***Sample Parameter Structure:*** <mark>Parameter is not shared between differnt CE Level</mark>

<br>
<img src="\lte_nbiot\img\lte_nbiot_nprachparam.png" width=70% height=70% />
<br>

---

#### Calculate Paging Capacity

Paging capacity can be calculated based on SIB2 parameters and also the capability of vendor to support as many TMSI possible per paging message.

> If paging cycle is shorter, paging capacity is higher but more resources is utilized for paging.

> If paging ocassion is higher, paging capacity is higher but more resources is utilized for paging.

> If more TMSI can be included in 1 paging message, more UE can be paged hence improve the capacity of paging.

<br>
<img src="\lte_nbiot\img\lte_nbiot_pagingcapacity.png" width=100% height=100% />
<br>

Table for easy copy:

| Parameter        | Description                                                                    | Param Set 1 | Param Set 2 | Param Set 3 |
|------------------|--------------------------------------------------------------------------------|-------------|-------------|-------------|
| Paging Cycle (T) | Received from SIB2. Also called as DRX Cycle.                                  | 256rf       | 256rf       | 256rf       |
| nB               | Received from SIB2.                                                            | one64thT    | one128thT   | one256thT   |
| Paging Record    | Vendor support capability. Number of TMSI can be included per paging occasion. | 1           | 10          | 15          |
| Paging Capacity  | For every cycle, how many TMSI can be paged?                                   | 4           | 20          | 15          |

---

#### References

1. 3GPP TS 36.213 Section 16.4.1.3
2. 3GPP TS 36.213 Section 16.5.1.1
3. 3GPP TS 36.211 Section 10.1.2.3
4. 3GPP TS 24.008
5. [Github](https://github.com/zulfadlizainal/4G-NB-IoT-Resource-Utilization/tree/master/DL%20NSF%20Resource%20Utilization)
6. [Github](https://github.com/zulfadlizainal/4G-NB-IoT-Resource-Utilization/tree/master/UL%20NRU%20Resource%20Utilization)
