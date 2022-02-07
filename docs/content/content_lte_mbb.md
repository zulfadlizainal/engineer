Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2019/02/26<br>
Date Edited: 2022/02/07<br>

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

#### Layer 2: RLC, MAC, PDCP 

- RLC Concept<br> 
- RLC: TM, AM, UM<br> 
- RLC: ARQ in AM<br> 
- Scheduling Type<br> 
- Timing Advance<br> 
- HARQ<br> 
- MAC Retransmission<br> 
- RLC Retransmission<br> 
- Power Headroom (PHR)<br> 
- Buffer Status Reporting<br> 
- SCell Activation/Deactivation<br> 

#### Layer 3: RRC, NAS

- SIB Information Table<br> 
- L3 Filtering<br> 

#### Protocol and Procedures 

- RACH (Causes, Timer, Max Trans)<br> 
- Bearer Allocation<br> 
- UL Power Control for PRACH<br> 
- UL Power Control for PUCCH<br> 
- UL Power Control for PUSCH<br> 

#### Idle Mode Mobility 

- Idle Mode Parameter<br> 
- Cell Reselection Design<br> 

#### Connected Mode Mobility 

- Measurement Reports/Events<br> 
- Connected Mode Parameter<br> 
- Connected Mode Strategy<br> 

#### Practical Analysis 

- BLER (Ack, Nack, CRC, Discarded Retransmission)<br> 
- TAU (TAC Planning)<br> 
- PCI Planning Rule<br> 
- PRB vs TTI Utilization<br> 
- Throughput Calculation<br> 
- Spectrum Efficiency Calculation<br> 
- IFHO: A2 and A5 Consideration in Mobility & Static<br>
- Coverage Simulation for Train Lines<br> 
- Too Big CIO: Causing ping Pong HO<br>
- Calculate RP, RQ, SINR, O<br>
- Idle Mode Parameter Simulation