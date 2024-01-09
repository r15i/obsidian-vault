# Intro
- The assignment of IP addresses to the ISP operating in a certain country is managed by the Regional Internet Registry(RIR) for that region , delegated by IANA
- What’s the minimum time taken to deliver a message of L bits, segmented into K packets of M bit each (header included) on a packet switching network with datagram approach, with a path of N links with bitrate R and propagation delay for each link τ?
	$T = (K + N - 1)M/R + N\tau$ 
	 Note : this formula accounts for the waiting of one transmitted packet at the time, enche waiting the arrival of each packet
 - internet is formed by the interconnecttion of a multitude of networks which communicate through the TCP/IP protocol stack
 - network Layer is unreliable because : packets may be out of order,packets may be lost, duplicates may be generated
 - which layer of the ISO/OSI model are host2host?: Transport,Session,Presentation,Application.
     Host2host means which are the layers wich are primarly concerned with the communication between the 2 host not with the general functioning of the net
- Repeater operates at ISO/OSI layer 1 (PHY)
- Flow control is handled by the Dll(2) and Transport layer(4)
- packet-switched networks transport services can be of any kind(connectionless,connection oriented, reliable, unrelaiable)
- a packet-switched network always requires an address and destination
- a bridge is used to connect LANS
