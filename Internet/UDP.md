Provide a **process-to-process** communication instead of host-to-host and nothing else
- **connectionless**
- **unreliable** 

used mainly for:
- No connection establishment(no delay)
- No congestion control: UDP can blast away packets
- Simple 
- Small segment header


# Packet format
datagrams with header of 8 bytes
![[Pasted image 20240116190620.png]]
#### UDP length(16bit)
defines the length of the packet 
#### UDP Checksum(16bit)
(optional)
## Services 
1. Process to process communication 
2. Connectionless Services $\rightarrow$ **different path** for datagram 
- each user datagram is an independent datagram 
- not numbered 
- no connection enstablished
- The process cannot send a stream of data and expect UDP to chop them into different, only processes s**ending short messages** (< 65,535 – 8 – 20 bytes) can use UDP.

#### Checksum 
![[Pasted image 20240116191418.png]]
- UDP checksum calculation includes 3 sections:
1. **pseudoheader**, the UDP header, and the data coming from the application layer 
2. the **UDP header** and the data coming from the application layer
3. the Data coming from the application layer  some field are to 0 
# Checksum 
additional level of protection 
- **violate the layering principles**
- is **optional** 
# Encapsulation and Decapsulation 
To send a message from one process to another, the UDP protocol encapsulates and decapsulates messages
# Multiplexing and Demultiplexing
there is only one UDP but several processes that may want to use UDP , to allow this UDP multiplexes and demultiplexes(**time statistical multiplexing**)
## Application 
useful for :
- **Trivial File Transfer Protocol (TFTP)**: process flow and **error control** are inside the application layer 
- **multicasting**
- **Simple Network Managemnet Protocol (SNMP)** management processes 
- update protocols like **Routing Information Protocol(RIP)**
- **in interactive real-time applications** that cannot tolerate uneven delay between sections of the received message
 






