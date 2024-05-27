we have Internet protocol 4 (Ipv4) and is responsible for:
- Packetizing 
- forwarding 
- delivery the packet at network layer
## IPv4 address
- 32-bit address 
- **unique** : each one defines one and only one connection to the internet(as single net)
- **universal** : the addressing system **must be accepted by any host** connected to the internet
- Note is considered IP address only the ones that actually idenitify a machine 
## Hierarchy
![[Pasted image 20240108200939.png]] 

The ip is divided into **two parts**
- **NetID**, called the **prefix**(**N** bit), defines the network(**NetID**)
- **HostID**, called the Suffix defines the host 

## Addressing 
### Classfull address 
-  Fixed Length (now obsolete)
	  Fixed-length prefix $\rightarrow$ three fixed-length prefixes were used n = 8,16,24	![[Pasted image 20240108205953.png]]
	Class A,B,C,D and E. This scheme is referred as **classfull addressing**
	![[Pasted image 20240108210231.png]]
	## Special Addresses 
	- Address only with the HostID with all zeros (only used in the routing table) 
	- Direct Broadcast address HostID with all ones put to 255
### Classless : Variable Length
Short term solution to the lack of ip , allows to **freely place the boundary** between NetId and HostId in the 32 bit IP address field
ADDRESSES:
- split large blocks in smaller ones $\rightarrow$ **subnetting**
- aggregate smaller blocks in larger ones $\rightarrow$ **supernetting**
- Another short-term solution is via **private addresses** (intranets and NAT)
Make it possible to **freely place** the boundary between NetId and HostId in the 32 bit IP address field
### Rappresentation of addresses
1.   Classless InterDomain Routing (CIDR)
    format **AddressOfanIPhost/n** with n the number of bit of the **NetHostID**
2. Netmask: All the bits of the **NetHostID** id are set to 1 
## Calculation 
Calculation of netadd netmask 
![[Pasted image 20240108212341.png]]
![[Pasted image 20240108212549.png]]

## Internet Corporation for Assigned Names and Numbers (ICANN)
[[Internet Corporation for Assigned Names and Numbers (ICANN)|ICANN]] EXERCISE FOR THE EXAM 









