Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2019/06/14<br>
Date Edited: 2022/02/07<br>

---

#### Downlink Reference Signal (RS) 

Most important -> Cell Specific RS (C-RS) [1]

1. Most of the channels (e.g, PDSCH, PDCCH, PBCH etc) is for carrying a special information (a sequence of bits) and they have some higher layer channel connected to them. 
2. Reference Signal is a special signal that exists only at PHY layer. This is not for delivering any specific information.  
3. The purpose of this Reference Signal is to deliver the reference point for the downlink power. 
4. When UE try to figure out DL power (i.e, the power of the signal from a eNode B), it measure the power of this reference signal and take it as downlink cell power. 

Picture below shows that: [1]

1. Logical antenna port for CRS: 1, 2, or 4 ports 
2. Gray = DTX (Discontinuous transmission) - Not transmitting RS because other ports are using that RE location for transmitting RS. 

<br>
<img src="\lte_mbb\img\lte_mbb_crsloc.png" width=100% height=100% />
<br>

***Relation of PCI Planning with C-RS Location***

1. PCI influence the RS pattern as well. (Based on PSS).
2. Each antenna port use different RS pattern. .
3. In case of 1 antenna port: 6 different pattern can be generated for RS (Mod 6).
4. In case of 2 antenna port: 3 different pattern can be generated for RS (Mod 3). 
5. In case of 4 antenna port: 3 different pattern can be generated for RS (Mod 3).

Why every PCI needs different RS locations? [2]

1. RS cannot be overlapped, if overlapped it causes interferences.
2. So if Mod3 = It means it is possible for the coverage to overlapped up to 3 Cell that have PSS 0, 1, 2. 

***Other types of DL RS***

0. Cell Specific RS (C-RS) -> As discussed above
1. UE Specific RS 
2. Positioning RS 
3. Channel State Information RS (CSI-RS)

<br>
<img src="\lte_mbb\img\lte_mbb_dlrstype.png" width=100% height=100% />
<br>

Eg: UE Speific RS [2]

<br>
<img src="\lte_mbb\img\lte_mbb_uers.png" width=50% height=50% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_uers2.png" width=100% height=100% />
<br>

Eg: Positioning RS [2]

<br>
<img src="\lte_mbb\img\lte_mbb_prs.png" width=50% height=50% />
<br>

Eg: Channel State Information RS (CSI-RS) [2]

<br>
<img src="\lte_mbb\img\lte_mbb_csirs.png" width=100% height=100% />
<br>

***Available RE for Traffic & Control Channel***

1. Number of Non-RS RE which are not RS RE and DTX is depend on the nu of antenna port. 
2. This Non-RS RE is used Traffic and Common Channel (PBCH, PCFICH, PDCCH, etc). 

<br>Definition of  number of RE per Symbol per PRB: 

    RS_RE_B(n): number of RS RE per symbol per PRB under RS symbol 
    RS_RE_A(n): number of RS RE per symbol per PRB under non RS symbol 
    DTX_RE_B(n): number of DTX RE per symbol per PRB under RS symbol 
    DTX_RE_A(n): number of DTX RE per symbol per PRB under non RS symbol 
    NRS_RE_B(n): number of non-RS and non-DTX RE per symbol per PRB under RS symbol 
    NRS_RE_A(n): number of non-RS and non-DTX RE per symbol per PRB under non RS symbol 

<br>
<img src="\lte_mbb\img\lte_mbb_crsloc2.png" width=100% height=100% />
<br>

| Antenna  | Symbol Where RS Present |             |             | Symbol Where RS Not Present |             |             |
|----------|-------------------------|-------------|-------------|-----------------------------|-------------|-------------|
| Port (n) | RS_RE_B(n)              | DTX_RE_B(n) | NRS_RE_B(n) | RS_RE_A(n)                  | DTX_RE_A(n) | NRS_RE_A(n) |
| 1        | 2                       | 0           | 10          | 0                           | 0           | 12          |
| 2        | 4                       | 4           | 16          | 0                           | 0           | 24          |
| 4        | 4                       | 12          | 32          | 4 or 0                      | 12 or 0     | Avg 44.8    |

---

#### Antenna Ports 

In LTE, every logical antenna port will generate its own resource grid. Means, every resource grid should have RS. This RS mapping can be mapped based on below table: [3]

| Antenna Ports | DL RS                                 | Release |
|---------------|---------------------------------------|---------|
| Port 0-3      | Cell Specific RS (C-RS)               | Rel-8   |
| Port 4        | MBSFN RS                              | Rel-8   |
| Port 5        | UE Specific RS for TM7 Beamforming    | Rel-8   |
| Port 6        | Positioning RS                        | Rel-9   |
| Port 7-8      | UE Specific RS for TM8 Beamforming    | Rel-9   |
| Port 9-14     | UE Specific RS for TM9 Beamforming    | Rel-10  |
| Port 15-22    | Channel State Information RS (CSI-RS) | Rel-10  |

The way in which these logical antenna ports are assigned to the physical transmit antennas of a base station is up to the base station, and can vary between base stations of the same type (because of different operating conditions) and also between base stations from different manufacturers. The base station does not explicitly notify the UE of the mapping that has been carried out, rather the UE must take this into account automatically during demodulation. 

<br>
<img src="\lte_mbb\img\lte_mbb_antport.png" width=100% height=100% />
<br>

---

#### Transmission Mode (TM)

Summary Table on Transmission Mode: [4] [5]

<br>
<img src="\lte_mbb\img\lte_mbb_tmsum.png" width=100% height=100% />
<br>

Antenna Port Corresponding to Transmission Mode: [2] [5]

<br>
<img src="\lte_mbb\img\lte_mbb_tmsum2.png" width=100% height=100% />
<br>

Codebook Based/or Non Codebook based Transmission Modes: [4] [5]

<br>
<img src="\lte_mbb\img\lte_mbb_tmsum3.png" width=100% height=100% />
<br>

***TM 1 - Single Transmit Antenna***

This mode uses only one transmit antenna. 

***TM 2 - Transmit Diversity***

1. Transmit diversity is the default MIMO mode. 
2. It sends the same information via various antennas. Each antenna stream uses different coding and different frequency resources. 
3. Improve SNR 
4. More robust, increase reliability. 

When transmit diversity is being used?

1. Usually as a fall back technology. When spatial multiplexing cannot be used (eg: In poor RF condition). 
2. Transmit important cannel: Eg- Control channel, PBCH, PDCCH. 

***TM 3 - Spatial Multiplexing (OL) with CDD***

<br>
<img src="\lte_mbb\img\lte_mbb_tm3.png" width=100% height=100% />
<br>

1. Supports 2-4 layers (2-4 antennas) 
2. Open Loop (OL) means: Not requires UE feedback (Not requires PMI) 
3. Used when -> Channel info is missing, or channel condition rapidly changes (when UE moves very fast) -> Not practical to use close loop in this condition. 

CDD means Cyclic Delay Diversity: 

The signal is supplied to every antenna with a specific delay (cyclic delay diversity, or CDD), thus artificially creating frequency diversity. This will improve reliability of every streams. 

<br>
<img src="\lte_mbb\img\lte_mbb_tm32.png" width=100% height=100% />
<br>

***TM 4 - Spatial Multiplexing (CL) with CDD***

<br>
<img src="\lte_mbb\img\lte_mbb_tm4.png" width=100% height=100% />
<br>

1. Supports up to 4 layers (4 Antennas). 
2. To permit channel estimation at the receiver, the base station transmits cell-specific reference signals (RS), distributed over various resource elements (RE) and over various timeslots.  
3. Close Loop (CL) - UE send response on channel situation (PMI) 

Sample Visualization: 

1. Case of 2x2 MIMO 
2. Both data only arrive at 1UE -> Indicates TM4 is for Single User MIMO (SU-MIMO). 
3. Refer 3GPP TS 36.211 Rel12 for 4 layers samples.  

<br>
<img src="\lte_mbb\img\lte_mbb_tm42.png" width=100% height=100% />
<br>

Precoding Table: 

<br>
<img src="\lte_mbb\img\lte_mbb_tm43.png" width=100% height=100% />
<br>

Element inside this table Matrix: Represents precoding. Precoding is not improving data rates directly: Efficient precoding improves PDSCH decoding rates (Improve BLER). Different precoding means: Antenna streams/channel (H) is being decoded by differently (Phase changed). Improve reliability of antenna streams/channels.  

How Phase is changed? # This is complicated.

    1 = Normal Phase 0deg 
    -1 = Change phase 180deg 
    j =  Change phase to different plane (90deg from 1) 
    -j = Flip j 180deg (270deg from 1) 

<br>
<img src="\lte_mbb\img\lte_mbb_tm43.png" width=100% height=100% />
<br>

***TM 5 - Multi User MIMO***

TM5 is similar to TM4: However, layers is divided to different UE. Sample 2 x 2 MIMO (But UE does not support MIMO). Since UE not support MIMO, the extra layer can be devided into different Ues as below: 

2 x 2 MIMO (Supported) = (2 x 1 MIMO) + (2 x 1 MIMO)  

<br>
<img src="\lte_mbb\img\lte_mbb_tm43.png" width=100% height=100% />
<br>

***TM 6 - Spatial Multiplexing (CL) using 1 transmission layer***

1. This is special type of TM4 (It uses only 1 layer to transmit). 
2. Basically, TM6 is beamforming with codebook based (Phase and Weight changed). 
3. If implement more than 1T (Multiple beams can be observed) .
4. Start TM7 not using codebook anymore. 

<br>
<img src="\lte_mbb\img\lte_mbb_tm6.png" width=100% height=100% />
<br>

Sample 2 x 1 MIMO (But UE does not support MIMO) 

<br>
<img src="\lte_mbb\img\lte_mbb_tm62.png" width=100% height=100% />
<br>

***TM 7 - Single Layer Beamforming (Single Ant Port 5)***

1. Why use port 5? Because CRS is not strong/not accurate anymore when beamforming established. [Refer picture] 
2. Port 5 is used to transmit UE-Specific RS for better channel estimation. 
3. Both the data and the RS (UE Specific) are transmitted using the same antenna weightings. 
4. Because the UE requires only the UE specific RS for demodulation of the PDSCH, the data transmission for the UE appears to have been received from only one transmit antenna, and the UE does not see the actual number of transmit antennas. 
5. Therefore, this transmission mode is also called "single antenna port; port 5". The transmission appears to be transmitted from a single "virtual" antenna port 5.  
6. UE informed to use UE-specific RS for as the phase reference in demodulation -> Why important: Eliminates need of UE to know how precoding was performed -> Where Transmitted: UE-specific RS only transmitted in RB’s of the PDSCH for a given UE 

<br>
<img src="\lte_mbb\img\lte_mbb_tm62.png" width=100% height=100% />
<br>

1. The beam is formed based on the weightage of every transmit antenna. 
2. More antenna -> More beam can be formed. 
3. Different Weightage between transmit antenna -> Will formed different pattern of beam. 
4. Weightage: Most likely a power factor (Not Confirmed) 

How weightage is being decided: 

1. Calculate DoA and AoA (Direction of Arrival, Angle of Arrival) - Hard Way 
2. Estimate based on UL channel (TDD) - Because TDD is using same band in DL & UL, it is safe to estimate DL channel based on UL SRS. This is why beamforming is easier to implement in TDD. 

***TM 8 - Dual Layer Beamforming (Ant Port 7 and 8)***

1. Release 9 specifies dual-layer beamforming.  
2. This will permit the base station to weight two layers individually at the antennas so that beamforming can be combined with spatial multiplexing for one or more UEs.  

UE Specific RS (Port 7 and 8) 
The UE Specific RS must be coded differently so that the UE can distinguish among them.  

<br>
<img src="\lte_mbb\img\lte_mbb_tm8.png" width=100% height=100% />
<br>

Because 2 layers are used, both layers can be assigned to one UE (SU MIMO), or the 2 layers can be assigned to two separate UEs (MU MIMO).  

Dual Layer Beamforming (SU MIMO) - 2 Layer, 1UE 

<br>
<img src="\lte_mbb\img\lte_mbb_tm82.png" width=100% height=100% />
<br>

Dual Layer Beamforming (MU MIMO) - 2 Layer, 2UE 

<br>
<img src="\lte_mbb\img\lte_mbb_tm83.png" width=100% height=100% />
<br>

***TM 9 - Up to 8 Layer Transmission (Ant Port 7-14)*** 

1. Release 10 adds Transmission Mode 9. In this mode up to 8 layers can be used (8 physical transmitter is needed) - Leads to 8 x 8 MIMO. 
2. Virtual antenna ports used: Ant port 7 - 14. 
3. Both single user (SU) and multi user (MU) MIMO is possible, dynamic switching between both modes is possible without special signaling by higher layers (without RRC). 

Improved RS Structure: 

1. UE-specific (DM-RS) for demodulation of PDSCH. This is an extension of the beamforming concept of TM7 and TM8 to support more layers. 
2. In addition CSI-RS allows the UE downlink channels state information (CSI) measurements. They are cell-specific. 

The same elements are used for ports 7,8,11,12 (noted as Rx, blue) and 9,10,13,14 (noted as Ry, green), the reference signals must be coded differently so that the UE can distinguish among them. 

<br>
<img src="\lte_mbb\img\lte_mbb_tm9.png" width=100% height=100% />
<br>
 
**Why start TM7 no need to use Codebook for precoding?**

Because DM-RS and CSI RS is being introduced - DMRS is applied before precoding, so weightage is known for beamforming.

1. The UE-specific DM-RS is applied to the data streams before the precoding.  
2. That means the UE receives the known RS which is precoded and transmitted via the channel.  
3. Thus the receiver does not need to know the used precoding in advance.  
4. There is no need to use special codebooks anymore, the UE does not send back the the PMI. -> In other words the spatial multiplexing is able to use the full range of weighting (precoding) for beamforming now, not only discrete precoding via the codebook like in TM3…6.

<br>
<img src="\lte_mbb\img\lte_mbb_tm92.png" width=100% height=100% />
<br>

vs

<br>
<img src="\lte_mbb\img\lte_mbb_tm93.png" width=100% height=100% />
<br>

TM9: The UE-specific RS is applied before the precoding. This enables non-codebook based precoding. So the full range of beamforming patterns can be used. 

***TM 10 - Up to 8 Layer Transmission (Ant Port 7-14)***

TM9: The UE-specific  

---

#### DL Power Allocation

1. eNB define the downlink RE power (EPRE(Energy per Resource Element)) of Reference signal and non reference signal. 
2. The EPRE of RS is directly defined the parameter as Reference-signal-power.  
3. The EPRE of non RS is not directly defined the parameter but it can be calculated by using ρA and ρB parameter which are defended by 3GPP.  

<br>
<img src="\lte_mbb\img\lte_mbb_rspow.png" width=100% height=100% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_rspow2.png" width=50% height=50% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_rspow3.png" width=50% height=50% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_rspow4.png" width=100% height=100% />
<br>

Calculation:

    EPRE_RS = RS Power 
    EPRE_A = Type A RE (PDSCH RE with no RS RE in the symbol) 
    EPRE_B = Type B RE (PDSCH RE with RS RE in the symbol) 

    ρA = EPRE_A / EPRE_RS 
    ρB = EPRE_B / EPRE_RS 
    ρB / ρA = EPRE_B / EPRE_A 

    Pa = ρA 
    Pb = ρB / ρA 

Formulas:

    RS Power (dBm) = Type A PDSCH RE Power (dBm) - Pa (dB) 
    Type A PDSCH RE Power (dBm) = 10 × log10 (Power per Port (dBm) / Subcarrier Number) 
    Type A PDSCH RE Power (dBm) =  Power per Port (dBm) - 10 x log10 (Subcarrier Number) 
    Type B PDSCH RE Power (dBm) = Type A PDSCH RE Power (dBm) + 10 × log10 (Rho B/Rho A) 

<br>
<img src="\lte_mbb\img\lte_mbb_rspow5.png" width=100% height=100% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_rspow6.png" width=100% height=100% />
<br>

For RS Power simulation code, go to this [repository](https://github.com/zulfadlizainal/4G-LTE-DL-Power-Allocation/tree/master/Ideal%20RS%20Power%20Settings).

---

#### References

1. 3GPP TS 36.211 Section 6.10
2. [Sharetechnote](https://www.sharetechnote.com/html/Handbook_LTE_Interference_Downlink.html#Intrafrequency_varying_PCI)
3. 3GPP TS 36.211 Section 6.2.1
4. [R&S Whitepaper](https://cdn.rohde-schwarz.com/pws/dl_downloads/dl_application/application_notes/1ma186/1MA186_2e_LTE_TMs_and_beamforming.pdf)
5. 3GPP TS 36.211 V 12.5.0 