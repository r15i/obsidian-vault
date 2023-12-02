

there are 2 modes :
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

## Comparison Virtual vs Datagram approach
![[Pasted image 20231201180733.png]]
