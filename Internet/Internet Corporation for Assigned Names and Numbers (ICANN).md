assign blocks of addresses to an ISP 

FOR CIDR the rules are :
1. requested address (M)$\rightarrow$ M needs to be a power of 2
2. Prefix length of each block (n)$\rightarrow$ $n = 32- log_2M$
3. the number of addresses in the block is always a power of 2. The network address fo the block will have hence a suffix of $log_2M$ zeros
![[Pasted image 20240108213430.png]]


