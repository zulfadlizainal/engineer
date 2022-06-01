Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/08/31<br>
Date Edited: 2022/03/29<br>

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