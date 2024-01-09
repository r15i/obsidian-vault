Handles framing, Flow control, and error control 

#### Flow Control 
If the receiving node gets overwhelmed Flow control allows to feed back from the receiving node to the sending node to stop or slow down pushing pushing frames, to allow the receiving node to breathe
#### [[Dll Framing]]
Division of the message in smaller parts, and the addition of a sender and a destination address(in the header)

#### Error Control
- **Error Correction** : Add enough redundacy bits to correct errors (FEC: FORWARD ERROR CORRECTION CODE)
- Error detection by means of Cyclic Redundancy Code (CRC) in combination with [[Automatic Repeat reQuest (ARQ)]] protocols

