Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2019/02/28<br>
Date Edited: 2022/02/11<br>

---

#### Differentiate PRB & TTI Utilization

All of this metric is calculated based on stardard deployed in most drive test analysis tools. [1]

***PRB Avg No***

    PRB Allocation Average over a period of time being allocated with TTI. 

***TTI Utilization (RB Share)***

    How many TTI is allocated with PRB across all time 
    Or
    PRB Include 0 / PRB Avg No 

***PRB Avg Including 0***

    PRB Avg No * TTI Allocation% 

***Calculation Sample:***

<br>
<img src="\lte_mbb\img\lte_mbb_prbtti.png" width=100% height=100% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_prbtti2.png" width=100% height=100% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_prbtti3.png" width=100% height=100% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_prbtti4.png" width=100% height=100% />
<br>

---

#### Differentiate TX, Layer, Spatial Rank, and Codewords

Layer mapping not related to transmission mode. Transmission mode 2 can have 2 or 4 layer, but all layer is transmitting same data (Transmit Diversity). [2]

<br>
<img src="\lte_mbb\img\lte_mbb_txlayer.png" width=100% height=100% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_txlayer2.png" width=100% height=100% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_txlayer3.png" width=100% height=100% />
<br>

---

#### Reading Antenna Pattern

Below are method of reading antenna pattern based on usual antenna pattern data provided by most antenna manufacturer. Tools to visualize antenna pattern already been made in this [repository](https://github.com/zulfadlizainal/RF-Antenna-Pattern).

<br>
<img src="\lte_mbb\img\lte_mbb_antpat.png" width=100% height=100% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_antpat2.png" width=100% height=100% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_antpat3.png" width=100% height=100% />
<br>

---

#### Simulate Coverage for Train Lines

The purpose of this simulation is to calculate the coverage of LTE at train lines based on path loss model.

<br>
<img src="\lte_mbb\img\lte_mbb_covtrain.png" width=100% height=100% />
<br>

***GPS Plotting***

1. Identify train lines. 
2. Cut train lines based on straight line. 

    How to cut: Cut based on straight line, because we use trigonometry to calculate distance. 

<br>
<img src="\lte_mbb\img\lte_mbb_covtrain2.png" width=100% height=100% />
<br>

3. Create GPS sample between cut lines (Eg: From B to C) 

How many accuracy of the samples: Based on the frequency of test samples - because we would like to match test samples with location point. If test samples is every 100ms, GPS point could be every 100ms. 

Example:

    If (Assumptions) 
    Speed of train = 70km/h, 
    And the travel distance is 226m between B and C, 
    And our test sample = 100ms / sample,
    Our ideal GPS sample to be created between point B to C is for every 1.9m 

Why? 

    Train travel in 70km in 1hour 
    Train travel in 70km in 3600s 
    Train travel in 70000m in 3600s 
    Train travel in 19.4m in 1s 
    Train travel in 1.94m in 100ms 

If we created GPS sample for every 1.9m between point B and C, how many point can we create? 

    Total Created Sample = 226m / 1.9m = ~118 Samples 

<br>
<img src="\lte_mbb\img\lte_mbb_covtrain3.png" width=100% height=100% />
<br>

***Calculate Distance, HLoss, VLoss***

The basic mainframe for this step is to calculate Distance, Hloss, and Vloss for every GPS point! 

| Point                 | Lon  | Lat  | Distance  | HLoss  | Vloss  |
|-----------------------|------|------|-----------|--------|--------|
| B                     | XXX  | XXX  |           |        |        |
| Created  GPS Point 1  | XXX  | XXX  |           |        |        |
| Created GPS Point 2   | XXX  | XXX  |           |        |        |
| Created GPS Point 3   | XXX  | XXX  |           |        |        |
| …                     | …    | …    |           |        |        |
| …                     | …    | …    |           |        |        |
| C                     | XXX  | XXX  |           |        |        |

***Distance***

Definition of Distance is the distance between UE to Cell. [Not distance between UE to Site Location]. Once get the Distance from every point, we can derive HLoss and VLoss. 

<br>
<img src="\lte_mbb\img\lte_mbb_covtrain4.png" width=100% height=100% />
<br>

***HLoss***

Definition of HLoss is horizontal loss -> derived from Antenna pattern. 

1. The problem is to match our GPS point [UE Location] with Antenna Patter HLoss.  
2. Our goal is to get HLoss for each of our points by referring antenna pattern. 

How to calculate: For every location point, find the horizontal angle in reflects to azimuth. With this angle, we can lookup to HLoss Table in Antenna Pattern.

<br>
<img src="\lte_mbb\img\lte_mbb_covtrain5.png" width=100% height=100% />
<br>

***VLoss***

Definition of VLoss is horizontal loss -> derived from Antenna pattern. 

1. The problem is to match our GPS point [UE Location] with Antenna Patter VLoss.  
2. Our goal is to get VLoss for each of our points by referring antenna pattern. 

How to calculate: For every location point, find the vertical angle in reflects to Mtilt + Etilt. With this angle, we can lookup to VLoss Table in Antenna Pattern 

---

#### Why Too Big CIO Causing Ping Pong Handover

Too big CIO will cause ping pong handover. It is because TT trigger too fast compared to actual cross point.

<br>
<img src="\lte_mbb\img\lte_mbb_ciopingpong.png" width=100% height=100% />
<br>

---

#### Why A2MG Change Will Only Impact Mobility Users

<br>
<img src="\lte_mbb\img\lte_mbb_a2mobility.png" width=100% height=100% />
<br>

---

#### References

1. Accuver XCAP
2. 3GPP TS 36.211