is an application layer service [[Application Layer]]

![[Pasted image 20240123192328.png]]
 ![[Pasted image 20240123191606.png]] 
## Distribution of Name space
exist 13 DNS root servers in the world but each **ISP** has one **Local Name Server (Local DNS)**
![[Pasted image 20240123191658.png]]

## DNS Resolution
- host makes a DNS query
- local DNS act (if not cached) as a proxy and forwards the query into hierarchi
- the IP address of the local DNS name server MUST be known to all local hosts
-  the query is sent to a **top-level-domain server**
- if the server does not know the name-address mapping it sends the request to the local DNS server in next level
- local DNS contacts destination (also caches it)
- The ip address is now sent back to the top-level DNS server, the root server, the ISP DNS SERVER, AND BACK TO THE HOST
  ![[Pasted image 20240124130353.png]]


**UDP** is typically considered (short and efficient messages)
mapping a name to a IP is $\rightarrow$ **name-address resolution**
A host that needs to map a name to a address $\rightarrow$ **resolver**
## DNS ITERATIVE Resolution
each server that does not know the mapping **equally sends the ip address of the next server back to the one that requested it** (as ask this other **guy**)
![[Pasted image 20240124130616.png]]
## DNS Caching
Once (any ) name server learns a  mapping it **caches** it 
- informs the client that the reference is **unauthoritative**
- Cache entries timeout(disappear) after some time to avoid sending an outdated mapping to the client - TTL IS ADDED
![[Pasted image 20240123192149.png]]

![[Pasted image 20240123192214.png]]