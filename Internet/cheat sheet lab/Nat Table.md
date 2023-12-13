
### Nat Table
usage: **used for NAPT operations and contains three pre-defined chains**:
**chains**:
- PREROUTING 
- OUTPUT 
- POSTROUTING 
**Operations**:
- **DNAT** changes the **destination** address and port of a packet
- **SNAT** changes the **source** address and peply, or Forwardort of a packet
- **MASQUERADE**  works like SNAT but supports firewalls with dynamic public IPs
- **REDIRECT** redirects the packet to the firewall
