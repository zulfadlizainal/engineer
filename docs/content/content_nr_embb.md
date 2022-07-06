Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/08/31<br>
Date Edited: 2022/07/06<br>

---

### 5G NR enhanced Mobile Broadband (eMBB)

#### Overview 

- [Concept and Target](/nr_embb/nr_embb_overview.md?id=Concept-and-Target)<br>
- [3GPP Roadmap](/nr_embb/nr_embb_overview.md?id=3GPP-Roadmap)<br>
- [Key Technology Difference with LTE](/nr_embb/nr_embb_overview.md?id=Key-Technology-Difference-with-LTE)<br>

#### Network Architecture

- [Network Architecture](/nr_embb/nr_embb_nwarchitecture.md?id=Network-Architecture)<br>
- [SA vs NSA](/nr_embb/nr_embb_nwarchitecture.md?id=SA-vs-NSA)<br>
- [CA vs DC](/nr_embb/nr_embb_nwarchitecture.md?id=CA-vs-DC)<br>
- [Deployment Options](/nr_embb/nr_embb_nwarchitecture.md?id=Deployment-Options)<br>
- [Option 3: EN-DC](/nr_embb/nr_embb_nwarchitecture.md?id=Option-3-EN-DC)<br>
- [Protocol Stack](/nr_embb/nr_embb_nwarchitecture.md?id=Protocol-Stack)<br>
- [Control Plane Functionality](/nr_embb/nr_embb_nwarchitecture.md?id=Control-Plane-Functionality)<br>
- [User Plane Functionality](/nr_embb/nr_embb_nwarchitecture.md?id=Control-Plane-Functionality)<br>
- [Protocol Functional Split in gNB](/nr_embb/nr_embb_nwarchitecture.md?id=Protocol-Functional-Split-in-gNB)<br>
- [User Plane Data Split in CA and DC](/nr_embb/nr_embb_nwarchitecture.md?id=User-Plane-Data-Split-in-CA-and-DC)<br>
- [User Plane QOS Framework](/nr_embb/nr_embb_nwarchitecture.md?id=User-Plane-QOS-Framework)<br>
- [5QI QOS Identifier](/nr_embb/nr_embb_nwarchitecture.md?id=_5QI-QOS-Identifier)<br>

#### Frame Structure

- [Resource Grid and Waveform](/nr_embb/nr_embb_framestructure.md?id=Resource-Grid-and-Waveform)<br>
- [Frequency Domain](/nr_embb/nr_embb_framestructure.md?id=Frequency-Domain)<br>
- [Time Domain](/nr_embb/nr_embb_framestructure.md?id=Time-Domain)<br>
- [TDD Structures](/nr_embb/nr_embb_framestructure.md?id=TDD-Structures)<br>
- [TDD Flexible Symbols](/nr_embb/nr_embb_framestructure.md?id=TDD-Flexible-Symbols)<br>
- [TDD Coexistence with LTE](/nr_embb/nr_embb_framestructure.md?id=TDD-Coexistence-with-LTE)<br>

#### Features and Algorithm 

- PRACH Power Control
- PUCCH Power Control
- PUSCH Power Control
- SRS Power Control
- Dynamic Power Control for NSA
- DSS
- Carrier Aggregation

#### Layer 1: PHY

- [SCS for SSB](/nr_embb/nr_embb_layer1.md?id=SCS-for-SSB)<br>
- [SSB](/nr_embb/nr_embb_layer1.md?id=SSB)<br>
- [SSB Frequency Domain Resource](/nr_embb/nr_embb_layer1.md?id=SSB-Frequency-Domain-Resource)<br>
- [SSB Time Domain Resource](/nr_embb/nr_embb_layer1.md?id=SSB-Time-Domain-Resource)<br>
- [SSB Burst Set and Periodicity](/nr_embb/nr_embb_layer1.md?id=SSB-Burst-Set-and-Periodicity)<br>
- [PRACH Preamble Format](/nr_embb/nr_embb_layer1.md?id=PRACH-Preamble-Format)<br>
- PRACH Time Domain Resource
- PRACH Frequency Domain Resource
- [Reference Signal Map](/nr_embb/nr_embb_layer1.md?id=Reference-Signal-Map)<br>
- [CORESET](/nr_embb/nr_embb_layer1.md?id=CORESET)<br>
- Search Space
- [SFI](/nr_embb/nr_embb_layer1.md?id=SFI)<br>
- [DCI Format](/nr_embb/nr_embb_layer1.md?id=DCI-Format)<br>
- [UCI (PUCCH Format)](/nr_embb/nr_embb_layer1.md?id=UCI-PUCCH-Format)<br>
- [PDSCH/PUSCH Channel Processing](/nr_embb/nr_embb_layer1.md?id=PDSCHPUSCH-Channel-Processing)<br>
- PUSCH Channel Processing
- CBG
- MCS
- Layer Mapping
- Transmission Scheme
- CSI Reporting
- Frequency Domain Resource Allocation
- Time Domain Resource Allocation
- DL Scheduling
- UL Scheduling
- BWP
- DL HARQ
- UL HARQ
- MIMO
- Beamforming
- PHR
- UE Measurment (RP/RQ/SINR)

#### Layer 2: MAC, RLC, PDCP, SDAP

- MAC Layer
- RLC Layer
- PDCP Layer
- SDAP Layer

#### Layer 3: RRC, NAS 

- MIB
- SIB
- UE Capability Information
- RRC Setup
- Flow Setup
- RRC Release

#### Protocol and Procedures 

- [Initial Access: Synchronization Establishment](/nr_embb/nr_embb_procedure?id=initial-access-synchronization-establishment)<br>
- [Initial Access: Synchronization Raster](/nr_embb/nr_embb_procedure?id=initial-access-synchronization-raster)<br>
- [MIB and SIB Acquisition](/nr_embb/nr_embb_procedure?id=MIB-and-SIB-Acquisition)<br>
- [RACH Procedure](/nr_embb/nr_embb_procedure?id=RACH-Procedure)<br>
- BWP Switching
- Paging
- [RRC State](/nr_embb/nr_embb_procedure.md?id=RRC-State)<br>

#### Beam Management

- Initial Beam Acquisition
- Beam Switching
- Beam Refinement
- Beam Failure and Recovery

#### Idle Mode Mobility 

- PLMN Selection
- Cell Selection
- Cell Reselection

#### Connected Mode Mobility 

- Measurement Reports
- Measurement Events
- Handover
- RLF

#### Practical Analysis

- [Design Cell Range for TDD](/nr_embb/nr_embb_practical.md?id=Design-Cell-Range-for-TDD)<br>
- Check Slot Utilization
- Dimension Channels Capacity