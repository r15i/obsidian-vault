the targets are the actions that iptables performs on packets 


- ACCEPT to accept the packet
- DROP to silently drop the packet 
- REJECT to drop the packet and send a message back to the sender
(--jump REJECT [--reject-with type])
- LOG to record all packets that match the criteria defined in the rule 


