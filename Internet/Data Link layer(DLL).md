Handles the p2p communication between the hosts and the routers of the [[Frame]].
ROLE: It is respnsible for delivering a [[Frame]] from one node to the physically adjacent node over a link (hopefully in a reliable way)
# Servicies 
![[Pasted image 20231222115347.png]]
Servicies offered by the Datalink layer falls in 2 categories:
- [[Data Link Control (DLC)]] :  mainly in charge of the flow of data in the channel 
- [[Medium Access Control (MAC)]] : mainly in charge of the access/identification 

## Protocols 
The dll layer have a lot of protocols that can be used
![[Pasted image 20231201183354.png]]
# MAC Address 
Identifyer at DLL of the machine 
Defines a 48-bit DLL address usually written in **12 hexadecimal digits** divided by colons
![[Pasted image 20231222115913.png]]

### Mac destination addresses:
- Multi-cast: second digit (A3:......) is ODD
- Uni-cast: second digit (A2:....)is EVEN
- Broadcast: all ones (FF:FF:FF:FF:FF:FF)

We need to have an automatic procedures to manage this correspondence between addresses and /or address assignment need to be in place
![[Pasted image 20240104171353.png]]

## Mac translation 
To translate te [[IP]] into a Mac Addres we use the [[ARP Protocol]]

## Broadcast domain 
a local network can be partitioned in multiple Ip (aka subnetting) each subenetwork is a separate broadcast domain 
Arp message cannot leave the subnetwork of the sender, 
### Proxy Arp
![[Pasted image 20240104181902.png]]
- implemented in the router interconnecting the different subnetworks 
- **Intercept** all ARP request for IP addresses of other subnets and replies with its own MAC address
- **Forward** all frames with its MAC address to the proper subnetwork
 

