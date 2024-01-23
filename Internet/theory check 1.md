Il tempo minimo richiesto per la consegna di un messaggio di \(*L*\) bit, suddiviso in \(*K*\) pacchetti ciascuno di \(M\) bit (incluso l'header) su una rete a commutazione di pacchetto con approccio datagram, con un percorso di \(N\) collegamenti, ciascuno con un bitrate \(R\) e un ritardo di propagazione per ciascun collegamento \(\tau\), è rappresentato dall'opzione:

$T = (K + N - 1) \frac{M}{R} + N\tau$


Ora analizziamo ogni parte dell'equazione:

- $( (K + N - 1) \frac{M}{R})$ : Questa parte rappresenta il tempo richiesto per inviare tutti i pacchetti sulla rete. \(K\) pacchetti devono essere inviati, ognuno con una dimensione di \(M\) bit (incluso l'header), attraverso \(N\) collegamenti con un bitrate \(R\). Il termine \(N - 1\) tiene conto del fatto che ci sono \(N\) collegamenti, ma solo \(N - 1\) "spazi" tra i collegamenti attraverso i quali i pacchetti possono essere inviati.

- \( N\tau \): Questa parte rappresenta il ritardo di propagazione totale attraverso tutti i collegamenti. \(N\) è il numero totale di collegamenti, e \(\tau\) è il ritardo di propagazione per ciascun collegamento.
## Question 6

**Select one:**

- Internet is a network with world-wide extension, managed by a single entity, which is called IETF.

- Internet is a set of networks where all subnetworks use the very same protocol stack in order to enable inter-network communications.

- Internet is formed by the interconnection of a multitude of networks, which communicate through the TCP/IP protocol stack.

- Internet is formed by a number of subnetworks, owned by different organizations, and each using their own protocols. The interconnection occurs in the Network Access Points (NAP), which performs protocol translations and make it possible inter-network communication.

**Feedback:**
The correct answer is: Internet is formed by the interconnection of a multitude of networks, which communicate through the TCP/IP protocol stack.

 **Question 12:**
  - What is the role of a bridge in the network?

- **Options:**
  - a. to separate LANs
  - b. to control network speed
  - c. to connect LANs
  - d. none of these

- **Feedback:**
  - The correct answer is: to connect LANs
    
- **Question 15:**
  - According to the ISO/OSI model, a Protocol Data Unit (PDU) of layer n is composed by:

- **Options:**
  - a. the PDU of layer n−1
  - b. the PDU of layer n+1 and the header/trailer (i.e., control information) of layer n
  - c. none of these
  - d. the PDU of layer n+1
  - e. the PDU of layer n−1 and the header/trailer (i.e., control information) of layer n    
    
# ISO/OSI Model: Flow Control

According to the ISO/OSI model, flow control can be handled by:

- a. Only the physical layer
- b. Only the transport layer
- c. None of these
- d. Only the data link layer
- e. Any layer


c none of these
