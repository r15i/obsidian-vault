## ARQ

1. *Acknowledgment (ACK)*: the receiver tells the sender when a frame (packet) is correctly received:
- *Selective acknowledgment (SACK)*: it specifies the set of frames correctly receives 
- *Cumulative acknowledgment(ACKi)*: it means that frame  i has been correctly received and all the previous
2. *Negative acknowledgment (NACK)*: the receiver **refuse to accept the frame now**
![[Pasted image 20240108115916.png]]
## Param
$C$     : bit rate at the LL \[bit/s\]
$F$     : (H+I) frame size \[bits\]
H     : header size \[bits\]
I       : payload size \[bits\]
$t_f$     : Frame TX time
$t_I$     : Frame TX time of only the DATA
$t_T$     : total frame TX time
$\eta$      : efficiency
$\tau_p$     : propagation delay
$t_A$     : ACK TX time (single TX)
$t_G$     : time to TX and ACK a packet ([[Delay metrics#Round Trip Time (RTT) [s ]|RTT]])
$E[t_T]$: total frame TX with succesful TX and retransmission


