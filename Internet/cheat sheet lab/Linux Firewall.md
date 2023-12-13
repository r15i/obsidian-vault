
# The Linux firewall
[[iptables]] is a user-space tool that acts on the kernel-space counter parte
[[Linux Firewall#NetFilter|NetFilter]] to implement a **stateful** packet filter with  [[Network Address and Port Translation (Napt)|Napt]]

## NetFilter 
Structure on 2 levels:
- ## Tables
 4 tables each containing chains (some of them predefined):
 1. [[Filter Table]]
 2. [[Nat Table]]
 3. [[Mangle Table]]
 4. [[Raw Table]]

- each chain contains a list of rules, defining some matching criteria and a target

## Path of the packets 

![[Pasted image 20231206204003.png]]

when we arrive to routing we have to find out if it is for us or to forward
and than it passes for the filters

## Streams 
### Input Stream Packets
### Output Stream Packets
### Forward Stream Packets




