# End-to-End Latency {Delay}: $d_{e2e}$ \[s\]

The time taken to deliver a  complete  message to the intended receiver 
from the time the first bit is sent out from the source:
# $d_{e2e} = d_{proc} + d_{queue} + d_{trans} + d_{prop}$

### 1. Processing Delay  $d_{proc}$ : 
Time required to process a packet in a router or destination host
(REDUCED WITH ROUTING ALGORITHMS) 
### 2. Queuing Delay  $d_{queue}$ :    
Time a packet waits in input and output queues in a router
### 3. Transmission Delay $d_{trans}$ :
OR also known as $Tx$ tempo di trasmissione
 $d_{trans} = (Packet\,length)/(Transmission\,Rate)$
$d_{trans} = L/C$
### 4.  Propagation Delay $d_{proc}$ :
Fiscal time for the signal to get by the wire 
usually one of packet and expressed as $\tau$
### $d_{prop} = (Distance)/(Propagation\,speed)$


# Delay metrics in practice 
usually we approximate as 

![[Pasted image 20240108103309.png]]
## $d_{e2e} = d_{trans} + d_{prop}$ 
given usually $d_{queue},d_{proc}\approx 0$


# Jitter: J\[s\]
- Variation in the latency on a packet flow between two systems
![[Pasted image 20231128222608.png]]


# Round Trip Time (RTT) \[s\]:
RTT is the time taken by a **packet** sent by A to reach B and for the corresponding **acknowledgement packet (ACK)** to return to A

Ack usually are small hence the  processing, queue, and **propagation** time are often neglected

## $RTT = d_{proc-AB} +  d_{queue-AB} +d_{trans-AB} +d_{prop-AB}$ 
## 	    	$+ d_{proc-BA} +  d_{queue-BA} +d_{trans-BA} +d_{prop-BA}$
	
    	$=($ time to reach B $)+($ ACK back Time$)$

is like 2 end to end delay
## Note no **propagation** when we approximate
## $RTT_{min} = d_{trans-AB} + d_{prop-AB} + d_{prop-BA}$













