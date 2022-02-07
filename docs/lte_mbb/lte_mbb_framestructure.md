Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2019/06/14<br>
Date Edited: 2022/02/07<br>

---

#### Basic Time Unit (Ts)

First, an introduction to some of the terms used in describing an LTE Frame. There are six time units: [1]

1. Frame
2. Half-frame
3. Subframe
4. Slot
5. Symbol
6. The basic time unit (Ts)

| Time Unit   | Value                          |
|-------------|--------------------------------|
| Frame       | 10 ms                          |
| Half-frame  | 5 ms                           |
| Subframe    | 1 ms                           |
| Slot        | 0.5 ms                         |
| Symbol      | (0.5 ms) / 7 for normal CP     |
|             | (0.5 ms) / 6 for extended CP   |
| Ts          | 1/(15000 * 2048) sec » 32.6 ns |

So,

    1ms = 30720 Ts 

#### FDD Frame (Type 1)

Key points for FDD frame structure: [1]

1. Uplink and downlink frames are both 10ms.
2. For full-duplex FDD, uplink and downlink frames are separated by frequency and are transmitted continuously and synchronously.
3. For half-duplex FDD, the only difference is that a UE cannot receive while transmitting.

<img src="\lte_mbb\img\lte_mbb_fddframe.png" width=100% height=100% />
<br />

#### TDD Frame (Type 2)

Key points for TDD frame structure: [1]

1. Uplink and downlink subframes are transmitted on the same frequency and are multiplexed in the time domain.
2. The locations of the uplink, downlink, and special subframes are determined by the uplink-downlink configuration.
3. There are seven possible configurations given in the standard.

<img src="\lte_mbb\img\lte_mbb_tddframe.png" width=100% height=100% />
<br />

TDD Subframe Config: [2]

<img src="\lte_mbb\img\lte_mbb_tddsubconfig.png" width=100% height=100% />
<br />

TDD Special Subframe Config: [2]

<img src="\lte_mbb\img\lte_mbb_tddspsconfig.png" width=100% height=100% />
<br />

#### Uplink Frame

Key points for UL frame structure: [1]

1. Uplink user transmissions consist of uplink user data (PUSCH), random-access requests (PRACH), user control channels (PUCCH), and sounding reference signals (SRS).
2. FDD and TDD uplink transmissions have the same physical channels and signals. 
3. The only difference is that TDD frames include a special subframe, part of which can be used for SRS and PRACH uplink transmissions.

<img src="\lte_mbb\img\lte_mbb_ulframe.png" width=100% height=100% />
<br />

#### References

1. [Keysight](https://rfmw.em.keysight.com/wireless/helpfiles/89600b/webhelp/subsystems/lte/content/lte_overview.htm)
2. [Sqimway](https://www.sqimway.com/lte_tdd.php) -> Good website to visualize LTE Frame