Division of the message in smaller parts, and the addition of a sender and a destination address(in the header)

We need to have similar transmission time between frames the physical layer provides **bit synchronization** to ensure that TX and RX use the same bit durations and timing 

IDEA:  Framing in the DLL divides a message in smaller parts, and adds a sender and a destination address (in the **header** ) 
# Frame size
## Fixed-size (example ATM WAN)
- no need for defining the bundaries of the frames;
- the size itself can be used as a delimiter
## Variable-size (PREVALENT)
### Character oriented framing (or byte-oriented)
![[Pasted image 20231222132206.png]]
### Bit oriented framing 
![[Pasted image 20231222132224.png]]
# Stuffing 
Used to distinguish between the flag and the actual data
both rely on modifying the data to allow to distinguish the data from the actual flag of header and trailer 
## Byte stuffing (for character oriented)
Stuff a predefined **ESC CHARACTER** before the FLAG  from the upper layer and after other ESC CHARACTERS that may be in the data from the upper layer
![[Pasted image 20231222133402.png]]
## Bit stuffing (for bit oriented)
we use **0111110** as the flag like pattern appears in the data it will change 011111**0**10, so the real flag is  011111**1**10 and is not stuffed by the sender and is recognized by the receiver.
![[Pasted image 20231222133335.png]]


![[Pasted image 20231222144013.png]]