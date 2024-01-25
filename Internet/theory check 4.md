Certainly! Here are the reformatted incorrect questions for Obsidian:

1. **Question:**
   - **Text:** Consider a TCP connection in a state where there are no outstanding ACKs. The sender sends two segments back to back. The sequence numbers of the first and second segments are 230 and 290, respectively. The first segment was lost, but the second segment was received correctly by the receiver. Let X be the amount of data carried in the first segment (in bytes), and Y be the ACK number sent by the receiver. The values of X and Y (in that order) are

   - **Options:**
     - a. 60 and 290
     - b. None of these
     - c. 230 and 291
     - d. 60 and 231
     - e. 60 and 230
       
    Since the first segment was lost, the receiver would send an acknowledgment (ACK) for the next expected sequence number. In this case, the next expected sequence number would be 230 (the sequence number of the first segment that was lost). Therefore, the ACK number sent by the receiver (Y) would be 230.
	X = Sequence number of the second segment - Sequence number of the first segment X = 290 - 230 X = 60
![[Pasted image 20240124184940.png]]
rifare i grafichetti

3. **Question:**
   - **Text:** In which way does a TCP endpoint react to the third received duplicate ACK?

   - **Options:**
     - a. It immediately retransmits all the bytes in the congestion window, but does not restart the RTO.
     - **b. It immediately retransmits the first non-ACKed segment, and restarts the RTO with the current value.**
     - c. None of these
     - d. It immediately retransmits the first non-ACKed segment but does not restart the RTO (nor update its value).
     - e. It doubles the RTO and retransmits the first non-ACKed segment.
     - f. It closes the connection, since it is unreliable.



4. **Question:**
   - **Text:** If an IP datagram that carries a UDP datagram gets fragmented, and one fragment is lost along the path, the receiving UDP entity

   - **Options:**
     - a. None of these
     - b. Does not even realize the loss because the IP protocol will recover the lost fragment before notifying the upper layer entity.
     - c. Does realize the loss because of the out-of-order reception of IP datagrams.
     - d. Does realize the loss because of the out-of-order reception of UDP datagrams.
     - **e. Does not even realize the loss because the IP entity at the destination node will silently drop the other fragments of the datagram.**
    
	simply ip is not reliable and will not ack 


7. **Question:**
   - **Text:** During the slow start phase, the TCP congestion window

   - **Options:**
     - a. None of these
     - b. Is set to 1
     - c. Is constant
     - **d. Grows exponentially over time**
     - e. Grows linearly over time

8. **Question:**
   - **Text:** What is the maximum size of data that the application layer can pass on to the TCP layer below?

   - **Options:**
     - **a. Any size**
     - b. None of these
     - c. 216 bytes
     - d. 1500 bytes
     - e. 216 bytes - size of TCP header

	virtually the application set how much data to consume

9. **Question:**
   - **Text:** Let the size of the congestion window of a TCP connection be 32 KB when a timeout occurs. The round trip time of the connection is 100 ms, and the MSS used is 2 KB. What is the time taken (in ms) by the TCP connection to get the congestion window back to 32 KB?

   - **Options:**
     - a. None of these
     - b. 1100 to 1300
     - c. 1400 to 1600
     - d. 1500 to 1700
     - e. 800 to 1000
    ![[Pasted image 20240124201231.png]]
       
       equal in both tahoe e reno
       ![[Pasted image 20240124201248.png]]
	![[Pasted image 20240124201506.png]]
