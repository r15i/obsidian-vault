Absolutely, here's the information formatted in a way that you can easily copy and paste:
### Route Utility Commands

#### Show Routing Table
```
route
```

#### Add Default Gateway(indirect)
```
route add default gw <IP_DEFAULT_GATEWAY>
```
This command sets the default gateway where all packets will be directed by default.

Example:
```
route add default gw 195.11.14.1
```
This directs all packets to the default gateway 195.11.14.1 for networks that aren't known.

#### Add a Static Route (direct)
```
route add -net <IP_DESTINATION_NET> netmask <NETMASK_DESTINATION_NET> gw <IP_OF_THE_GATEWAY> dev <INTERFACE_GATEWAY>
```
Explanation:
This command establishes a specific route to a destination IP with a specific netmask through a defined gateway reachable via a specified interface.

Example:
```
route add -net 195.11.14.0 netmask 255.255.255.0 gw 100.0.0.9 dev eth1
```
- **-net** \<IP_DESTINATION_NET\>: Network to reach.
- **netmask** \<NETMASK_DESTINATION_NET\>: Netmask of the target network.
- **gw** \<IP_OF_THE_GATEWAY\>: IP of the machine facilitating access to the network.
- **dev** \<INTERFACE_GATEWAY\>: Interface through which the gateway is accessible.

#### Delete Entry in the Routing Table
```
route del -net <IP_DESTINATION_NET> netmask <NETMASK_DESTINATION_NET> gw <IP_OF_THE_GATEWAY> dev <INTERFACE_GATEWAY>
```
This command removes a specific entry from the routing table.

### Additional Information

- In most PCs, there's usually only a default gateway as they're often terminal nodes.
- Routers generally have static routes configured.
- If a node is connected to two identical networks on different collision domains but with the same IP, it may default to the first one (e.g., often eth0).

#### Testing Connectivity
For testing connectivity, `traceroute` is usually employed.

