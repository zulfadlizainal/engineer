Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/08/31<br>
Date Edited: 2022/06/01<br>

---

#### Network Architecture

5G NR introduces some new nodes and architecture. These includes under the scope of NG-RAN (Next Generation Radio Access Network) nodes, 5GC (5G Core) nodes, and network interfaces. [1]

***<mark>Basic Concept</mark>*** 

<br>
<img src="\nr_embb\img\nr_embb_nwarchitecture.png" width=100% height=100% />
<br>

***Important terminologies:***

New Nodes in NG-RAN:

    gNB: NR Base Station
    ng-eNB (Next Generation eNB): Upgraded LTE Base Station that can talk to 5GC

New Nodes in 5GC:

    AMF (Access Mobility Function): Control Plane (CP) signaling handling entity
    UPF (User Plane Function): User Plane (UP) data handling entity

New Network Interfaces:

    Xn Interface Interfaces between NG-RAN nodes
    Xn-C: Interfaces between NG-RAN nodes for CP
    Xn-U: Interfaces between NG-RAN nodes for UP 
    
    NG Interface Interfaces between NG-RAN and 5GC
    NG-C: Interfaces between NG-RAN and AMF for CP
    NG-U: Interfaces between NG-RAN and UPF for UP

***gNB Architecture***

1. gNB in NG-RAN is further enhanced by the introduction of F1 Interface between gNB CU and DU.
2. F1 Interface is being used for protocol layer function split between gNB CU and DU.
3. It is an enhancement concept to C-RAN in LTE. C-RAN is only build to distribute RF.
4. F1 is build to support DU and CU architecture where lower and higher layer function can be separated.

Refer [2]

<br>
<img src="\nr_embb\img\nr_embb_gnbarchitecture.png" width=70% height=70% />
<br>

<br>
<img src="\nr_embb\img\nr_embb_gnbarchitecture2.png" width=70% height=70% />
<br>

---

#### SA vs NSA

1. NR can be deployed with SA (Standalone) or NSA (Non Standalone) deployment.
2. NSA means that DC (Dual Connectivity) need to be adapted between multiple RATs.

<br>
<img src="\nr_embb\img\nr_embb_savsnsa.png" width=100% height=100% />
<br>

***<mark>History of Cell Aggregation:</mark>*** Starts with CA and move to DC

1. Multi Cell Aggregation is a concept where allowing a cell to connect to multiple cell in the same time.
2. CA (Carrier Aggregation) allows UE to send/receive packets from multiple CCs (Component Carriers)
3. DC (Dual Connectivity) allows UE to send/receive packets from multiple Cell Groups across all CCs.  

?> Why DC is introduced when we already have CA: DC have more relaxed requirement on X2 backhaul allowing non colocated cell to be aggregated together. DC aggregation happen in PDCP layer which have more relaxed timing requirements compared to MAC layer aggregation in CA. That is why most CA implementation can only be seen in colocated cells.

<br>
<img src="\nr_embb\img\nr_embb_dchistory.png" width=100% height=100% />
<br>

---

#### CA vs DC

Key differences:

1. CA: Tight Backhaul Requirement (TTI Level), DC: Relaxed Backhaul Requirement.
2. CA: One MAC scheduler for all aggregated cells, DC: Independent MAC scheduler for MCG and SCG.
3. CA: Aggregation/Split at MAC layer, DC: Aggregation/Split at PDCP layer.

<br>
<img src="\nr_embb\img\nr_embb_cavsdc.png" width=100% height=100% />
<br>

<mark>Important Terminologies:</mark>

    MN: Master Node
    SN: Secondary Node
    MCG: Master Cell Group
    SCG: Secondary Cell Group
    PCell: Primary Cell
    Scell: Secondary Cell
    PSCell: Primary Secondary Cell

<mark>Important Definitions:</mark>

xNB Level:

    MN: xNB that has termination to core network CP nodes and sends RRC (Eg: S1-MME, NG-C) 
    SN: xNB that does not have termination to core network CP and provides additional cells to MN

Cell/UE Level:

    PCell: A primary cell on MN
    PSCell: A primary cell on SN once SN is added by MN
    SCell: Secondary cell on MN and SN
    SpCell: PCell in MCG or PSCell in SCG
    MCG: Cells associated with MN (PCell + Optional SCell)
    SCG: Cells associated with SN (PSCell + Optional SCell)

Operation Level: 

    Anchor: MN that handles CP for SN
    Non Anchor: SN that CP being handled by MN 

---

#### Deployment Options

Key Concepts: [4]

1. 3GPP has aligned 7 deployment options standards where MNO can choose based on their strategy.
2. The deployment options are categorized based on SA and NSA implementation.

<br>
<img src="\nr_embb\img\nr_embb_depopt.png" width=100% height=100% />
<br>

Table for easy copy:

| Type          | Options | Core | RAN         | Description                    |
|---------------|---------|------|-------------|--------------------------------|
| SA (No DC)    | 1       | EPC  | eNB         | Common 4G implementation       |
|               | 2       | 5GC  | gNB         | Common 5G implementation       |
|               | 5       | 5GC  | ng-eNB      | LTE air interface with 5G core |
|               | 6       | EPC  | gNB         | NR air interface with 4G core  |
| NSA (Need DC) | 3/3a/3x | EPC  | eNB, en-gNB | LTE eNB as Anchor (EN-DC)      |
|               | 4/4a    | EPC  | ng-eNB, gNB | NR gNB as Anchor (NE-DC)       |
|               | 7/7a/7x | 5GC  | ng-eNB, gNB | LTE ng-eNB as Anchor (NGEN-DC) |

Visual representation of 5G NR deployment options excluding Option 6. [5]

<br>
<img src="\nr_embb\img\nr_embb_depopt2.png" width=100% height=100% />
<br>

***Popular Deployment Strategy***

1. Most MNO with 4G network assets will tend to start with NSA deployment for fast implementation and cost efficiency.
2. Option 6 are rarely discussed by the industries because of its an unlikeliness possibility to happen but it is still defined in the specifications as a choice.

<br>
<img src="\nr_embb\img\nr_embb_depopt3.png" width=100% height=100% />
<br>

---

#### Option 3: EN-DC

1. Option 3: EPC as core network, DC for RAN with LTE eNB as Anchor and NR en-gNB as Non Anchor.
2. MN is always LTE eNB as it handles Control Plane RRC for the DC.
3. Difference between 3/3a/3x -> <mark>Different User Plane path options.</mark>

Picture from [3]

<br>
<img src="\nr_embb\img\nr_embb_option3.png" width=100% height=100% />
<br>

***<mark>NSA Option 3 (EN-DC): UP Bearers from Network Perspective</mark>***

Concept from [6]

1. In case of Split Bearer, the PDCP will perform the split (for DL) and aggregation (for UL).
2. When no SCG bearer added or SCG fail to add, only MCG bearer will be used.
3. PDCP in MN can be upgraded to NR PDCP protocol.

<br>
<img src="\nr_embb\img\nr_embb_endcupnet.png" width=100% height=100% />
<br>

***<mark>NSA Option 3 (EN-DC): UP Bearers from UE Perspective</mark>***

Concept from [6]

1. From UE perspective, the deployment options concept does not apply.
2. UE shall only understand whether to split or not (for UL) and whether to aggregate or not (for DL).

<br>
<img src="\nr_embb\img\nr_embb_endcupue.png" width=100% height=100% />
<br>

***<mark>NSA Option 3 (EN-DC): UP Bearers Bearer Reconfigurations</mark>***

Concept from [6]

?> Deployment options are not fixed. Depends on implementation, options can switch with PDCP reconfig.

<br>
<img src="\nr_embb\img\nr_embb_endcupbearer.png" width=100% height=100% />
<br>

Example of Split Bearer Implementation by OEM: [7]

?> Generally, most OEM try to utilize NR leg in good NR RF, and split User Plane (UP) to LTE once NR RF become lower.

<br>
<img src="\nr_embb\img\nr_embb_splitbearerericsson.png" width=100% height=100% />
<br>

***<mark>NSA Option 3 (EN-DC): CP Enhancement</mark>***

Control plane implementation is totally separate concept from user plane implementation. [3] [5]

> Enhancement 1: SRB3 is optional. Both RAN and UE need to support SRB3 to be able to enable it.
> Enhancement 2: Can be configured as both air interface transmit same RRC or transmit different RRC.

<br>
<img src="\nr_embb\img\nr_embb_endccpenhance.png" width=100% height=100% />
<br>

---

#### Protocol Stack

2 types of protocol stack: [8]

1. Control Plane
2. User Plane

***<mark>End to End Control Plane protocol stack in NR system.</mark>***

<br>
<img src="\nr_embb\img\nr_embb_cpstack.png" width=100% height=100% />
<br>

***<mark>End to End User Plane protocol stack in NR system.</mark>***

<br>
<img src="\nr_embb\img\nr_embb_upstack.png" width=100% height=100% />
<br>

***<mark>CP and UP - How it Connects?</mark>***

NR radio access protocol stack are similar with LTE. SDAP protocol is the only addition in NR. [6]

<br>
<img src="\nr_embb\img\nr_embb_cpupstack.png" width=100% height=100% />
<br>

Protocol layer <mark>functional mapping</mark> with channel coding remain the same with LTE.

<br>
<img src="\nr_embb\img\nr_embb_cpupfunctionmap.png" width=100% height=100% />
<br>

---

#### Control Plane Functionality

Refer [3]

***<mark>Control Plane: NAS Layer Function</mark>***

For a system that dependent on 5GC for Control Plane, NAS will be terminated to 5GC’s AMF.<br> 
For a system that dependent on EPC for control plane, NAS will be terminated at EPC’s MME

1. NAS chippering and integrity protection
2. Registration Management
3. Connection Management
4. Reachability Management
5. Mobility Management
6. Transport for Session Management
7. Access Authentication
8. Access Authorization
9. Transport for SMS Messages

***<mark>Control Plane: RRC Layer Function</mark>***

RRC handles important Control Plane information for AS (Access Stratum).<br> 
Everything related to Radio Resource Control is handles by RRC.

1. Broadcast System Information
2. Measurement Configurations and Reporting
3. Paging
4. Initial Security Activation
5. Connection Control Eg: RRC Establishment, Release, Suspend, Resume.
6. Mobility Control Eg: Handover
7. DRB Configuration and Modification
8. Radio Configuration Control Eg: Resource
9. Recovery from RLF

?> Physical sublayer will mapped all user plane and control plane from higher layer with physical channels.

!> Physical channels is a broad discussion because it involves many kind of channels and signals with its own proprietary functionality.

---

#### User Plane Functionality

Refer [1]

***<mark>User Plane: SDAP Layer Function</mark>*** 

SDAP sublayer is added to NR when 5GC is being used in User Plane.<br> 
SDAP main functions is to handles QoS Flow ID – A enhanced concept of QCIs in LTE.

1. Transfer User Plane Data <mark>[New in NR]</mark>
2. QoS Flow ID mapping with DRB for DL & UL <mark>[New in NR]</mark>

***<mark>User Plane: PDCP Layer Function</mark>*** 

PDCP hold the bridge to combine both User Plane and Control Plane.<br> 
PDCP sublayer introduced few new functions in NR such as handling user plane split bearer.

1. Transfer of Data (User Plane to Control Plane)
2. IP Header Compressions
3. Security Functions
4. Retransmissions of Missing Packets
5. Reordering and Duplication Detection <mark>[New in NR]</mark>
6. PDCP PDU Routing in case of Split Bearer <mark>[New in NR]</mark>
7. Timer Based Packet Discarding
8. PDCP Re-establishment and Data Recovery
9. Duplication of PDCP PDUs <mark>[New in NR]</mark>

***<mark>User Plane: RLC Layer Function</mark>*** 

RLC sublayer holds a lot of functionalities but all functionalities are mostly similar wit LTE.<br> 
The only difference in NR is ‘Reordering & Duplication Detection’ function has been moved to PDCP.

1. Transfer of upper layer PDUs
2. Error Correction through ARQ (AM only)
3. Segmentation (AM and UM) of RLC SDUs 
4. Re-segmentation (AM only) of RLC SDUs
5. Reassembly of SDU (AM and UM)
6. Duplicate Detection (AM only)
7. RLC SDU discard (AM and UM)
8. RLC re-establishment
9. Protocol error detection (AM only)

***<mark>User Plane: MAC Layer Function</mark>*** 

Key functions for MAC sublayer 1) Scheduling 2) HARQ 3) Beam Management 4) RACH 5) TA<br> 
Beam Management is being done in MAC layer for fast beam recovery.

1. Assignment DL & UL Resources
2. HARQ Retransmission
3. Packet to TB conversion (Mux/Demux)
4. Priority Handling of Logical Channel
5. Error Correction Through HARQ
6. Beam Quality Feedback <mark>[New in NR]</mark>
7. Beam Switch Procedures <mark>[New in NR]</mark>
8. RACH Procedures
9. Maintenance of UL Timing (TA)
10. Support for Multiple Numerology <mark>[New in NR]</mark>

?> Physical sublayer will mapped all user plane and control plane from higher layer with physical channels.

!> Physical channels is a broad discussion because it involves many kind of channels and signals with its own proprietary functionality.

---

#### Protocol Functional Split in gNB

Refer [5] [9]

Protocol layer functional split can be implemented based on few standardized Options.<br> 
The decision of implementation is based on hardware capability and requirements.

<br>
<img src="\nr_embb\img\nr_embb_protocolfuncsplit.png" width=100% height=100% />
<br>

***<mark>Configuration Options:</mark>***

<br>
<img src="\nr_embb\img\nr_embb_protocolfuncsplit2.png" width=100% height=100% />
<br>

---

#### User Plane Data Split in CA and DC

CA split the User Plane in MAC <mark>(Ideal backhaul necessary)</mark> while DC split the User Plane in PDCP layer.

<br>
<img src="\nr_embb\img\nr_embb_cadcdatasplit.png" width=100% height=100% />
<br>

---

#### User Plane QOS Framework

Refer [10]

In LTE, strict one-to-one mapping approach is being used for UP bearers.<br>
In NR, different QoS flows can be mapped with similar DRB. SDAP layer is introduced for this purpose. 

<br>
<img src="\nr_embb\img\nr_embb_qosflow.png" width=100% height=100% />
<br>

?> LTE: High E2E signaling overhead needed for bearer setup and release every time service start or end.

?> NR: No bearer setup in E2E is needed (Because no bearer). QoS flow is just an IP flow based on services. It will dynamically created and stopped based on user plane data transfer.

***<mark>NR vs LTE QOS Framework Differences</mark>***

| Parameter       | NR                             | LTE                           |
|-----------------|--------------------------------|-------------------------------|
| QoS Identifier  | 5G QoS Identifier - 5QI        | Quality Class Indicator - QCI |
| IP Flow         | QoS Flow                       | EPS Bearer                    |
| Flow Identifier | QoS Flow Identifier - QFI      | EPS Bearer Identity - EBI     |
| Reflective QoS  | Reflective QoS Indicator - RQI | N/A                           |

***<mark>Visualizing NR QoS Framework</mark>***

Refer [6] [8]

Representation of NR QoS Framework for every PDU Session.<br>
Network Slice will slice the network from core to radio based on service requirements.

<br>
<img src="\nr_embb\img\nr_embb_qosflow2.png" width=100% height=100% />
<br>

---

#### 5QI QOS Identifier

<mark>For GBR</mark> case, whenever data is transported across QoS Flow, it will be treated based on the 5QI parameters definition for both DL and UL. <br>
However, <mark>for Non-GBR</mark>, UE will use similar QoS treatment in UL based on DL 5QI parameters - RQI.<br>
No NAS signaling needed for both cases as 5QI parameters is embedded inside packet header.

<br>
<img src="\nr_embb\img\nr_embb_5qi.png" width=70% height=70% />
<br>

***<mark>User Plane 5QI Specifications - Table A for GBR and Non GBR</mark>***

Table A is designed for QoS requirements under services that based on GBR and Non-GBR. [11]

<br>
<img src="\nr_embb\img\nr_embb_5qitablea.png" width=100% height=100% />
<br>

Table version for easy copy:

| 5QI | Resource Type | Priority Level | Packet Delay    Budget (PDB) | Packet Error Loss Rate | Services                                         |
|-----|---------------|----------------|------------------------------|------------------------|--------------------------------------------------|
| 1   | GBR           | 2              | 100ms                        | 10^-2                  | Conversational Voice                             |
| 2   | GBR           | 4              | 150ms                        | 10^-3                  | Conversational Video                             |
| 3   | GBR           | 3              | 50ms                         | 10^-3                  | Real Time Gaming                                 |
| 4   | GBR           | 5              | 300ms                        | 10^-6                  | Non Conversational Video (Buffered Streaming)    |
| 65  | GBR           | 0.7            | 75ms                         | 10^-2                  | Mission Critical Push to Talk Voice (MCPTT)      |
| 66  | GBR           | 2              | 100ms                        | 10^-2                  | Non-Mission Critical Push to Talk Voice (MCPTT)  |
| 67  | GBR           | 1.5            | 100ms                        | 10^-3                  | Mission Critical Video                           |
| 75  | GBR           | 2.5            | 50ms                         | 10^-2                  | V2X Messages                                     |
| 5   | Non-GBR       | 1              | 100ms                        | 10^-6                  | IMS Signaling                                    |
| 6   | Non-GBR       | 6              | 300ms                        | 10^-6                  | Video (Buffered Streaming), TCP Based            |
| 7   | Non-GBR       | 7              | 100ms                        | 10^-3                  | Voice, Live Streaming, Interactive Gaming        |
| 8   | Non-GBR       | 8              | 300ms                        | 10^-6                  | Video (Buffered Streaming), TCP Based            |
| 9   | Non-GBR       | 9              | 300ms                        | 10^-6                  | Video (Buffered Streaming), TCP Based            |
| 69  | Non-GBR       | 0.5            | 60ms                         | 10^-6                  | Mission Critical Delay Sensitive Signaling       |
| 70  | Non-GBR       | 5.5            | 200ms                        | 10^-6                  | Mission Critical Data                            |
| 79  | Non-GBR       | 6.5            | 50ms                         | 10^-2                  | V2X Messages                                     |
| 80  | Non-GBR       | 6.8            | 10ms                         | 10^-6                  | Low Latency eMMB applications, Augmented Reality |

***<mark>User Plane 5QI Specifications - Table B for Delay Critical GBR</mark>***

Table B is designed for QoS requirements under services that based on GBR but delay critical. [11]

<br>
<img src="\nr_embb\img\nr_embb_5qitableb.png" width=100% height=100% />
<br>

Table version for easy copy:

| 5QI | Resource Type        | Priority Level | Packet Delay Budget (PDB) | Packet Error Loss Rate | Maximum Burst Size | Data Rate Averaging Window   | Services                                             |
|-----|----------------------|----------------|---------------------------|------------------------|--------------------|------------------------------|------------------------------------------------------|
| 82  | GBR (Delay Critical) | 1.9            | 10ms                      | 10^-4                  | 255 bytes          | 2s                           | Discrete Automation                                  |
| 83  | GBR (Delay Critical) | 2.2            | 10ms                      | 10^-4                  | 1358 bytes         | 2s                           | Discrete Automation                                  |
| 84  | GBR (Delay Critical) | 2.4            | 30ms                      | 10^-5                  | 1358 bytes         | 2s                           | Intelligent Transport System                         |
| 85  | GBR (Delay Critical) | 2.1            | 6ms                       | 10^-5                  | 255 bytes          | 2s                           | Electricity Distribution – High Volt, Remote Control |

Notes:

1. The Maximum Burst Size is the amount of data which the RAN is expected to deliver within the part of the PDB.
2. The Data Rate Averaging Window is the 'sliding window’ duration over which the GBR and MBR shall be calculated.
3. PDB or Packet Delay Budget is calculation between UE and PCEF (Element inside Core Getaway). PDB defines an upper bound.
4. Delay amount of assumption XXms value should be deducted from PCEF to gNB to derive PDB at radio interfaces, 3GPP Delay Assumptions for PCEF to gNB, Example: 20 ms delay (Average value), 10ms delay (gNB close to PCEF), 50ms delay (roaming with home routed), 10ms delay (mission critical services), etc etc.

***<mark>Reflective QoS Identifier (RQI) for UL in Non GBR</mark>***

For Non-GBR, UE will use similar QoS treatment in UL based on DL 5QI parameters - RQI.

<br>
<img src="\nr_embb\img\nr_embb_5qirqi.png" width=100% height=100% />
<br>

---

#### References

1. 3GPP TS 38.300
2. 3GPP TS 38.401
3. [Qualcomm](https://www.qualcomm.com/media/documents/files/whitepaper-making-5g-nr-a-reality.pdf)
4. 3GPP TS 38.804
5. Docomo - Unable to find link.
6. [5G NR by Sassan Ahmadi](https://www.sciencedirect.com/book/9780081022672/5g-nr)
7. Ericsson
8. Netmanias
9. 3GPP TR 38.801
10. Huawei - Can't find link
11. 3GPP TS 23.303