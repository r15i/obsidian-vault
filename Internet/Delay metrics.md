

## End-to-End Latency {Delay}: $d_{e2e}$ \[s\]
The time taken to deliver a  complete  message to the intended receiver 
from the time the first bit is sent out from the source:
### $d_{e2e} = d_{proc} + d_{queue} + d_{trans} + d_{prop}$

#### Processing Delay  $d_{proc}$ : 
Time required to process a packet in a router or destination host
(REDUCED WITH ROUTING ALGORITHMS) 

#### Queuing Delay  $d_{queue}$ :    
Time a packet waits in input and output queues in a router

#### Transmission Delay $d_{trans}$ :
$d_{trans} = (Packet\,length)/(Transmission\,Rate)$

#### Propagation Delay $d_{proc}$ :
Fiscal time for the signal to get by the wire 
$d_{prop} = (Distance)/(Propagation\,speed)$

## Delay metrics in practice 
$d_{e2e} = d_{trans} + d_{prop}$
given processing time and processing queue are around 0 

## Jitter: J\[s\]
- Variation in the latency on a packet flow between two systems
![[Pasted image 20231128222608.png]]

## Round Trip Time (RTT) \[s\]:

RTT is the time taken by a **packet** sent by A to reach B and for the corresponding **acknowledgement packet (ACK)** to return to A

$RTT = d_{proc-AB} +  d_{queue-AB} +d_{trans-AB} +d_{prop-AB}$
		$+ d_{proc-BA} +  d_{queue-BA} +d_{trans-BA} +d_{prop-BA}$
$RTT_{min} = d_{trans-AB} + d_{prop-AB} + d_{prop-BA}$













