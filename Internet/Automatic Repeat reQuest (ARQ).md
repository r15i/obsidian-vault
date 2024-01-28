[[Dictionary#ARQ|Dictionary ARQ ]]

Error Control  System at [[Data Link Control (DLC)]] of [[Data Link layer(DLL)]] level

![[Pasted image 20240104184157.png]]
If i don't receive an ACK i retransmit the packet until the sender receives an ACK or exceeds a number of re-transmission.
## Requirements
- Accuracy : Packets have to delivered to layer N+1 AT THE RECEIVER SIDE  without errors and once and only once (no duplicated)
- Efficiency: Capacity loss due to useless re-transmission and time waste when waiting for packets or ACK has to be avoided 
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
![[Pasted image 20240108144534.png]]
## Total frame transmission time

$\tau_p$ the propoagation delay
$t_F$ frame tx time 
$t_A$ ACK TX time (single TX)

$t_G$ = $t_f+\tau_p+t_A+\tau_p$ total transmission (without delay)

we need to account for the retransmission in case packets are not received we model this possible retransmission as a geometric random variable 
$E[X] = \frac{p}{1-p}$ **number of failures before first success (ACK)**

**Total frame TX time (successful TX + RE TRANSMISSION)**
$E[t_T] =t_G + E[x]t_g = t_f+\frac{p}{1-p}t_g=\frac{t_f+2\tau_p+t_A}{1-p}$
    
# Approximation for single bit
$p = 1-(1-P_{bit})^F\approx FP_{bit}$

## Utilization factor
$t_f$ : Frame TX time
$\rho = \frac{t_f}{E[t_T]}=\frac{t_f(1-p)}{t_f+2\tau_p+t_A} = \frac{t_f(1-p)}{t_G} = F\frac{1-p}{F+A+2C\tau_p}$

## Efficiency
$F$ :frame size
$I$ : payload size
$\eta = \frac{t_I}{E[T_t]}=\frac{t_F}{E[t_T]}\frac{t_I}{t_F}=\rho\frac{t_I}{t_F}=\rho\frac{\frac{I}{C}}{\frac{F}{C}}=\rho\frac{I}{F} = I\frac{1-p}{F+A+2C\tau_p}$


- To note that Efficiency and Utilization factor share the same formula but with the whole $F$ for $\rho$ and $I$ for $\eta$ 

- also keep in mind that using the approximation for $P_{bit}$ 
	$\eta \approx \frac{I(1-FP_{bit})}{F+A+2C\tau_p}$
## Problem of SW-ARQ
Allows the transmission of only **ONE FRAME** at a time reducing the efficiency

# Sliding windows ARQ
Solves the problems of transmission of SW-ARQ with 
### Pipeling:
TX multiple unacknowledged frames back-to-back
the pipelining limit/size depends on the [[Pipe Capacity metrics#Bandwidth-Delay Product (BDP) [bits ] [pcks  |BDP]]
## Sliding window 
## Sender
![[Pasted image 20240105143302.png]]
the sender is provided with a **sending window**  of size N as $[SN_{min},SN_{max}]$
$SN_{min}$ is the first unacknowledged packet
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

## Update the window
#### on Sender
![[Pasted image 20240105145950.png]]
- if we receive an $ACK(n)$ with n in the window $[SN_{min}SN_{max}]$ the window is slid forward setting $SN_{min} = n$ wich actually mean i have **ACKNOWLEDGED**  those packet (**comulative ACK**) and $SN_{max} = SN_{MIN}+ N -1$ 
- ![[Immagine WhatsApp 2024-01-25 ore 10.39.38_58f19fd9.jpg]]
#### on Receiver
when a packet arrives with $SN = x$  from the lower level 
- if $x>RN_{min}$ packed is buffered
- if $x=RN_{min}$ the receiver set $RN_{min}$ = $SN$ of the next missing packet in the sequence of received packets and it delivers to the upper layer the packets with $SN$s up to the new $RN_{min}$ 
- Receiver sends $ACK(RN_{min})$ (the ACK of the next is-order packet to be received)
## Problems of Sliding window
What happens if a frame of the sequence is corrupted?

- a lot of frames arrive at the receiver before the sender realizes it 
- what to do with the remaining frames if one is currupted

# GO-BACK-N (GBN)
![[Pasted image 20240108162149.png]]

- receiver : **discards all the out-of-order packets**
- sender: **When a timeout occurs it transmit again all the frames from the first unacknowledged frame on**

- efficient($\eta=1$)  in absence of channel errors(p=0),and works with links with large pipe capacities
- Inefficient in presence of errors as some packets are needlessly re transmitted
![[Pasted image 20240108162220.png]]
#### Continuos transmission
We want to choose $N$ large enough to allow **continuous transmission** while waiting for an ACK for the first packet of the window: 
- $N\geq t_G/t_F$ 
- $N*t_F\geq RTT$
with $RTT=t_F+2\tau_p$
essentially we want that the ack falls in the first ack of each window falls in the time of RTT wich means we don't have stopped sending packet of the same frame
![[Pasted image 20240108163546.png]]

## Total frame transmission time
$t_f$ frame TX TIME 
$t_A$ ACK TX time (single TX)

the **timeout** should be set such that $t_0\geq Nt_f$
$t_G = t_F+\tau_p + t_A+\tau_p$ 

$E[t_T] =t_f + E[X]Nt_f = t_f+\frac{p}{1-p}Nt_f$

$Nt_f$ : represent the time taken by the re transmission of any given packet since when an error occurs the entire window of N packets must be re transmitted
the last transmission of the packet only takes t_f seconds since it is successful
## Utilization factor
$\rho = \frac{t_f}{E[t_T]}=\frac{t_f(1-p)}{(N-1)(pt_f+t_f)}=\frac{(1-p)}{(N-1)(p+1)}$
## Efficiency
$\eta = \frac{t_I}{E[T_t]}= \frac{\rho I}{F}= I\frac{1-p}{F[(N-1)(p+1)]}$
#### Countiuos transmission 
requires that ACK relative to one in-flight packet is received while the transmitter **is still transmitting** (one of the N packets in the previous window)
$N * t_F \geq RTT$ 
![[Pasted image 20240105152640.png]]
### Selective Repeat (SR) 
![[Pasted image 20240108170250.png]]
- Same window size TX and RX (**M=N**)
- receiver: it accepts also the **out-of-order** packets but it does **NOT** deliver them to the upper layer until it has received a set of consecutive ones
- sender: When a timeout occurs, it transmits again just the first unacknowledged frame


- In absence of channel error(p=0) there is no differece between GBN-ARQ AND SR-ARQ
- for $N>1$ and $p>0$ , SR has higher throughput than GBN since we have to retransmit less packets
## Total frame transmission time
$t_f$ time taken by the re transmission of any given packet is $t_f$ since we don't re transmit the **whole window**

$E[t_T] =t_f + E[X]t_f = t_f+\frac{p}{1-p}t_f$

## Utilization factor
$\rho = \frac{t_f}{E[t_T]}=\frac{t_f(1-p)}{t_f}=1-p$

## ARQ Comparision

![[Pasted image 20240105153556.png]]

- ARQ performance generally depends on pipe capacity
- ARQ SR always has the best performance
- ARQ S&W is the simplest and still performs optimally when the pipe capacity is close to one, as in p2p connection (**S&W is very common at DLL**)
- ARQ mechanism are also used at other layers 
- For sliding window protocols 
	**The optimal size of the transmit window is equal to the pipe capacity** 
-
![[Pasted image 20240105153543.png]]