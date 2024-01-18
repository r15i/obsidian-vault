![[Pasted image 20240114191103.png]]
Main protocol of the [[Network layer]] based on the [[IP address]]
- Unreliable
- best-effort communication service 
     means that ip packets can be corrupted, lost, arrive out of order, delayed and create congestion for the network 
- Universal addressing 
- Fragmentation / reassembly 
- **Connectionless** , uses a **datagram approach**. it is responsible for **packetizing**,**forwarding** and **delivery** of a packet
essentially knows where is everything but can't speak to whom needs to in a concrete way


![[Pasted image 20240114190642.png]]

## IP datagram 
![[Pasted image 20240114191210.png]]
##### **Vers** (4bit) 
version number (number 4)
##### HLen(4bit) 
total length of the data gram **header** in 4-byte words 
 $Hl\cdot4\,byte=$L header (Byte)
    $min(HLen) = 0101|_2$ wich is 20 bytes 
    $max(HLen) = 1111|_2\,(2^4-1)$ ()wich is 60 bytes 
##### TOS(o DS)(8 bit)
![[Pasted image 20240115160551.png]]
Type of Service
![[Pasted image 20240115124419.png]]
##### Total length(16 bit)
total length (header+data)
$Lenght\,of\,data = Total Length -(HLEN)\cdot 4$

##### TTL (8 bit)
**Time to live** of a datagram that loses its way in the internet. 
The TTL is used to control the **maximum number of hops(routers)** that can be visited by the datagram 
- decrease at each forwarding/hop of each router
- if TTL becomes zero Datagram is droppend and the rutrer **may** send **ICMP**
##### Protocol (8bit)
specify wich upper layer protocol we use (with an id)
![[Pasted image 20240115124855.png]]

when the datagram arrives at the destination the value of this field helps to define to wich protocol the payload should be delivered
(**multiplexing/demultiplexing**)
##### Header Checksum(16bit)
**Header Check sum** is used to check against the **IP header** errors and rappresent  a **rough form of control**

- checks only the **IP Header** 
- Has to be recomputed at every op since the header changes ([[#TTL (8 bit)]])
- Checksum is 16bit wich is the complement of the sum of other fields calculated using 1s complement

##### Source and Destination Addresses (32bit + 32bit)
- this values remains **unchanged** during the time the IP datagram travels 
- **Netmask** is not included (this info is provided by net admin or [[DHCP]] servers)
# Maximum tranfer Unit (MTU)

- the format and size of the frame **depend on the protocol used by the physical network** through wich the frame has just traveled
- One feature of these protocols is the MTU, wich dictates the maximum size of the **payload** 
- Ethernet default is 1500 bytes but can be lower for wans

  ## IP packets fragmentation
  Large IP datagrams are **fragmented** so that they can comply to the MTU specified at lower layers
  ![[Pasted image 20240115162241.png]]

  - **only** the payload is fragmented , the header is kept the same 
  - if a packet during is way to his destination encounters a smaller MTU     gets more fragmented 
#### Updating for fragmentation  (re put in top near the rest of the fields)


if a router needs to fragment some packets 3 fields need to be updated: **flags**,**fragmentation* **offset** and **total length**
- **Identification** (16bit): same for all fragments, used as a label for all fragments of the same datagram
- **Flags** (3bit): **fragmentation control**
	- R - Reserverd
	- D- Don't fragment 
		  **Note** that if the message is too big to pass for MTU it will discard the datagram and sends an error to the host
	- M- more fragment to come 
- **Fragmentation Offset**(13bit) 
shows the relative position of a fragment with respect to the whole datagram. it is the offeset of the **data** in the original datagram **measured in units of 8 bytes**
![[Pasted image 20240115163132.png]]

## Fragmentation example 
![[Pasted image 20240115163155.png]]
#### reassembly 
i recognize the original (unfragmented) PDU 
- since it has :
	  1. **M** flag
	  2. **fragment offset** 0 
- first fragment :
	1. M flag to 1 
	2. **fragment offset** 0 
- last fragment :
	1. M flag to 0
	2. fragment offset $\neq$ 0
- fragment from the same PDU:
	- same **identification** FIELD

 the fragment offset field is computed by taking into account only the *data* that has been carried in previous fragment
## Changed by FRAGMENTATION
![[Pasted image 20240115164018.png]]


### Avoid Fragmentation
A **single late** fragment may determine the loss of the whole datagram and IP does not care about this

- Transport layer(the upper) is unaware of IP fragmentation $\rightarrow$ it can recover a whole datagram but not a single fragment
- if MTU is known just don't exeed it on the internet the minimum required MTU is of about **576 bytes**
  
# Options and Padding 
Options (up to 40 bytes):
Not required , used for test and debug
![[Pasted image 20240115164558.png]]







 






