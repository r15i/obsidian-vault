## Subnetting
More levels of hierarchy can be created using **subnetting**
allow to create another level of network starting using part of the HostID

![[Pasted image 20240108213828.png]]
Note that the:
- address is expressed in format **Address/n** wich express the number of bit of the net, 
- the netmask express the actual bit for the host_id
the difference between this 2 indicators gives us the the number of bits of the subnet

**Note the Network ID part is the real deal breaker for the ISP** and the part that they can't actually change

rules for functioning subnets: 
1. requested addresses per subnetwork($N_{sub}$) $\rightarrow$ must be a power of 2 
2. prefix length of each subnetwork($n_{sub}$)$\rightarrow$ $n_{sub}= 32 - log_2N_{sub}$

	THIS IS TO CHECK 
3. if we are creating more than one level of subnetting we need to fist assign the larger sublocks(the ones that requires more bits)

## Supernetting 
Inverse problem of Subnetting 

Classes A and B do not have enough networks
so we use some class (bits from the **NetID**) and join them into a bigger network(**supernetting**) 

![[Pasted image 20240109092244.png]]
