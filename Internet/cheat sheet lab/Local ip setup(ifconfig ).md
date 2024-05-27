
## Setting Up an Interface with a Hard-coded IP

```bash
ifconfig <INTERFACE> <IP> netmask <NETMASK> broadcast <BROADCAST_ADDR> <up/down>
```

### Example:

1. **Setting Up a Static IP Address on a Network with IP 192.168.1.0/24**
   ```bash
   ifconfig eth0 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.255
   ```

2. **Changing Maximum Transfer Unit (MTU)**
   ```bash
   ifconfig <INTERFACE> <IP> netmask <NETMASK> broadcast <BROADCAST_ADDR> MTU <mtu_size_BYTE> <up/down>
   ```

Setting the IP in this manner signifies interaction with a specific network. For handling other networks, a proper [[routing setup(route)|routing]] is required.

To check connectivity, use [[ping]].
