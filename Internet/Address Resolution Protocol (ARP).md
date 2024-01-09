Protocols related to these functionality:
### Address Resolution Protocol (ARP)
Goal: basically convert the IP address to a mac address 
- ip datagrams are assigned at the network layer but are **embedded** in PHY/MAC frames (in the SDU) to be TX on PHY
- it is then required to find the mac address of the next hop device from the IP address and we use **ARP**

Anytime a node has a IP there is :
- The sender has the IP address of the destination 
- the sender knows the IP address of the router that relays the datagram
- each router in the path finds the ip of the next router in it's **routing table**
![[Pasted image 20231222122513.png]]

# ARP in the same network 
ARP relies on the underlying Broadcasting capability of the lower layer
#### ARP request packet (broadcast)
Anytime a host or a router needs to find the link-layer address of another host or router in its network
**it sends an ARP request packet** 
- the packet includes the **link-layer** and **IP** address of the **sender** and the **IP** address of the **receiver** (the only address known)
- the query is **broadcast** over the link unsing the link-layer broadcast address (FF:FF:FF:FF:FF.FF)
- ![[Pasted image 20231222123828.png]]
![[Pasted image 20240108114223.png]]
#### ARP response (unicast)
- every host or router on the network receives and processes the ARP request packet , but only the **Intended receiver** recognizes it's IP address and send back an **ARP reply**
the response is **unicast**
![[Pasted image 20231222124717.png]]
![[Pasted image 20240108114243.png]]
## Multi-hop Arp
![[Pasted image 20240104172159.png]]


basically a very complicated way to say how the mac address is changed at each route if we don't actually Know wich is the destination mac address , we know it at each subnet we go
![[Pasted image 20240104181025.png]]![[Pasted image 20240104180957.png]]
![[Pasted image 20240104180917.png]]

![[Pasted image 20240104180900.png]]
# Proxy Arp

### Broadcast domain
since a local network can be partitioned in multiple Ip (aka sub netting) each sub networks is a separate broadcast domain Arp message cannot leave the sub network of the sender, 
For instance, if a device within Subnet A sends out an ARP request to resolve the MAC address of another device in Subnet A, that ARP message will only be broadcasted within Subnet A. It won't reach devices in other subnets because routers, which connect different subnets, typically do not forward broadcast traffic across subnet boundaries.
### Proxy Arp
![[Pasted image 20240104181902.png]]
- implemented in the router interconnecting the different sub networks 
- **Intercept** all ARP request for IP addresses of other subsets and replies with its own MAC address
- **Forward** all frames with its MAC address to the proper sub network
 
Proxy ARP is a networking technique where a device, typically a router, answers ARP (Address Resolution Protocol) requests on behalf of another device. This process involves the router intercepting ARP requests for IP addresses that are not within the local subnet and responding with its own MAC address.
