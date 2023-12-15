![[Pasted image 20231206204003.png]]
## Common Usages

### Cleaning Policies

- **Flush and Delete Chain in Filter Table**
    ```bash
    iptables --table filter --flush
    iptables --table filter --delete-chain
    ```

## Setting Default Policies

- **Setting Default Policy for Chains in Filter Table**
    ```bash
    iptables --table filter --policy <CHAIN> <ACTION>
    ```
    Example:
    ```bash
    iptables --table filter --policy INPUT DROP
    ```

## Notes
- To allow loopback when dropping traffic:
    ```bash
    iptables --table filter --append INPUT --in-interface lo --jump ACCEPT
    ```
## Append a Rule
```bash
iptables --table <TABLE> --append <chain-name> [matching-criteria] --jump ACCEPT
```
Example:
```bash
iptables --table filter --append INPUT --protocol icmp --icmp-type echo-request --jump ACCEPT
```

### Show Chain
```bash
iptables --table filter --list
```
## Filtering 
usually ONLY FILTER TABLE  is only on INPUT, OUTPUT,FORWARD

### Accepting ping 

```bash
iptables --table filter --append INPUT --protocol icmp --icmp-type echo-request --jump ACCEPT
```

### Accepting port 
```bash

iptables --table filter --append INPUT --protocol tcp --destination-port 22 --jump ACCEPT
```
### Accepting the Conversation
```bash
iptables --table filter --append FORWARD --in-interface eth1 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
```
## NAT Commands

NAT IS (USUALLY)ONLY PREROUTING POSTROUTING 
#### Change Outgoing IPs
```bash
iptables --table nat --append POSTROUTING --source 192.168.1.0/24 --out-interface eth1 --jump SNAT --to 163.132.142.213
```
#### Redirect to a PC
```bash
iptables --table nat --append PREROUTING --protocol tcp --destination-port 80 --in-interface eth1 --jump DNAT --to 192.168.1.1:80
```



## Matching Criteria

### From/To Which Interface
- `--in-interface eth0`
- `--out-interface eth0`

### Source/Destination IP
- `--source ip-address`
- `--source network-address/netmask`
- `--destination ip-address`
- `--destination network-address/netmask`
### ICMP
- `--protocol icmp --icmp-type message-type`

### TCP (only for the port)
- `--protocol tcp --source-port port-number`
- `--protocol tcp --destination-port port-number`

### State Match (Used for Conversations)
- `--match state --state NEW,ESTABLISHED,RELATED`
## Actions
- `--jump REJECT`
- `--jump DROP`
- `--jump ACCEPT`
- `--jump DNAT --to ipaddr[:port]`
- `--jump SNAT --to ipaddr[:port]`
