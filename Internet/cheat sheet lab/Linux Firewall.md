# The Linux Firewall

`iptables` is a user-space tool that interacts with the kernel-space counterpart [[NetFilter]] to establish a **stateful** packet filter incorporating [[private and public ip]].

## NetFilter Structure

NetFilter operates on two primary levels:

### Tables

There are four tables within NetFilter, each containing chains (some predefined):

1. [[Filter Table]]
2. [[Nat Table]]
3. [[Mangle Table]]
4. [[Raw Table]]
### Chains

There are five chains where rules are applied:

1. PREROUTING
2. FORWARD
3. INPUT
4. OUTPUT
5. POSTROUTING

Each chain contains a list of rules defining matching criteria and a target for packets.

## Path of Packets
![[Pasted image 20231206204003.png]]


After routing decisions, packets are directed to determine if they are destined for the local system or need forwarding. Subsequently, they pass through the defined filters.

## Streams

### Input Stream Packets
Packets entering the system.

### Output Stream Packets
Packets leaving the system.

### Forward Stream Packets
Packets being forwarded between interfaces on the system.

---

This explanation offers an overview of the Linux firewall, particularly focusing on `iptables` and its integration with NetFilter. It emphasizes the structure involving tables, chains, the path packets take through the system, and different packet streams that the firewall processes.