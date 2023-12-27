Handles the p2p communication between the hosts and the routers of the [[Frame]].
ROLE: It is respnsible for delivering a [[Frame]] from one node to the physically adjacent node over a link (hopefully in a reliable way)

### Frames can be transferred with  *different link protocols* over different links

![[Pasted image 20231201183354.png]]


## Servicies 
![[Pasted image 20231222115347.png]]
### Data Link Control (DLC)
#### Error Control
- **Error Correction** : Add enough redundacy bits to correct errors (FEC: FORWARD ERROR CORRECTION CODE)
- **Error Detection with retrasmission**: Add redundacy sufficient to detect errors, these are not **corrected** but retransmitted
#### Flow Control 
If the receiving node gets overwhelmed Flow control allows to feed back from the receiving node to the sending node to stop or slow down pushing pushing frames, to allow the receiving node to breathe
#### [[Framing]]
#### Medium Access Control (MAC)
- Random Access
- Controlled Access 
- Channelization 
## Protocols 
we have 3 kind of unique identifyers:
- Host Name
- Internet protocol (IP) address (Net layer)
- MAC Address (Data Link layer)
### MAC Address 
Defines a 48-bit DLL address usually written in **12 hexadecimal digits** divided by colons
![[Pasted image 20231222115913.png]]

Kinds of destination addresses:
- Multicast: second digit (A3:......) is ODD
- Unicast: second digit (A2:....)is EVEN
- Broadcast: all ones (FF:FF:FF:FF:FF:FF)

We need to have an automatic procedures to manage this correspondence between addresses and /or address assignement neet to be in place

Protocols related to these functionality:
### Address Resolution Protocol (ARP)
Goal: basically convert the IP address to a mac address 
- ip datagrams are ssigned at the network layer but are **embedded** in PHY/MAC frames (in the SDU) to be TX on PHY
- it is then required to find the mac address of the next hop device from the IP address and we use **ARP**


Anytime a node has a IP there is :
- The sender has the IP address of the destination 
- the sender knows the IP address of the router that relays the datagram
- each router in the path finds the ip of the next router in it's **routing table**
![[Pasted image 20231222122513.png]]
basically it says forward to this ip to reach this other ip 

ARP relies on the underlying Broadcasting capability of the lower layer
#### ARP request packet
Anytime a host or a router needs to find the link-layer address of another host or router in its network
**it sends an ARP request packet** 
- the packet includes the **link-layer** and **IP** address of the **sender** and the **IP** address of the **receiver** (the only address known)
- the query is **broadcast** over the link unsing the link-layer broadcast address (FF:FF:FF:FF:FF.FF)
- ![[Pasted image 20231222123828.png]]
#### ARP response
- every host or router on the network receives and processes the ARP request packet , but only the **Intended receiver** recognizes it's IP address and send back an **ARP reply**
the response is **unicast**
![[Pasted image 20231222124717.png]]

### Multi-hop
#### Broadcast domain 


- Reverse Arp 
- BootStrap Protocol (BOOTP)
- Dynamic Host Configuration Protocol(DHCP)




