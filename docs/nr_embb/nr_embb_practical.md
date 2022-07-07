Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2022/05/09<br>
Date Edited: 2022/06/07<br>

---

#### Design Cell Range for TDD

Based on the flexible symbol, guard band can be estimated, max cell range can be determined. 

***<mark>Symbol Length (Normal CP Case)</mark>***

<br>
<img src="\nr_embb\img\nr_embb_symbollength.png" width=70% height=70% />
<br>

| Numerology  | SCS   | OFDM Symbol Duration | Cyclic Prefix Duration | OFDM Symbol including CP  |
|-------------|-------|----------------------|------------------------|---------------------------|
| (μ)         | (kHz) | (μsec)               | (μsec)                 | (μsec)                    |
| 0           | 15    | 66.67                | 4.69                   | 71.35                     |
| 1           | 30    | 33.33                | 2.34                   | 35.68                     |
| 2           | 60    | 16.67                | 1.17                   | 17.84                     |
| 3           | 120   | 8.33                 | 0.57                   | 8.92                      |
| 4           | 240   | 4.17                 | 0.29                   | 4.46                      |

***<mark>Estimating Cell Range</mark>***

    Distance (m) = c (m/sec) × t (sec)

Eg: 30kHz SCS

    Distance (m) 
    = 3x(10^8) x 35.68x(10^-6)
    = 10650 m

1 Symbol CP provides protection for:
    10.65km (2 Way Propagation)
    5.33km (1 Way Propagation)

<br>
<img src="\nr_embb\img\nr_embb_cellrange.png" width=70% height=70% />
<br>

---

#### Dimension Channels Capacity

Total of 8 topics of channel capacity planning and dimensioning uploaded in a form of simulation coding projects on github. Click [here](https://github.com/zulfadlizainal/5G-NR-Planning-And-Dimensioning). [1]

***<mark>Planning & Dimensioning Topic Includes:</mark>***

1. Part 1: Operating Band, Frame Structure
2. Part 2: Synchronization
3. Part 3: System Information
4. Part 4: DL Common Channel
5. Part 5: PDSCH
6. Part 6: Paging
7. Part 7: UL Common Channel
8. Part 8: PUSCH

---

#### References

1. [Github](https://github.com/zulfadlizainal/5G-NR-Planning-And-Dimensioning). 