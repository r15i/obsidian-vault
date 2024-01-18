Provide a **process-to-process** communication instead of host-to-host
and nothing else
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
#### Process to process communication 
#### Connectionless Services 
- each user datagram is an independent datagram 
- not numbered 
- no connection enstablished
- **different path** for datagram 
- The process cannot send a stream of data and expect UDP to chop them into different, related user datagrams are only processes sending short messages (< 65,535 – 8 – 20 bytes) can use UDP.
##### Flow Control
there is no flow control 
#### Checksum 
![[Pasted image 20240116191418.png]]
- UDP checksum calculation includes 3 sections:
1. **pseudoheader**, the UDP header, and the data coming from the application layer 
2. the **UDP header** and the data coming from the application layer
3. the Data coming from the application layer 
some field are to 0 
# Checksum 
additional level of protection 
- violate the layering principles
- is optional 
# Error Control 
# Congestion Control 

# Encapsulation and Decapsulation 
# Multiplexing and Demultiplexing

## Application 
useful for :
- **Trivial File Transfer Protocol (TFTP)**: process flow and error control are inside the application layer 
- **multicasting**
- **Simple Network Managemnet Protocol (SNMP)** management processes 
- update protocols like **Routing Information Protocol(RIP)**  
- **in interactive real-time applications** that cannot tolerate uneven delay between sections of the received message
 






