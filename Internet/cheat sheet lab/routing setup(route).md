## add default gateway
**route** add default gw \<IP_DEFAULT_GATEWAY\>

AKA where all the packets by default go

example:
route add default gw 195.11.14.1
basically every network i don't know is reachable by 195.11.14.1

## add a static route
**route add**  -net \<IP_DESTINATION_NET\> **netmask** \<NETMASK_DESTINATION_NET\> gw \<IP_OF_THE_GATEWAY \> dev \<INTERFACE_GATEWAY\>

explanation:
basically how to reach the destination ip of the net with this netmask with the interface and at that ip


route add -net 195.11.14.0 netmask 255.255.255.0 gw 100.0.0.9 dev eth1
- -net \<IP_DESTINATION_NET\>  is the network i want to reach
-  **netmask** \<NETMASK_DESTINATION_NET\> net mask is the objective network netmask
-  gw \<IP_OF_THE_GATEWAY \>  is the ip of the machine that allows me to get to the network
-  dev \<INTERFACE_GATEWAY\>  the interface wich the gw is 


in every PC there is usually only a default gateway (since is usually a terminal node)
on router PC there is generally static routes 
to test the connectivity we usually use [[traceroute]]
