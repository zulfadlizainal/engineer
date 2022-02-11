Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2019/02/26<br>
Date Edited: 2022/02/11<br>

---

### 4G LTE Mobile Broadband (MBB)
#### Overview 

- [UE Category](/lte_mbb/lte_mbb_overview.md?id=Ue-Category)<br>
- [Operating Bands](/lte_mbb/lte_mbb_overview.md?id=Operating-Bands)<br>
- [Supported Bandwidths](/lte_mbb/lte_mbb_overview.md?id=Supported-Bandwidths)<br>
- [CA Band Combinations](/lte_mbb/lte_mbb_overview.md?id=CA-Band-Combinations)<br>

#### Network Architecture 

- [System Architecture Evolution (SAE)](/lte_mbb/lte_mbb_nwarchitecture.md?id=System-Architecture-Evolution-SAE)<br>
- [Evolved Packet Core (EPC)](/lte_mbb/lte_mbb_nwarchitecture.md?id=Evolved-Packet-Core-EPC)<br>
- [Bearer Architecture](/lte_mbb/lte_mbb_nwarchitecture.md?id=Bearer-Architecture)<br>
- [E-UTRAN Architecture](/lte_mbb/lte_mbb_nwarchitecture.md?id=E-UTRAN-Architecture)<br>
- [Protocol Stack](/lte_mbb/lte_mbb_nwarchitecture.md?id=Protocol-Stack)<br>

#### Frame Structure 

- [Basic Time Unit (Ts)](/lte_mbb/lte_mbb_framestructure.md?id=Basic-Time-Unit-Ts)<br>
- [FDD Frame (Type 1)](/lte_mbb/lte_mbb_framestructure.md?id=FDD-Frame-Type-1)<br>
- [TDD Frame (Type 2)](/lte_mbb/lte_mbb_framestructure.md?id=TDD-Frame-Type-2)<br>
- [Uplink Frame](/lte_mbb/lte_mbb_framestructure.md?id=Uplink-Frame)<br>

#### Features and Algorithm 

- Link Adaptation<br> 
- Carrier Aggregation (CA)<br> 
- [MIMO Concept](/lte_mbb/lte_mbb_featurealgo.md?id=MIMO-Concept)<br>
- Massive MIMO<br>
- Beamforming<br>
- UL Power Control for PRACH<br> 
- UL Power Control for PUCCH<br> 
- UL Power Control for PUSCH<br> 
- Idle Mode Mobility Load Balancing (IMLB)<br> 
- Connected Mode Mobility Load Balancing (MLB)<br> 
- Mobility Robustness Optimization (MRO)<br> 
- Automatic Neighbor Relation (ANR)<br> 

#### Layer 1: PHY

- [Downlink Reference Signal (RS)](/lte_mbb/lte_mbb_layer1.md?id=Downlink-Reference-Signal-RS)<br>
- UL DMRS and SRS<br> 
- [Antenna Ports](/lte_mbb/lte_mbb_layer1.md?id=Antenna-Ports)<br>
- [Transmission Mode (TM)](/lte_mbb/lte_mbb_layer1.md?id=Transmission-Mode-TM)<br>
- [DL Power Allocation](/lte_mbb/lte_mbb_layer1.md?id=DL-Power-Allocation)<br>
- Measurement Metrics (RPRP, RSRQ, SINR, RSSI)<br>
- Overlapping Measurment<br> 

#### Layer 2: MAC, RLC, PDCP 

- [MAC: Scheduler](/lte_mbb/lte_mbb_layer2.md?id=MAC-Scheduler)<br>
- MAC: HARQ<br> 
- MAC: Retransmission<br>
- MAC: Timing Advance<br>  
- MAC: Power Headroom (PHR)<br> 
- MAC: Buffer Status Reporting (BSR)<br> 
- MAC: SCell Activation/Deactivation<br> 
- [RLC: Concept](/lte_mbb/lte_mbb_layer2.md?id=RLC-Concept)<br>
- [RLC: TM, AM, UM](/lte_mbb/lte_mbb_layer2.md?id=RLC-TM-AM-UM)<br>
- [RLC: ARQ in AM](/lte_mbb/lte_mbb_layer2.md?id=RLC-ARQ-in-AM)<br>
- RLC: Retransmission<br> 

#### Layer 3: RRC, NAS

- [MIB](/lte_mbb/lte_mbb_layer3.md?id=mib)<br>
- [SIB](/lte_mbb/lte_mbb_layer3.md?id=sib)<br>
- RRC<br>

#### Protocol and Procedures 

- Attach<br> 
- RACH<br> 
- Bearer Allocation<br> 

#### Idle Mode Mobility 

- Cell Selection<br> 
- Intra Frequency Cell Reselection<br> 
- [Inter Frequency Cell Reselection](/lte_mbb/lte_mbb_idle.md?id=Inter-Frequency-Cell-Reselection)<br>

#### Connected Mode Mobility 

- Measurement Reports<br>
- [Measurement Events](/lte_mbb/lte_mbb_connected.md?id=Measurement-Events)<br>
- Intra Frequency Handover<br>
- Inter Frequency Handover<br>
- Measurement Gap <br>

#### Practical Analysis 

- Plan TAC<br> 
- Plan PCI<br> 
- [Differentiate PRB & TTI Utilization](/lte_mbb/lte_mbb_practical.md?id=Differentiate-PRB-&-TTI-Utilization)<br>
- [Differentiate TX, Layer, Spatial Rank, and Codewords](/lte_mbb/lte_mbb_practical.md?id=Differentiate-TX-Layer-Spatial-Rank-and-Codewords)<br>
- Calculate Throughput<br>
- Calculate Spectrum Efficiency<br>
- [Reading Antenna Pattern](/lte_mbb/lte_mbb_practical.md?id=Reading-Antenna-Pattern)<br>
- Simulate Coverage based on Path Loss<br>
- [Simulate Coverage for Train Lines](/lte_mbb/lte_mbb_practical.md?id=Simulate-Coverage-for-Train-Lines)<br>
- [Why Too Big CIO Causing Ping Pong Handover](/lte_mbb/lte_mbb_practical.md?id=Why-Too-Big-CIO-Causing-Ping-Pong-Handover)<br>
- [Why A2MG Change Will Only Impact Mobility Users](/lte_mbb/lte_mbb_practical.md?id=Why-A2MG-Change-Will-Only-Impact-Mobility-Users)<br>
