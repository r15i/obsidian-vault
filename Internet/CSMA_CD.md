Variant of [[Carrier sense multiple access (CSMA)]] with collision detection 

# Collision detection 

if energy level consistent with frame transmission$\rightarrow$ **frame is ok** 

if abnormal energy level $\rightarrow$ **collsion**

handling of the collsion: 
- **abort transmission**
- send  a **jamming signal** to inform other stations

![[Pasted image 20240107173132.png]]



# Worst case scenarios
![[Pasted image 20240107173357.png]]![[Pasted image 20240107173457.png]]![[Pasted image 20240107173506.png]]

# Ethernet
- Implementation of [[CSMA_CD]] with **Retransmission in case of collision**
- **Connection less** (a frame is sent whenever ready) 
- No Flow control (sender can overwhelm receiver with frames)
- **NO ACK** (ARQ is not natively implemented at MAC layer for bit errors, if CRC fails, the frame is silently dropped by the receiver)
## Ethernet frame
IEEE 802.3 frame Size
![[Pasted image 20240107173942.png]]![[Pasted image 20240107174043.png]]

# Ethernet Implementations

![[Pasted image 20240107174143.png]]

## Performance 
![[Pasted image 20240107174258.png]]