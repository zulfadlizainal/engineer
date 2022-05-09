Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2022/05/09<br>
Date Edited: 2022/05/09<br>

---

#### Design Cell Range for TDD

Based on the flexible symbol, guard band can be estimated, max cell range can be determined. 

***<mark>Symbol Length (Normal CP Case)</mark>***

<br>
<img src="\nr_embb\img\nr_embb_symbollength.png.png" width=100% height=100% />
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
Distance (m) = 3x(10^8) x 35.68x(10^-6)
             = 10650 m

> 1 Symbol CP provides protection for:
> 10.65km (2 Way Propagation)
> 5.33km (1 Way Propagation)

<br>
<img src="\nr_embb\img\nr_embb_cellrange.png.png" width=100% height=100% />
<br>

---

#### References

1. 