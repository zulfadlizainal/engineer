Topic: 5G NR<br>
Sub-Topic: eMBB<br>
Date Written: 2020/08/31<br>
Date Edited: 2022/06/01<br>

---

#### Initial Access: Synchronization Establishment

Synchronization is the fist step before establishing any connections between Tx & Rx.<br>
Sync happen in DL (SSB Sync) and UL (RACH Process), and this overall process is called <mark>Initial Access.</mark>

***<mark>High level Process:</mark>***

<br>
<img src="\nr_embb\img\nr_embb_initaccesssync.png" width=70% height=70% />
<br>

<br>
<img src="\nr_embb\img\nr_embb_initaccesssync2.png" width=70% height=70% />
<br>

***<mark>Types of Syncronization</mark>***

1. Sync Establishment for Initial Access.
2. Sync Maintenance for Idle & Connected.

<br>
<img src="\nr_embb\img\nr_embb_synctype.png" width=70% height=70% />
<br>

***<mark>Key Procedure:</mark>***

***1> 2-Step Synchronization Process (Similar with LTE)***

1. UE sync with PSS
2. UE sync with SSS (And acquire PCI)

***2> Time and Freq domain resources are pre-defined***

1. Different Time domain patterns for Sync Establishment (Initial Access) and Sync Maintenance (Idle & Connected)
2. SCS for SSB is dependent on frequency band

---

#### RRC State

Refer [1] [2] [3]

Overview of RRC State difference in Mobility Management based on implementation.

<br>
<img src="\nr_embb\img\nr_embb_rrcstate.png" width=100% height=100% />
<br>

---

#### References

1. [5G NR by Sassan Ahmadi](https://www.sciencedirect.com/book/9780081022672/5g-nr)
2. 3GPP TS 38.300
3. 3GPP TS 38.804