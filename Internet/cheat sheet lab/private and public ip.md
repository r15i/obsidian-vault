![[Pasted image 20240116125303.png]]
- EG: External Gateway 
- IG: Internal Gateway
## Intranet vs internet 
main reason **Different Intranets can reuse the same private IP addresses**

## Intranet
an intranet is never crossed by **external** traffic is not a media 
#### Intranet Private IP add
![[Pasted image 20240116125512.png]]

### Pros:
In the intranet, i can configure/activate more network hosts than the number of available IP addresses for that ISP
### Drawback:
i still need a PUBLIC IP address to connect to the Internet

## Implementation of the ip translation 
#### Application Proxy
![[Pasted image 20240116130103.png]]
all request are addressed to the proxy that forward by using its own public IP address
- needs a proxy for each application 
### Network Address Translator(NAT)
NAT has a **pool of public addresses** to be used to forward messages through the public internet
![[Pasted image 20240116150546.png]]
to allow **bi-directional** communication, the mapping must be **reversible** 
Must be a **Nat Table** tracking the translation 

- **Static** correspondence $\rightarrow$ a certain MAC addr is linked to an ip add (not feasible)
- **Dynamic** correspondence$\rightarrow$ a certain MAC address is assigned to any of the available public IP addresses upon request 
## **Dynamic association**
is based on session concept 
When interceptiong the first packet from a host the nat create a session and binds the private address of the host with a public address 

when the session is over the binding is broken and the public address is released in the pool and becomes available for other requests

## Nat characteristic
- **Transparent address translation**
- Transparent to routing algorithms 
- ICMP packet translation:(need to to translate also the ICMP pack )
![[Pasted image 20240116151305.png]]

# Traditional NAT
#### Basic Nat
also known as **outbound Nat** it only supports connections **Intranet**$\rightarrow$**Internet**
- Translates only private IP addresses of the host into public IP addresses
- **1-1** correspondence between private and public IPs in a session 
- A public address can be used by **single host during one session** 
- if the n$\cdot$public addr < n$\cdot$private addr: some connection may not start
- to serve multiple sessions with a single ip addr we need to use the NAT public IP address for multiple/different sessions
- PROBLEM: cannot support multiple sessions with the same NAT public IP
#### Network Address Port Translation (NAPT)
\[Private IP, Source port\] $\rightarrow$ \[Public IP, NAT source port\]
- NAT source port is randomly choosen among the still available ports of the **NAT-enabled gateway**
- The same public ip is reused in multiple sessions, **even with the same external host**

## Example 
![[Pasted image 20240116152435.png]]
  

# Bidirectional NAT 
Essentially not only change the source but also the destination  

we want to start the comunication from the public internet and end to a private intranet
we want to connect from a public IP to A private IP 
basically we want to connect to a server using only the private ip and translating it to a public ip 
![[Pasted image 20240116152602.png]]
![[Pasted image 20240116153202.png]]
 1. gets the private ip from the dns(with both public and private interface to be reachable from the client and to know)
 2. the response coming back from the dns passes by the nat that changes the IP from private to public 
- Supports both internal and external **session initiation**
- also sad as Twice NAT 

uses a **Domain Name System (DNS)** inside the Intranet
- DNS server translates the host name into its corresponding IP addresses
- After DNS TRANSLATION IP address is translated into public IP using NAT 
- Public IP is sent back to the public client using a DNS response 
		- DNS must be inside the Intranet
		- DNS must be statistically associated with a **public address**
		- **Static public/private binding for DNS addresses**

- All future communication will be done using that public IP address 
- The traditional NAT will make translation to reach the actual server in the Intranet



![[Pasted image 20240116155135.png]]
		
  



	