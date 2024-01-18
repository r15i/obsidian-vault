Transport layer privides end2end logical communication between app processes running on different hosts

Responsible for creating a one2one transparent VIRTUAL PIPE between two ends of the communication flow
- offers **process2process** communication
- It offers realiability and tries to acheve **error-free communication** 

 Addressing at the transport layer adds the port number  ![[Pasted image 20240107194442.png]]

- Sender: breaks app messages into **segments**, passes to network layer
- Receiver: reassembles **segments** into messages, passes to app layer 

communication is provided using a **logical connection** wich means that the 2 application layers, assume there a **direct imaginary connection** through wich they can send/receive messages

Transport-layer protocols are implemented in the end system **but Not in routers**

## Services offered at transport layer

- Process-to-process communication
  Allow communication between application processes
- Addressing 
  Client-server paradigm using port numbers
- Encapsulation/Decapsulation
- Multiplexing/Demultiplexing
  Delivery from one source to many sources

if using a reliable Transport protocol also :
- Error control
- Flow control
- Congestion control

A **process** is an application-layer entity (running program)

### port numbers
16 bits \[ 0, 65.535 \] values are used to identify the process referring the packet

- **universal port numbers** are well known port numbers used for some specific application and assigned
- **ephemeral port number** (>1023) port defined in the client side program used to receive data 
![[Pasted image 20240116173342.png]]

## IP addresses at transport layer
## Socket
![[Pasted image 20240116174917.png]]
**IP address** $\rightarrow$ identifies the host
**Port number** $\rightarrow$ identifies the process on the host

## ICANN Ranges 
![[Pasted image 20240116174057.png]]
ICANN has divided the port numbers into 3 ranges:
- **Well-known** ports(0,1023) assigned and controlled by ICANN 
- **Registered** ports (1024,49151) not assigned or controlled by ICANN 
- **Dynamic ports** (49152,65535)e used as temporary or private port numbers
![[Pasted image 20240116174339.png]]
## Encapsulation/Decapsulation
- Encapsulation: happen at the sender site. When a process has a message to send 
- Decapsulation: happen at the receiver site , drop the header and return the message
## Flow control 
Balancing **production and consumption** rates of data 

- **pulling** : the producer delivers items after the consumer has requested them (no need of FC , RECEIVER IS REDY)
- **pushing**: the producer delivers items whenever they are produced (need for **flow control**) if the items are produced faster than they can be consumed, the consumer may be overwhelmed
  ![[Pasted image 20240116175512.png]]

## Buffers
Buffers can alleviate the burden of flow control 

A buffer is a set of memory locations that can **hold packets** at the sender and receiver 

- When the buffer **sending transport** layer is full it informs the application layer to stop passing chunks of messages , and when in case restart
- When the buffer **receiving transport layer** is full, it informs the **sending transport layer to stop sending packets**

## Error Control
we need to implement **reliability** with:
- **discarding corrupted packets**
- **Keeping track of lost and discarded packets** and resending them 
- Recognizing **duplicate** packets and discarding them 
- Buffering **out-of-order** packets until the missing packets arrive

As in flow control the reciving transport layer manages error control by informing the sending transport layer about the problems (with ack an nack)

To know wich packet to resent, and wich is a duplicate or wich packet has arrived out of order uses a **sequence number**
of the packet


## Congestion Control 
refers to the mechanism that control the congestion and keep the load below capacity 

- Congestion in a network occurs because routers and switches have queues. 
- Congestion at the transport layer is the result of congestion at the network layer 

a router has an input queue and an output queue for each interface. If a router cannot process the packets at the same rate at which they arrive

## Control service
- ERROR: involves only the sending and receiving transport layers 
- FLOW: Depends on the capability at the receiver/sender
- CONGESTION: Depends on the channel and context characteristics 

## Protocols 

- **User Datagram Protocol(UDP)** :
	- **unreliable** (error control can be provided by the application-layer process) 
	- connectionless transport-layer
	- used for its simplicity and efficiency 
- **Transmission Control Protocol(TCP)** 
	- **reliable**
	     Mainly through some already seen transport protocols such as Stop-and-wait,Go-back-N,Selective-repeat
	- connection-oriented
- **Stream Control Transmission Protocol (SCTP)** is a new transport-layer protocol that combines the features of UDP/TCP 
  
  ## Examples 
  ![[Pasted image 20240116185858.png]]
  








