Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/08/31<br>
Date Edited: 2022/03/24<br>

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
<img src="\nr_embb\img\nr_embb_gnbarchitecture2.png" width=100% height=100% />
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

#### References

1. 3GPP TS 38.300
2. 3GPP TS 38.401
3. [Qualcomm](https://www.qualcomm.com/media/documents/files/whitepaper-making-5g-nr-a-reality.pdf)