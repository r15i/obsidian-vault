## setup an interface with an harcoded ip

**ifconfig** \<INTERFACE\> \<IP\> **netmask** \<NETMASK\> **broadcast** \<BROADCAST_ADDR\> \<up/down\> 

example :
 1. SETTING UP A STATIC IP ADDRESS ON A NET with ip 192.168.1.0/24
	 ifconfig eth0 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.255
	
 2. it is also used to change [[Maximum transfer unit (MTU)]]
	 **ifconfig** \<INTERFACE\> \<IP\> **netmask** \<NETMASK\> **broadcast** \<BROADCAST_ADDR\> 	 **MTU** \<mtu_size\> \<up/down\> 








