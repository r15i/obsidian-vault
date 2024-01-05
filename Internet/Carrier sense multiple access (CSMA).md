IDEA: The chances of collision can be reduced if a station **senses** the medium before trying to use it:

- CSMA requires that each station first listen to the medium before sendimg ("listen before talk") 
- The possibility of collision still exist because of propagation delay $T_p$  (the probing in each node is not istant) 
- A station may sense the medium and find it idle, only because the first bit sent by another station has not yet beed received
 ![[Pasted image 20240105161809.png]]!
 
## Vulnerable Time
Time needed to propagate from one end of the medium to the other 
![[Pasted image 20240105161919.png]]
# Persistence Methods

1- Persistent 
- **Continuosly sense**: After the statin finds the line idle, it sends it 