Topic: 4G LTE<br>
Sub-Topic: eMTC<br>
Date Written: 2019/05/17<br>
Date Edited: 2022/02/16<br>

---

#### 3GPP Roadmap

References: [1]

Picture from [2]

<br>
<img src="\lte_emtc\img\lte_emtc_3gpproadmap.png" width=100% height=100% />
<br>

---

#### UE Category

IoT UE category so far from Rel 13 to Rel 14. 

<br>
<img src="\lte_emtc\img\lte_emtc_uecatiot.png" width=100% height=100% />
<br>

Table version for easy copy:

| Device Category     | Cat-4                | Cat-1                | MTC Cat-0            | eMTC Cat-M1          | NB-IoT Cat-NB1     |
|---------------------|----------------------|----------------------|----------------------|----------------------|--------------------|
| 3GPP Release        | Release 8            | Release 8            | Release 12           | Release 13           | Release 13         |
| Device Bandwidth    | 20MHz                | 20MHz                | 20MHz                | 1.08MHz              | 180KHz             |
| Downlink Peak Rate  | 150Mbps              | 10Mbps               | *1Mbps               | *1Mbps               | <100kbps           |
| Uplink Peak Rate    | 50Mbps               | 5Mbps                | *1Mbps               | *1Mbps               | <100Kbps           |
| Device Duplex Mode  | Full Duplex          | Full Duplex          | Full or Half Duplex  | Full or Half Duplex  | Half Duplex        |
| Duplex              | FDD/TDD              | FDD/TDD              | FDD/TDD              | FDD/TDD              | FDD                |
| Modem Complexity    | Very High            | High                 | Medium               | Low                  | Very low           |
| Coverage Gain       | Base (MCL>140.7 dB)  | Base (MCL>140.7 dB)  | Base (MCL>140.7 dB)  | 15dB (MCL>155.7 dB)  | 23dB (MCL>164 dB)  |
| Battery Life        | Varies               | Varies               | Varies               | > 10 Years           | > 10 Years         |

<br>

***Cat M UE category info:***

<br>
<img src="\lte_emtc\img\lte_emtc_uecatm.png" width=50% height=50% />
<br>

Table version for easy copy:

| Device Category     | Cat M1      | Cat M1      | Cat M2      |
|---------------------|-------------|-------------|-------------|
| 3GPP Release        | Release 13  | Release 14  | Release 14  |
| Device Bandwidth    | 1.4MHz      | 1.4MHz      | 5MHz        |
| Downlink Peak Rate  | 1Mbps       | 1Mbps       | 4Mbps       |
| Uplink Peak Rate    | 1Mbps       | 3Mbps       | 7Mbps       |
| Max Downlink TBS    | 1000bits    | 2984bits    | 4008bits    |
| Max Uplink TBS      | 1000bits    | 2984bits    | 6968bits    |

---

#### Redefined Air Interface

Since R8, 3GPP has define lower complexity UE categories to compliment IoT vision. However, since R13, not only UE complexity is being reduced but even the air interface is being modified to suits specific needs of IoT. [3]

<mark>Why is it necessary to introduce specific architecture for IoT in air interface?</mark>

>The first main focus of the new air interface is changing the operating bandwidth of eMTC and NB-IoT. IoT UE does not need to monitor or decode any PRB outside the IoT system bandwidth. With this Bandwidth Low reduction, extra saving of power consumption can be achieved hence battery life savings can be up to 10 years. 

>The other reason is IoT technology requires to support deeper coverage. Deeper coverage means coverage gain compared to normal LTE should be increased by enabling certain IoT features such as Physical Channel Repetitions. eMTC able to support Maximum Coupling Loss (MCL) more than 155dB while NB-IoT able to support MCL more than 164dB.  

---

#### Carrier Deployment Mode

Key Concept: [4] [5] [6] [7]

1. Operating Bandwidth required for eMTC Cat M1 UE: 1.4MHz  
2. Operated within LTE wider system bandwidth 
3. 6 Consecutive PRB needed (6x180KHz): 1.08MHz 
4. 6 eMTC Consecutive PRB defined as Narrowband PRB in 3GPP 
5. The position of the 6 PRB varies depending on the configuration 
6. 6 PRB can be shared between Cat-M1 UE and Common UE 
7. eMTC divide the LTE system bandwidth into multiple sections of 1.4Mhz and use any one of those sections 
8. Cat M1 UE can use different 1.4Mhz section within the system bandwidth at every subframe 

<br>
<img src="\lte_emtc\img\lte_emtc_depmode.png" width=100% height=100% />
<br>

***Common Between LTE UE and eMTC UE***

1. Use same PSS and SSS – PCI Configured same as LTE 
2. Use  same CRS 
3. Use same MIB and SIBs 
4. Use same physical channel structure except LTE control channel 

?>eMTC PRB Location: Based on Narrowband Index

?>eMTC PCI Design: Same PCI with LTE

---

#### References

1. 3GPP TR 21.914
2. [Qualcomm](https://www.qualcomm.com/media/documents/files/leading-the-lte-iot-evolution-to-connect-the-massive-internet-of-things.pdf)
3. 3GPP TR 36.888 
4. 3GPP TS 36.211 Section 5.2.4 
5. 3GPP TS 36.331 Section 6  
6. 3GPP TS 36.211 Section 6.8B 
7. [Docomo](https://www.nttdocomo.co.jp/english/binary/pdf/corporate/technology/rd/technical_journal/bn/vol18_2/vol18_2_008en.pdf)