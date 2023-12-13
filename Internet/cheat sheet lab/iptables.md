Used to interact with the [[Linux Firewall]]

## Common  Usages
## Cleaning policy's
- iptables --table filter --flush
- iptables --table filter --delete-chain
### Setting default policy's

# to note default  table is filter table 
**iptables** --table \<TABLE> **--policy \<CHAIN> \<ACTION>**

Examples:
 - iptables --table filter --policy INPUT DROP
	 Drop everything going in the INPUT chain 
 - iptables --table filter --policy OUTPUT ACCEPT 
	ACCEPT evrything going in the OUTPUT CHAIN
## Append a rule 
**iptables** --table \<TABLE> --**append**  \<CHAIN> **--in-interface** \<INTERFACE> **--jump** \<ACTION>

Examples :
- **iptables** --table filter --**append**  INPUT **--in-interface** eth0 **--jump**  ACCEPT
- Accept everything  from eth0 and append it to the filter table 

### Matching protocols data 
**iptables** --table \<TABLE> --**append**  \<CHAIN> **--protocol ICMP**   **\<PROTO PAR>** --jump** \<ACTION>


- TCP matching
	**iptables** --table \<TABLE> -A \<CHAIN> **-p ICMP**   **\<PROTO PAR>** --jump** \<ACTION>

	

- **ICMP protocol**
**iptables** --table \<TABLE> --**append**  \<CHAIN> **--in-interface** \<INTERFACE> **--jump** \<ACTION>
## Allow coversations
- **iptables** --table filter --append INPUT --match state --state ESTABLISHED,RELATED --jump ACCEPT

	Allow conversation per le connessioni già stabilite per le connessioni correlate("RELATED"), per related si intende connessioni già stabilite,
## Parts 
[[Rules Commands]]
[[Maching Criteria]]
[[Targets]]



