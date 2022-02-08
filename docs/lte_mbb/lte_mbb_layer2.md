Topic: 4G LTE<br>
Sub-Topic: MBB<br>
Date Written: 2019/12/02<br>
Date Edited: 2022/02/08<br>

---

#### RLC Concept 

3 Types of RLC Modes: TM, AM, UM [1]

1. TM (Transparent Mode) 
2. UM (Unacknowledged Mode) 
3. AM (Acknowledged Mode) 

<br>
<img src="\lte_mbb\img\lte_mbb_rlc.png" width=100% height=100% />
<br>

How is RRC mapped to PHY and RLC layer (Sample as below): [1]

<br>
<img src="\lte_mbb\img\lte_mbb_rlcdl.png" width=100% height=100% />
<br>

This is how RLC interact between layers: [1]

<br>
<img src="\lte_mbb\img\lte_mbb_rlcul.png" width=100% height=100% />
<br>

---

#### RLC: TM, AM, UM

***TM (Transparent Mode)*** [1]

1. Simplest RLC Mode 
2. Transparent means: Contents go through this layer without Modification 
   - Not add/remove header 
   - Not split input data to multiple segment 
   - Not combine multiple input data to single data 
3. Only purpose for this mode: To buffer data. Data go in, keep the input data for certain amount of time or until next data come in. It will just discard if not transmitted within certain time frame. 

<br>
<img src="\lte_mbb\img\lte_mbb_rlctm.png" width=100% height=100% />
<br>

***UM (Unacknowledged Mode)*** [1]

1. UM means: Does not requires any reception response from other party. 
2. Response simple means ACK or NACK from other party. 
3. TM Mode also don’t need ACK/NACK, however UM mode adds its own header. 

Process (Tx Side): 

- Buffer 
- Split or Concatenate 
- Add Header 
- Sends to logical channel 

Process (Rx Side):

- Buffer
- Reorder 
- Remove Header 
- Reassembly 

<br>
<img src="\lte_mbb\img\lte_mbb_rlcum.png" width=100% height=100% />
<br>

Important UM parameters in rrcConnectionReconfiguration-r8:

| Information Element  | Description                                                                                                                                            |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| sn-FieldLength       | This parameter indicates the length of Sequence Number field of RLC-UM.                                                                                |
| t-Reordering         | This timer is used by the receiving side of an UM RLC entity and receiving UM RLC entity in order to detect loss of RLC PDUs at lower layer. Unit = ms |

***AM (Acknowledged Mode)*** [1]

1. It requires ACK/NACK from the other party! 
2. If need ACK/NACK from every transmission, then overhead is too big? YES! 
3. When RLC is sent, a copy will be sent to buffer.  
4. In case ACK is received, data in buffer will be discarded. 
5. In case NACK is received, data in buffer will be sent again (Retransmission). 

<br>
<img src="\lte_mbb\img\lte_mbb_rlcam.png" width=100% height=100% />
<br>

<br>
<img src="\lte_mbb\img\lte_mbb_rlcam2.png" width=100% height=100% />
<br>

Important UM parameters in rrcConnectionReconfiguration-r8:

| Information Element  | Description                                                                                                                                             |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| t-PollRetransmit     | This timer is used by the transmitting side of an AM RLC entity in order to retransmit a poll. Unit = ms                                                |
| pollPDU              | In most typical condition, the poll bit is inserted after the number transmitted RLC PDU gets larger than this value. See 36.322 5.2.2.1                |
| pollByte             | In most typical condition, the poll bit is inserted after the transmited RLC data is greater than (this value x 1000 bytes). See 36.322 5.2.2.1         |
| maxRetxThreshold     |                                                                                                                                                         |
| t-Reordering         | This timer is used by the receiving side of an AM RLC entity and receiving AM RLC entity in order to detect loss of RLC PDUs at lower layer. Unit = ms  |
| t-StatusProhibit     | This timer is used by the receiving side of an AM RLC entity in order to prohibit transmission of a STATUS PDU. Unit = ms                               |
 
---

#### RLC: ARQ in AM

This mechanism involves two main part as follows: [1]

1. Transmitter side: Poll Request 
2. Receiver side: Status Report carrying ACK, NACK etc 

Polling parameter in rrcConnectionSetup-r8: [1]

| Information Element  | Description                                                                                                                                     |
|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| t-PollRetransmit     | This timer is used by the transmitting side of an AM RLC entity in order to retransmit a poll. Unit = ms                                        |
| pollPDU              | In most typical condition, the poll bit is inserted after the number transmitted RLC PDU gets larger than this value. See 36.322 5.2.2.1        |
| pollByte             | In most typical condition, the poll bit is inserted after the transmited RLC data is greater than (this value x 1000 bytes). See 36.322 5.2.2.1 |

Case 1: Basic Poll Handling 

<br>
<img src="\lte_mbb\img\lte_mbb_rlcamarq.png" width=100% height=100% />
<br>

Case 2: Poll bit and RLC ACK operates by sequence number 

<br>
<img src="\lte_mbb\img\lte_mbb_rlcamarq2.png" width=100% height=100% />
<br>

Case 3: Retransmission due to t-PollRetransmit timeout

<br>
<img src="\lte_mbb\img\lte_mbb_rlcamarq3.png" width=100% height=100% />
<br>

Case 4: Retransmission due to RLC NACK 

<br>
<img src="\lte_mbb\img\lte_mbb_rlcamarq4.png" width=100% height=100% />
<br>

Case 5: RLF due to Max Retx Fail 

<br>
<img src="\lte_mbb\img\lte_mbb_rlcamarq5.png" width=100% height=100% />
<br>

---

#### References

1. [Sharetechnote](https://www.sharetechnote.com/html/RLC_LTE.html)