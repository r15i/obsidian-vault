TERMS
1. *Acknowledgment (ACK)*: the receiver tells the sender when a frame (packet) is correctly received:
- *Selective acknowledgmet (SACK)*: it specifies the set of frames correctly receives 
- *Comulative acknowledgment(ACKi)*: it means that frame  i has beed correclty received and all the previous
2. *Negative acknowledgment (NACK)*: the receiver **refuese to accept the frame now**

![[Pasted image 20240105134103.png]]

# Arq
![[Pasted image 20240104184157.png]]

If i don't receive an ack i retransmit the packet until the sender receives an ACK or exceeds a number of re-transmission

## Requirements
- Accuracy : Packets have to delivered to layer N+1 AT THE RECEIVER SIDE  without errors and once and only once (no duplicated)
- Efficienty: Capacity loss due to useless re-trasmission and time waste when waiting for packets or ACK has to be avoided 
##### Problems
- Duplicate packets $\rightarrow$ this is against the requirement of accuracy
	    without a sequence number SN the packets can be mixed up
- Deadlock problem $\rightarrow$ this is against the requirement of efficiency 
		essentially without an **ACK time-out** the sender can be left waiting because the receiver without receiving the entire frame does not produce an ack 
# Types of ARQ

### Stop and Wait ARQ (SW-ARQ)
Simplest form of Arq
- **one frame at a time** 
- waits of ACK
- transmit or re transmit 
![[Pasted image 20240104185655.png]]

Solves duplicate Ack with sequence numbers(SN) and acknowledgment numbers:
- Acknowledgment numbers always announce the sequence of the new packet expected by the receiver (a binary switching at each packet) in the ack
- the SN number serves as an identifier for received packes as such to not have duplicates in the case that an ack is lost but the packet is actually received
![[Pasted image 20240105133854.png]]
## Model
![[Pasted image 20240105133936.png]]
![[Pasted image 20240105134005.png]]
![[Pasted image 20240105134200.png]]
## Problem of SW-ARQ
Allows the transmission of only **ONE FRAME** at a time reducing the efficiency

# Sliding windows ARQ
Solvese the problems of transmission of SW-ARQ with 
### Pipeling:
Tx multiple unacknowledged frames back-to-back
the pipelining limit/size depends on the [[Pipe Capacity metrics#Bandwidth-Delay Product (BDP) [bits ] [pcks  |BDP]]

## Sliding window IDEA


## Sender
![[Pasted image 20240105143302.png]]
the sender is provided with a **sending window**  of size N as $[SN_{min},SN_{max}]$
$SN_{min}$ is the first unacknoledged packet
$SN_{nxt}$ is the next packet that can be sent
$SN_{max}$ of the last packet that can be sent within the sending window

$[SN_{min}+1,SN_{nxt}]$ total number of in-flight packets **packets that have beed sent but not ACKed ($\leq N$) $\rightarrow$  Buffered by the sender

$[SN_{min}+1,SN_{max}]=N=$ sending window size = max number of in-flight packets**

## Receiver
![[Pasted image 20240105145244.png]]
- RECEIVER is provided with a **receiving window** of size M
- $[RN_{min}+1,RN_{max}+M-1]$: acceptable packets at the receiver
- $RN_{min} = SN$ of the next expected packet (in-order)
- $M =$ maximum number of packets that can be buffered in sequence(without gaps) 

### Update the window
### on sender
![[Pasted image 20240105145950.png]]
- if we receive $Ack(n)$ with $SN_{min}<n<SN_{max}$ the sendimg window is slid forward setting a new $SN_{min} = n$ (**comulative ACK**) and $SN_{max} = SN_{min} + N-1$
### on receiver
arrives $SN = x$  
- if $x>RN_{min}$ packed is buffered
- if $x=RN_{min}$ the receiver set $RN_{min}$ = $SN$ of the next missing packet in the sequence of received packets and it delivers to the upper layer the packets with $SN$s up to the new $RN_{min}$ 
- Receiver sends $ACK(RN_{min})$ (the ACK of the next is-order packet to be received)
### Problems of Sliding window
What happens if a frame of the sequence is corrupted?
- a lot of frames arrive at the receiver before the sender realizes it 
- the receiver discards the corrupted frame and what does it do with the next?

### GO-BACK-N (GBN)
- receiver : discards all the out-of -order packets
- sender: When a timeout occurs it transmit again all the frames from the first unacknowldeged frame on 
 ![[Pasted image 20240105153423.png]]

#### Countiuos transmission 
requires that ACK relative to one in-flight packet is received while the transmitter **is still transmitting** (one of the N packets in the previous window)
$N * t_F \geq RTT$ 
![[Pasted image 20240105152640.png]]

### Selective Repeat (SR) 
- receiver: it accepts also the out-of-order packets but it does **NOT** deliver them to the upper layer unitl it has received all the missing ones
- sender: When a timeout occurs, it transmits again just the first unacknowledged frame
![[Pasted image 20240105153406.png]] 

![[Pasted image 20240105153543.png]]
![[Pasted image 20240105153556.png]]