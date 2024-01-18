Routing consist of all the procedures that make possible to determine a path from a point to another one.
- The network layer is responsible for finding the best (**route**)
- Using **routing protocols** saved in a **forwarding table** wich allows

## Route net model 
to find the best route , internet is modeled as a **weighted graph** wich **cost** of each edeges can be expressed as:
- [[Delay metrics#Round Trip Time (RTT) [s ] |RTT]]
- bitrate
- PRR
- ...
  
  The best route from a source router to a destination is the **least-cost route (LCR)** 

## Routing Algorithms
the LCR can be found with many different kind of algo
Outcome of the algo: **a sequence of connected vertexes starting from Source and ending in any vertex V so that the sum of the link distance is the LEAST COST PATH  (LCP )
### Distance-Vector
- decentralized
- Each node exchange global information at **local level** (only with its neighbouring nodes)
- The **least-cost paths** are computed in an iterative, distributed manner (Bellman-Ford's Algorithm)
(Bellman-Ford's Algorithm)
### Link-State

- centralized
- requires **global knowledge** of the topology
- each node exchange local information at **global level** (with all the other nodes)
- Computes **least-cost paths** on the whole network graph (DIJKSTRA)

Dijkstra's Algorithm 

### Path-Vector
Spanning Trees
- unlike link-state and distance-vector the goal of routing is **ONLY** **reachabilty** to allow the packet to reach its destination more efficiently without assigning cost to the route 


# Routing Protocols
routing protocol implements a [[Routing#Routing Algorithms|Routing Algorithms]]

![[Pasted image 20240115171829.png]]
# Hierarchical routing 
Routing **CANNOT** be done with a single protocol 
- **Scalability**:To avoid explosion of routing tables a hierarchical partition of the routing tables 
- **Administrative autonomy**: A company/ISP wants (and needs) to manage it's routers inside its own network (ISP does not want to handle traffic not from his users)

we need to consider each **ISP** as an autonomous system (AS).
![[Pasted image 20240115180039.png]]
- System composed of a set of interconnected Routers and using a standard routing protocol to connect to routers in other AS
### Interior Gateway Protocol(IGP) or Intra-As routing 
usually managed by only one ISP, The interior Gateways (IGs) use one routing algorithm, wich may be different for each AS


### Exterior Gateway Protocol(EGP) or inter-As routing (between AS TO ANOTHER AS)

## **Border Gateways(BGs)** 
provide interconnection between ASs.
The BGs notify the IGs og their own AS ABOUT 
![[Pasted image 20240115180326.png]]

## Routing performance
![[Pasted image 20240115180359.png]]

### ROUTING TABLE 
- Essentially tell the router wich is the next hop (and we are sure that the overally route is the LCR)
- **Format** of the packets that are used to find the routing table 
![[Pasted image 20240115180608.png]]


## Forwarding 
Places the packet on the route to it's destination 

Although the IP protocol was originally designed as a connection less protocol(datagram approach), today the tendecy is to use a **connection-oriented** protocol (virtual circuit)

## Direct Forwarding
Destination directly reachable 
1. B want to send pack $\rightarrow$ A
2. B compares the NetID to the one in the net
3. B checks MAC address for IP-A in **ARP table**
4. IP-layer entity passes the datagram to lower entityes
   
## Indirect Forwarding 
 1. B want to send a datagram to a different netid
 2. B compares the NetID of its own and they are **not** the same
 3. B needs to forward the datagram to an **edge router** (usually by default gateway )
 4. B binds the MAC of the default gateway in the arp table and passes the datagram to mac layer
 5. Mac Layer forges the mac fram and forward it to router
 6. In the Default gateway 
    ![[Pasted image 20240116104652.png]]

 NOTE :
 the sender needs to know it's default gateway
 and if not should be able to do a DHCPACK wich containts :
 - Netmask
 - Default Gateway
 - Dns server
 

## Forwarding with Netmask
Configuration of a network interface **requires both IP address and netmask** 
- **routing table**: contains, destination network IP addresses and associated netmask, together with the next hop
![[Pasted image 20240116105058.png]]
- **interface configuration**: contains the list of hops that can be reached (and the MTU)
![[Pasted image 20240116105137.png]]

to obtain the NetID the router perform an AND operation between the ip of the interface and the netmask

# Forwarding algo 


first uses   
[[#Direct Forwarding]] $\rightarrow$  **which mainly uses the interface configuration** 
   - IF {IP(dst) AND NM(x)}= {IP(x) AND NM(x)} THEN $\rightarrow$ direct forwarding through interface x  (substantially check for the IP address in the table )
   - else another interface 
   - if not [[#Indirect Forwarding]]
![[Pasted image 20240116105836.png]]
[[#Indirect Forwarding]] $\rightarrow$ **Use routing table**
- **Longest mask matching** : inspect the routing table from the entry corresponding the **LONGEST NETMASK** (and is not in order)
- **Default gateway**: last row shall have all 0s in the netmask (matches with any address)
![[Pasted image 20240116110103.png]]

## Routing Example 
![[Pasted image 20240116110126.png]]

## Blurred line 
not in the interface , in arp, but still in the same network cuz strange number of bit in netmask
![[Pasted image 20240116111959.png]]

![[Pasted image 20240116112010.png]]

![[Pasted image 20240116112028.png]]









  