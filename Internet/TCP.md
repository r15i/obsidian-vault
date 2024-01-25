- connection-oriented
- reliable 


## Services 
1. Proces2process 
2. Full-duplex Communication:(data flow in both directions at the same time)
3. Multiplexing and Demultiplexing
4. Reliable Service
	   TCP uses a combination of GBN and SR
	- checksum for error detection
	- Byte numbers, sequence numbers, acknowledgment numbers:
	  1. **retransmission**
	  2. **reordering**
	  3. **cumulative** and **selective** acknoledgments
5. Connection-Oriented Service TCP, unlike UDP, is a connection-oriented protocolThere is a **logical** connection 

# TCP Packet Format
![[Pasted image 20240118123705.png]]
### Source e port (16bit)
#### Sequence Number(SN)(32bit)
defines the number assigned to the first byte of data contained in this segment 
- During connection establishment, the **initial sequence number(ISN)** is random 
- **segment without payload do not have SN**
- SN is the sequence number of any other segment  is the sequence number of the **prev_seg + num of bytes carried by the previous segment**
# Ack number(32-bit)
defines the next byte number expected by the receiver 
- if the receiver of the segment has received succesfully x from the other party returns x+1 as the ack num 
# HLEN(4BIT)
the number of 4-bytes (32 bit * HLEN) words in the TCP header

# Resv(6bit)
Reserved for future
# Window Size(16bit)
defines the available buffer space at the **receiver** in bytes
- normally referred as **receiving window** (rwnd)
- value **set by the receiver** 
- used in flow and congestion controll
# Flags (or Control)(6bit)
![[Pasted image 20240118125116.png]]
# Urgent Pointer(16bit)
points to urgent data, if there is
location of urgent data is obtained by 
UP +SN = LOCATION OF URGENT DATA IN THE PACKET

![[Pasted image 20240118130115.png]]
# Checksum(16bit)
![[Pasted image 20240118130332.png]]
the same as UDP but  **mandatory**
1. TCP header
2. TCP data
3. pseudoheader
   
   # Options
   ![[Pasted image 20240118130721.png]]
   up to 40 bytes of optional information in th TCP HEADER as:
   - EOP(end of operation) for padding
   - No operation: used to align the beginning of an option
   - **Maximum segment size** (MSS): define the maximum size of the segment to be used IS \[536,65535 byte\]
 - TO NOTE to avoid fragmentation in the IP layer (usually is MTU_SIZE-(IP/TCP) headers)
     
     
    
# TCP Connection 
![[Pasted image 20240118130754.png]]
- **Establish** the **connection-oriented** logical path between the source and destination

## Connection Establishment
#### Three-way Handshaking
1. **SYN** (client)
	 ![[Pasted image 20240118170949.png]]
	 **SYN  = 1** **synchronization** FLAG
	 random(ISN)
	- **SYN** segment carries no data
	- **SYN** consumes one sequence number
	- no **ACKn** no **rwnd** def
	![[Pasted image 20240118172959.png]]
2. **SYN + ACK** (server)
	   ![[Pasted image 20240118172229.png]]
	- **SYN + ACK** flag segment with ACK,SYN = 1
	- with a different ISN choosen by the server for **FULL-DUPLEX** communication
	- the server also send **ACK** the receipt of the **SYN** segment and displaying the next SN it expects to receive
	- Note that this segment **does not** contain an acknowledgment number.
	- **it also needs to reply with the **receive window** size for flow control **
  ![[Pasted image 20240118173020.png]]
3. ACK (client)
   - just an ACK with ACK = 1
   -  Contains **receive window** size  for the server
    ![[Pasted image 20240118173529.png]]
3.  ACK + piggy back  (client)
	the sender also sends some data:
	-  in this case the SN is changed on the number of bytes
	- in this case the communication starts immediately
![[Pasted image 20240118173702.png]]

## Time for connection Establishment
###### without Piggyback
- SYN +(SYN+ACK)+ACK (than data transfer)
- $T_{CE}=3\cdot(\tau_p+T_{tx})=3\cdot(\tau_p)$
###### with Piggyback
- SYN+(SYN+ACK)+ACK (transmission data already starts)
- $T_{CE}=2\cdot(\tau_p+T_{tx})=2\cdot(\tau_p)$ 
## Data transfer 
- After connection is established, **bidirectional data transfer** can start
![[Pasted image 20240118174344.png]]
## Connection Termination
## Three-way handshaking 
- **FIN** *consumens a sequence number*
- FIN +  ACK  TCP server 
- TCP clients sends ACK and closes the session in both direction 
![[Pasted image 20240118175650.png]]
## Four-way handshaking 
- FIN TCP client 
- TCP server receives **FIN** and replies with **ACK** 
  1.  TCP server keeps sending data
  2.  TCP CLIENTT CAN ONLY SEND ACKs with no payload
- TX completed $\rightarrow$  TCP server sends **FIN**  
- TCP client sends **ACK** and closes the connection 
![[Pasted image 20240118180039.png]]

# Flow control
similar to selective Repeat ARQ protocol but :
### Send Window
-  window size in SR is the number of packets, in **TCP is the number of bytes**
- The sending TCP can send segments as soon as it receives them from its process 
- The theoretical SR protocol use several timers for each packet sent, but the TCP protocol uses only **one timer**
![[Pasted image 20240118180604.png]]
### Receive Window (rwnd)
difference with TCP:
- TCP allows the receiving process to pull data as its own pace
- part of the allocated buffer at the receiver may be occupied by bytes that 
- rwnd = buffer size-number of waiting bytes to be pulled
- ACK is SR is selective , defining the uncorrupted packets that have been received. ACK in TCP is cumulative annuncing the next expected byte to receive
  ![[Pasted image 20240119110832.png]]
### Achieve flow control 
TCP forces the sender and the receiver to **adjust their window sizes** , although the size of the buffer is fixed 

cases:
- Receive Window Closes(buffer is filled up)
- Receive Window Opens(buffer is freed up, more bytes can be accepted)
- Send Window Closes (ACK is received and rwdn HAS BEED reduced)
- Send Window Opens(data has been delivered to the receiver's application)
- Send Window Shrinks(should be avoided)(ACK is received and rwdn has been very much reduced)

#### General rule 
#### Sender window
How many packets i can send over the channel 
#### Receiver window 
How many packets the receiver can accept

**The value of the sender window depends on the value of the receive window** 

### Example Flow Control
![[Pasted image 20240119112337.png]]
![[Pasted image 20240119112354.png]]
# Flow control Problems
#### Dead Lock Problem 
when the buffer on the receiver is full is necessary an ack to de freeze the transmission becuase of flow control
- When application at receiver side empties (at least) 1 MSS or half of the buffer size, receiver sends a DUPACK with rwnd >0 $\rightarrow$ **unfortunately... Ack is lost**
- Sender does not get the ack and hence cannot transmit new segments
![[Pasted image 20240119112831.png]]

**SOLUTION** Persist timer
- when rwnd=0(blocked sender) the sender starts a "persist" timer
- When persist timer elapses and no segment are received during this time, sender transmits a **probe** (if thereceiver is full it rejects the probe if not it will ack)
- Persist time management (exponential backoff) Doubles every time, max 60 s

# Tiny datagram 
issue that arises when the sending application creates data slowly 

- Small segments that reduces the efficiency of the operation 
**Solution** : **Nagle's algorithm**
- After sending the first segment, **The sending TCP accumulates data** in the buffer and waits until the receiving TCP sends an ACK or until enough data have filled the MSS, then TX
- Nagle's algorithms uses **speed of the application and speed of the netwok** in accout to transport data


# Silly Window Syndrome
Issure that arises when the receiving application consumes data slowly

### Delayed ACK
The ACK is not sent immediately, but only when there is a decent amount of space in receiver buffer
### Clark's algorithm 
Send an acknowledgment as soon as the data arrive, but annunce a window size of zero unil either there is enough space to accomodate a segment of MSS or until at least half of the receive buffer is empty


## Error Control
TCP is a reliable transport-layer protocol

**Error control** includes mechanism for:
- **detecting** and **resending** corrupted segments, resending lost segments
- **storing** out-of-order segments until missing segments arrive, and detecting and discarding **duplicated** segments

tools:
- checksum
- acknowledgment
- time-out

## retransmission
##### after RTO (retransmission time out)
The sending TCP maintains one **retransmission time-out (RTO)** for each connection.

When the timer matures, i.e., times out, TCP resends the segment in the front of the queue (the segment with the smallest sequence number) and restarts the timer.

- The value of RTO is dynamic in TCP and is updated based on the round-trip time (RTT) of segments.
##### after Duplicate ACK (Fast retransmission )
to expedite service throughout the Internet by allowing **senders** to -**re transmit** without waiting for a time out.
- most implementation after 3 dup Ack will retransmit the missing segment immediately (FAST RETRASMISSION)

## Lost segment example
![[Pasted image 20240119115131.png]]
## Fast retransmiossion
![[Pasted image 20240119115142.png]]
- **Text:** In which way does a TCP endpoint react to the third received duplicate ACK?
- ** It immediately retransmits the first non-ACKed segment, and restarts the RTO with the current value.**

# Congestion Control 
control the number of segments to transmit
using a **congestion window (cwnd)**
- wich defines **how many bytes can be transmitted before stopping to wait for ACKs** (very similar to sliding window in ARQ)
- The cwnd size is controlled by the congestion situation in the network 

**THE ACTUAL SIZE OF THE WINDOW IS THAN**
![[Pasted image 20240119115608.png]]
- when cwnd is full, new bytes can be transmitted only upon reception of ACK that confirms the reception
## Alogrithms for congestion
## slow Start (exponential 
Increase)
Start slow and increase rapidly to reach a good throughtput fast
- At connection set up, start cwnd = 1 MSS(maximum segment size) packets
- for each received ACK, **add 1 MSS** to the cwd :


**CWND** doubles at every RTT: this algo start slowly but grows **exponentially**

![[Pasted image 20240119120201.png]]


## Congestion avoidance(Linear (additive) Increase)
After a while increase slowly to prevent congestion 
- Slow starts quickly saturates the link
- The whole **windows** of segments is ACKed, add 1 MSS to the cwnd 
![[Pasted image 20240119120340.png]]

![[Pasted image 20240119120400.png]]

![[Pasted image 20240119120418.png]]
![[Pasted image 20240119120440.png]]
## Fast Recovery (Linear (additive) increase)
recover from minor congestion 
(optional in TCP old version)

It starts when **three duplicate ACKs arrive** wich is interpreted as light congestion 
- it increases the size of the congestion window when more duplicate ACK arrive
  ![[Pasted image 20240119120802.png]]


**THE VALUE OF THE SENDER WINDOW DEPENS ON THE VALUE OF THE RECEIVE WINDOW**
![[Pasted image 20240119120855.png]]


# TCP variants
![[Pasted image 20240118165228.png]]

## Tahoe
![[Pasted image 20240123192533.png]]
## Reno
![[Pasted image 20240123192505.png]]


## Reno 2 
![[Pasted image 20240123192518.png]]






![[Pasted image 20240118165326.png]]

