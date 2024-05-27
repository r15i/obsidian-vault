after the net block is assigned to the organization the network administration can **manually** assign addresses to the host or routers 

# Automatic ip assignation 
protocols:
![[Pasted image 20240114175548.png]]
1.  Bootstrap Protocol (BOOTP)$\rightarrow$ Deprecated
   - static addressing
   - essentially a db wich contains each MAC-IP couple for every  pc in the net
   - BOOTP request request the response is the ip assigned
   
1. **Dynamic Host Configuration(DHCP)**
- More hosts than available IP addresses 
- Useful when hosts don't require permanent IPs
- Addresses are **leased** to a host a limited time, after which the host must return it ,and if the ips are over requests are denied
- DHCP is a **client-server protocol** in wich the client sends a request message and the server returns a response message
## DHCP workflow
1. Discovery (broadcast)
	A host (client) that needs to configure its interface **broadcasts** a **DHCPDISCOVER** message, containing it's MAC address
	![[Pasted image 20240114184540.png]]
	the transaction-ID field is set to a random number.
2. Offer (broadcast)
	- Each(can be multiple) DHCP server intercept the request and replies with a **broadcast** **DHCPOFFER** that contains it's ID and proposed IP address with **lease time** 
	![[Pasted image 20240114184905.png]]
3. Request (broadcast)
	- The joining host receives one or more offers and select the best of them.
	- The client can accept the offer by sending a **broadcast** **DHCPREQUEST** 
		![[Pasted image 20240114184944.png]] 
4. ACK (broadcast+ftp)
	- The server then associates the IP to the host and replies with **broadcast** DHCPACK message that contains the **path to fetch all needed information** by **FTP**: **netmask(for HostID and NetID), Default Gateway,DNS SERVER** ![[Pasted image 20240114185748.png]]
5. Release (unicast)
	- When the address is no longer needed (e.g. the interface is switched off ), the host sends a (**unicast**) **DHCPRELEASE** to the server
	![[Pasted image 20240114185730.png]] 

# DHCP State Diagram 
![[Pasted image 20240114190103.png]]
