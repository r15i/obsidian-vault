# IDEA: 
## The chances of collision can be reduced if a station **senses** the medium before trying to use it:

- CSMA requires that each station first listen to the medium before sendimg ("listen before talk") 
- The possibility of collision still exist because of propagation delay $T_p$  (the probing in each node is not istant) 
- A station may sense the medium and find it idle, only because the first bit sent by another station has not yet beed received
 ![[Pasted image 20240105161809.png]]!
 
## Vulnerable Time
Time needed to propagate from one end of the medium to the other 
![[Pasted image 20240105161919.png]]
# Persistence Methods

## 1-persistent
- **Persistent Continuosly sense**: After the statin finds the line idle, it sends its frame immediately (with probability 1). 
- **HIGH chance of collision** more stations may find the line idle and send immediately

![[Pasted image 20240107170937.png]]
## Non-presistent
- **Sense 1 time** if the line is idle, send immediately, elese if is busy wait a **backoff** and then sense again
- **Reduce efficency** because the medium remains idle
- **Reduce chance of collision**
## p-Persistent
- if line is idle:
	1. with probability $p$, send the frame
	2. with probability $q=1-p$ , wait for the next time slot and check the line again
			a. if the line is idle go to 1.
			b. if the line is busy, act as if a collision has occurred and use the **backoff procedure** (binary exponential backoff)
	![[Pasted image 20240107171837.png]]

- Channel has time slots with a slot duration $\geq$ maximum $T_p$ 
- Reduce both **chance of collision** and **improve efficiency**


# Performance Throughput 
![[Pasted image 20240107172038.png]]


# Variants

- [[CSMA_CD]] : Carrier sense multiple access with **collision detection**

- [[CSMA_CA]] : Carrier sense multiple access with **collision avoidance**