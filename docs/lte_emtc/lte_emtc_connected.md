Topic: 4G LTE<br>
Sub-Topic: eMTC<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/02/14<br>

---

#### Features to 3GPP Mapping

Up to Rel 13. [5]

!> TODO Need to update.

| Features                           | eMTC Cat-M1                   | NB-IoT Cat NB-1  |
|------------------------------------|-------------------------------|------------------|
|  Intra Frequency FDD-FDD Handover  | 3GPP TS 36.133 Sec 5.5.2.1-2  |                  |
|  Intra Frequency TDD-TDD Handover  | 3GPP TS 36.133 Sec 5.5.2.3    |                  |
|  Inter Frequency FDD-TDD Handover  |                               |                  |
|  Inter Frequency TDD-FDD Handover  |                               |                  |

#### Measurement Gap for MTC

In MTC, measurement gap is supported starting on Release 14 (FeMTC). Measurement Gap is to support measurement of other carrier before start doing handover. 

<mark>In MTC, measurement gap is needed even for Intra Frequency handover. Here is why: BL/CE UE operating frequency is different with cell operating frequency even both source and target cell having same EARFCN.</mark> [1]

***Measurement Gap Scenarios*** 

Refer [1]

<br>
<img src="\lte_emtc\img\lte_emtc_mgap.png" width=100% height=100% />
<br>

1. Same carrier frequency and cell bandwidths (Scenario A): an intra-frequency scenario; not measurement gap assisted.  
2. Same carrier frequency, bandwidth of the target cell smaller than the bandwidth of the current cell (Scenario B): an intra-frequency scenario; not measurement gap assisted.  
3. Same carrier frequency, bandwidth of the target cell larger than the bandwidth of the current cell (Scenario C): an intra-frequency scenario; not measurement gap assisted.  
4. Different carrier frequencies, bandwidth of the target cell smaller than the bandwidth of the current cell and bandwidth of the target cell within bandwidth of the current cell (Scenario D): an inter-frequency scenario; measurement gap-assisted scenario.  
5. Different carrier frequencies, bandwidth of the target cell larger than the bandwidth of the current cell and bandwidth of the current cell within bandwidth of the target cell (Scenario E): an inter-frequency scenario; measurement gap-assisted scenario.  
6. Different carrier frequencies and non-overlapping bandwidth, (Scenario F): an inter-frequency scenario; measurement gap-assisted scenario.  
7. Same carrier frequency, the operating frequency of the bandwidth reduced low complexity (BL) UE or the UE in Enhanced Coverage is not guaranteed to be aligned with the centre frequency of the current cell (Scenario G): an intra-frequency scenario; measurement gap assisted scenario.  

***How Measurement Gap is Triggered/Release***

1. Measurement Gap is Triggered: When eNodeB send Gap Config IE in RRCConnectionReconfiguration. 
2. Measurement Gap is Released: When eNodeB send Gap Release IE in RRCConnectionReconfiguration. 
3. ENodeB know UE need to do measurement gap when UE send Event A2 to eNodeB. 

<mark>Why UE cannot directly do measurement gap when event A2 threshold is triggered?</mark>

Because, UE in connected mode must be controlled by eNodeB. ENodeB need to know when is the time to schedule UE in DL and UL, hence ENodeB will coordinate when a UE should do measurement gap. 

***Measurement Gap Parameters***

MGAP Pattern ID:  [2] [3] [4]

    Gp0: Every 40ms (MGL), Gap for 6ms (MGRP), start based on Gap Offset 
    Gp1: Every 80ms (MGL), Gap for 6ms (MGRP), start based on Gap Offset 
    Gp2: Every 40ms (MGL), Gap for 3ms (MGRP), start based on Gap Offset 
    Gp3: Every 80ms (MGL), Gap for 3ms (MGRP), start based on Gap Offset 

---

#### References

1. 3GPP TS 36.300 Section 10.1.3
2. 3GPP TS 36.133 Section 8.1.2
3. [Sharetechnote](http://www.sharetechnote.com/html/Handbook_LTE_MultiCell_Measurement_LTE.html#Measurement_GAP)
4. [Sqimway](https://www.sqimway.com/lte_meas_gaps.php) -> Good visualization
5. 3GPP TS 36.133 Section 5