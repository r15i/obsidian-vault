### Handles the p2p communication between the hosts and the routers of the [[Frame]].

ROLE: It is responsible for delivering a [[Frame]] from one node to the physically adjacent node over a link (hopefully in a reliable way)
# Servicies 
![[Pasted image 20231222115347.png]]
Services offered by the Data link layer falls in 2 categories:
- [[Data Link Control (DLC)]] :  mainly in charge of the flow of data in the channel 
- [[Medium Access Control (MAC)]] : mainly in charge of the access/identification 

## Protocols 
The DLL layer have a lot of protocols that can be used
![[Pasted image 20231201183354.png]]
# MAC Address 
Identifier at DLL of the machine 
Defines a 48-bit DLL address usually written in **12 hexadecimal digits** divided by colons
![[Pasted image 20231222115913.png]]

### Mac destination addresses:
- Multi-cast: second digit (A3:......) is ODD
- Uni-cast: second digit (A2:....)is EVEN
- Broadcast: all ones (FF:FF:FF:FF:FF:FF)

We need to have an automatic procedures to manage this correspondence between addresses and /or address assignment need to be in place
![[Pasted image 20240104171353.png]]
## Mac translation 
To translate the [[Internet Protocol (IP)]] into a Mac address we use the [[Address Resolution Protocol (ARP)]]
