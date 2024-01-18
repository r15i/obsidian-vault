- connection-oriented
- reliable 

# Connection phases:
1. Connection set-up: Three-way handshake
2. Data transmission : byte stream (as if a dedicated circuit were enstablished between source and destination)
3. Connection close: close the connection(only at the 2 hosts connected)
# reliablilty 
TCP uses a combination of GBN and SR
- checksum for error detection
- Byte numbers, sequence numbers, acknowledgment numbers:
  1. **retransmission**
  2. **reordering**
  3. **cumulative** and **selective** acknoledgments

## Services 
1. Proces2process 
2. Full-duplex Communication:(data flow in both directions at the same time)
3. Multiplexing and Demultiplexing
4. Reliable Service
5. Connection-Oriented Service:
   - TCP, unlike UDP, is a connection-oriented protocol
   - There is a **logical** connection 
   - TCP turns the **unreliable/connectionless** services offered by IP into a reliable/connection-oriented service offered to the application 
   

# TCP Packet Format
![[Pasted image 20240118123705.png]]
### Source e port (16bit)
#### Sequence Number(SN)(32bit)
defines the number assigned to the first byte of data contained in this segment 
- During connection establishment, each party uses a random generator to create a **initial sequence number(ISN)**
- **segment without payload do not have SN**
- SN is the sequence number of any other segment  is the sequence number of the prev_seg + num of bytes carried by the previous segment
# Ack number(32-bit)
defines the next byte number expected by the receiver 

- if the receiver of the segment has received succesfully x from the other party returns x+1 as the ack num 
# HLEN(4BIT)
the number of 4-bytes words in the TCP header


# Resv(6bit)
Reserved for future
# Window Size(16bit)
defines the available buffer space at the **receiver** in bytes
- normally referred as **receiving window** (rwnd)
- value **set by the receiver** 
- used in flow and congestion controll
# Flags (or Control)(6bit)
![[Pasted image 20240118125116.png]]
# Urgent Pointer(16bit)
used when the segment contains urgent data. It defines a value that must be added to the SN to obtain the number of the last urgent byte
![[Pasted image 20240118130115.png]]
# Checksum(16bit)
![[Pasted image 20240118130332.png]]
the same as UDP but  **mandatory**
1. TCP header
2. TCP data
3. pseudoheader
   
   # Options
   ![[Pasted image 20240118130721.png]]
   up to 40 bytes of optional information in th TCP HEADER as:
   - EOP(end of operation) for padding
   - No operation: used to align the beginning of an option
   - **Maximum segment size** (MSS): define the maximum size of the segment to be used, to avoid fragmentation in the IP layer (usually is MTU_SIZE-IP/TCP headers)
   
   # Connection Establishment
![[Pasted image 20240118130754.png]]
## Connectin