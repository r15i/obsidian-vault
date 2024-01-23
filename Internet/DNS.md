is an application layer service [[Application Layer]]

![[Pasted image 20240123192328.png]]
 ![[Pasted image 20240123191606.png]] 
exist 13 DNS root servers in the world
![[Pasted image 20240123191658.png]]

but each ISP has one **local Name Server** (local DNS)
the **default name server**
![[Pasted image 20240123191841.png]]


- Mapping a name to an address is called **name-address resolution** 
- A host that needs to map a name to an address is called **resolver**
## DNS Caching
Once (any ) name server learns a  mapping it **caches** it 
- informs the client that the reference is **unauthoritative**
- Cache entries timeout(disappear) after some time to avoid sending an outdated mapping to the client - TTL IS ADDED
![[Pasted image 20240123192149.png]]

![[Pasted image 20240123192214.png]]