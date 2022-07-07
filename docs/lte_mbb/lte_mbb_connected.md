Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2020/01/26<br>
Date Edited: 2022/07/07<br>

---

#### Measurement Events

UE will report below measurement events whenever any criteria of connected mode is met. [1] [2] 

| Event Type  | Description                                                                                                                         |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Event A1    | Serving becomes better than threshold                                                                                               |
| Event A2    | Serving becomes worse than threshold                                                                                                |
| Event A3    | Neighbour becomes offset better than serving                                                                                        |
| Event A4    | Neighbour becomes better than threshold                                                                                             |
| Event A5    | Serving becomes worse than threshold1 and neighbour becomes better than threshold2                                                  |
| Event A6    | Neighbour become offset better than S Cell (This event is introduced in Release 10 for CA)                                          |
| Event B1    | Inter RAT neighbour becomes better than threshold                                                                                   |
| Event B1-NR | NR neighbour becomes better than threshold                                                                                          |
| Event B2    | Serving becomes worse than threshold1 and inter RAT neighbour becomes better than threshold2                                        |
| Event B2-NR | Serving becomes worse than threshold1 and NR neighbour becomes better than threshold2                                               |
| Event C1    | CSI-RS resource becomes better than threshold                                                                                       |
| Event C2    | CSI-RS resource becomes offset better than reference CSI-RS resource                                                                |
| Event W1    | WLAN becomes better than a threshold                                                                                                |
| Event W2    | All WLAN inside WLAN mobility set becomes worse than threshold1 and a WLAN outside WLAN mobility set becomes better than threshold2 |
| Event W3    | All WLAN inside WLAN mobility set becomes worse than a threshold                                                                    |
| Event V1    | The channel busy ratio is above a threshold                                                                                         |
| Event V2    | The channel busy ratio is below a threshold                                                                                         |
| Event H1    | The Aerial UE height is above a threshold                                                                                           |
| Event H2    | The Aerial UE height  is below a threshold                                                                                          |


<mark>This is a good website to explain this in animation -> [Sqimway](https://www.sqimway.com/lte_event.php).</mark> [3]

---

#### Blind Based CA

The process off blind based CA observed in major vendor:

***<mark>Scell Add Procedure Using Blind Addition:</mark>***

<br>
<img src="\nr_embb\img\lte_mbb_scelladd.png" width=100% height=100% />
<br>

***<mark>Scell Add Fail Procedure When Scell Poor CQI:</mark>***

<br>
<img src="\nr_embb\img\lte_mbb_scelladdfail.png" width=100% height=100% />
<br>

***<mark>Scell Release Procedure When Scell Poor CQI</mark>***

<br>
<img src="\nr_embb\img\lte_mbb_scellrel.png" width=100% height=100% />
<br>

---

#### References

1. [Sharetechnote](https://www.sharetechnote.com/html/Handbook_LTE_MultiCell_Measurement_LTE.html)
2. 3GPP TS 36.331 5.5.4
3. [Sqimway](https://www.sqimway.com/lte_event.php) -> Cool animation