# Datagram approach

![[Pasted image 20231130113527.png]]
- No setup at network layer
- **Store-and-forward** based network: the intermediate nodes stores the packets and decides to forward it to another node towards the destination 
- No call to setup network layer
- The routers have no idea they are forwarding packets of a connection
- Packets are forwarded using a **destination host address**, (using the **header**)
- Packets between same source-destination pair may take different paths
- Leverage **statistical multiplexing**:
	![[Pasted image 20231130114035.png]]


# Virtual approach

![[Pasted image 20231201180422.png]]
- as [[Packet-switched network (PS)]] messages are divided in small units called cells
- as [[Circuit-switched network (CS)]] communication requires three phases:
 1. circuit setup
 2. data transfer 
 3. circuit tear down
 - Dedicated Logical connection(no dedicated resources)
 - Local identifier is carried by each cell and changed at each hop
 - All packets follow the **same path** and are sent in **sequential order**
 
## Comparison Virtual vs Datagram approach 
![[Pasted image 20231201180733.png]]


