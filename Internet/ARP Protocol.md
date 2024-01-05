
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




# Arp i the same network 
ARP relies on the underlying Broadcasting capability of the lower layer
#### ARP request packet (broadcast)
Anytime a host or a router needs to find the link-layer address of another host or router in its network
**it sends an ARP request packet** 
- the packet includes the **link-layer** and **IP** address of the **sender** and the **IP** address of the **receiver** (the only address known)
- the query is **broadcast** over the link unsing the link-layer broadcast address (FF:FF:FF:FF:FF.FF)
- ![[Pasted image 20231222123828.png]]
#### ARP response (unicast)
- every host or router on the network receives and processes the ARP request packet , but only the **Intended receiver** recognizes it's IP address and send back an **ARP reply**
the response is **unicast**
![[Pasted image 20231222124717.png]]

## Multi-hop Arp
![[Pasted image 20240104172159.png]]


basically a very complicated way to say how the mac address is changed at each route if we don't actually now wich is the desitination mac address 
![[Pasted image 20240104181025.png]]![[Pasted image 20240104180957.png]]
![[Pasted image 20240104180917.png]]

![[Pasted image 20240104180900.png]]