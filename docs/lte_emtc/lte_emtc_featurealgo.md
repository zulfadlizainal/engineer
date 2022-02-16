Topic: 4G LTE<br>
Sub-Topic: eMTC<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/02/16<br>

---

#### Coverage Level (CE Level)

1. Coverage enhancement (CE) are introduced to adapt to the coverage depth and capacity performance requirements of eMTC UE. 
2. Dividing the coverage allowing UE/eNB to selects an appropriate coverage level based on the signal strength to provide reliable transmission in poor RF without trading off good performance in good RF. 
3. Four CE Level available in eMTC defined based on RSRP range. 
4. To achieve deep coverage, number of repetitions can be set separately for different coverage areas. 

?> Different CEL have different PHY channel repettition parameter set.

<br>
<img src="\lte_emtc\img\lte_emtc_cel.png" width=100% height=100% />
<br>

---

#### Coverage Enhancement Mode (CE Mode) 

1. Coverage enhancement (CE) are introduced to adapt to the coverage depth and capacity performance requirements of eMTC UE. 
2. Dividing the coverage allowing UE/eNB to selects an appropriate coverage level based on the signal strength to provide reliable transmission in poor RF without trading off good performance in good RF. 
3. Two CE Modes in connected mode are defined by 3GPP in regards for different motivations.  

?> Concept of CE Mode almost similar with CEL. However, this concept focus on connected mode part. UE should be able to support certain CE Mode to use this concept.

<br>
<img src="\lte_emtc\img\lte_emtc_cem.png" width=100% height=100% />
<br>

---

#### Normal and Enhance Coverage (NC, EC) 

1. In Release 13, two types of coverage mode is being defined by 3GPP: Normal Coverage and Enhanced Coverage. 
2. The motivation is to have capability to control cell selection region based on UE capability (BL/CE UE, BL/CE Mode B UE.
3. The mechanism being used is S criterion rule by utilizing Qrxlevmin and Qqualmin indicator. 

?> This concept focus on Cell Selection procedure.

***Basic Concepts*** [1] [2] [3] [4]

1. Standard S criterion is being used to evaluate UE whether being able to select to normal coverage.
2. If S criterion in Normal Coverage not fulfilled, UE should consider itself to be in Enhanced Coverage (CE) if S criterion in Enhance Coverage (CE) is fulfilled by applying  Qrxlevmin_CE and Qqualmin_CE.
3. Qrxlevmin_CE and Qqualmin_CE dedicated for BL/CE UE.
4. If S criterion in Enhance Coverage (CE) not fulfilled, UE should consider itself to be in Enhanced Coverage (CE1) if S criterion in Enhance Coverage (CE1) is fulfilled by applying Qrxlevmin_CE1 and Qqualmin_CE1 and UE supports CE Mode B. 
5. Qrxlevmin_CE1 and Qqualmin_CE1 dedicated for BL/CE UE  that supports CE Mode B.
6. For the UE in Enhanced Coverage, coverage specific values Qrxlevmin_CE and Qqualmin_CE (or Qrxlevmin_CE1 and Qqualmin_CE1) are only applied for the suitability check in Enhance Coverage (i.e. not used for measurement and reselection thresholds).
7. There is no Enhance Coverage defined for NB-IoT up to Release 13.  However, cell selection procedure for Cat NB1 at Enhance Coverage is already being defined.   

<br>
<img src="\lte_emtc\img\lte_emtc_ncec.png" width=100% height=100% />
<br>

---

#### Power Saving Mode (PSM)

Start Release 12, IoT UE (MTC Cat 0 R12, eMTC Cat M1 R13, NB-IoT Cat NB1 R13) able have a Power Saving Mode feature. 

    PSM = UE status that can minimize the UE power consumption  lower than idle mode. 
    Target PSM = Reduce power consumption as almost the UE is off and lower power consumption than idle mode. 


***References from 3GPP:*** [5]

1. Same like power off, but UE still registered to the network. 
2. After wake up no need to re-attach to the network. (Save UE power!) 
3. UE in PSM are not immediately reachable for MT due to not monitor paging. 
4. UE in PSM only available for MT after an MO activity for certain period of Active Time. 
5. Target of PSM is for UE that does not require frequent MT. 
6. Should not support UE for CS domain. 

***References from 3GPP:*** [6]

- If UE want to use PSM, UE will request Active Time (T3324) timer through Attach Request or TAU. 
- If network support PSM & accept UE to use PSM, network will allocate Active Time (T3324) timer to UE. If T3324 timer field state "deactivated" -> Network does not support PSM/Not allow UE to use PSM. 
- If T3324 timer expires, 
    1. Check if UE not in Emergency Bearer Services 
    2. Check if UE in Idle Mode 
    3. Check if UE in Normal Service 
- Then UE can enter PSM mode. 
    1. T3412 Extended Value started when UE enter PSM. But UE can leave PSM mode at any time when UE have MO event. 
    2. PSM time = T3412-T3324 
    3. If UE want to change timer, UE can send during the periodically TAU. 
    4. The maximum time a device may sleep is approximately 413 days (set by 3GPP Release 13 for T3412). The maximum time a device may be reachable is 186 minutes (an equivalent of the maximum value of the Active timer T3324).  

Picture form [7]

<br>
<img src="\lte_emtc\img\lte_emtc_psmsignal.png" width=100% height=100% />
<br>

<br>
<img src="\lte_emtc\img\lte_emtc_psm.png" width=100% height=100% />
<br>

---

#### References

1. 3GPP TS 36.304 Section 5.2.3.2 
2. 3GPP TS 36.331 Section 6.2.2 
3. 3GPP TS 36.304 Section 5.2.3.2a 
4. 3GPP TS 36.133 Section 4.6.2 
5. 3GPP TS 23.682 Section 4.5.4
6. 3GPP TS 24.301 Section 5.3.11
7. [Sharetechnote](https://www.sharetechnote.com/html/Handbook_LTE_PSM.html#:~:text=ShareTechnote&text=What%20is%20PSM%20%3F,normal%20idle%20mode%20energy%20consumption.)
