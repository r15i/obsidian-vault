
5 sus 
L≥2×Propagation Time×Bitrate

9 sus

è una sliding window quindi bisogna fare il conto della queue dei pacchetti, quando si arriva a mandare piu di 3 pacchetti in realtà in quella trasmissione manda comunque un pacchetto
![[Immagine WhatsApp 2024-01-25 ore 10.39.38_58f19fd9 1.jpg]]
10 sus 
11 sus 

**Given Parameters:**
- Bitrate (\(R\)): 64 Kbps (\(64 \times 10^3\) bps)
- Propagation Delay (\(T_{prop}\)): 20 ms (\(20 \times 10^{-3}\) seconds)

**Formulas:**
1. Transmission Time (\(T_{trans}\)): \(T_{trans} = \frac{S}{R}\)
2. Link Utilization (\(U\)): \(U = \frac{S}{S + 2 \times T_{prop} + T_{trans}}\)

**Steps:**
1. Calculate \(T_{trans}\) using the bitrate (\(R\)).
2. Substitute \(T_{trans}\) into the link utilization formula.
3. Set \(U\) to 0.5 for 50% link utilization.
4. Solve for \(S\) (frame size).

**Result:**
The minimum frame size (\(S\)) for 50% link utilization is 320 bits. Since 1 byte = 8 bits, the minimum frame size in bytes is \(\frac{320}{8} = 40\) bytes.


11 sus
12 sus

13 sus
14 susu
has a smaller averatge transmission latency that fdma

# Sliding Window Protocol: Optimal Window Size

**Given Parameters:**
- Packet Size (\(P\)): 32 bytes
- Round Trip Delay (\(RTD\)): 80 ms
- Bottleneck Bandwidth (\(B\)): 128 kbps

**Formulas:**
1. Bandwidth-Delay Product (\(BDP\)): \(BDP = B \times RTD\)
2. Optimal Window Size (\(W\)): \(W = \frac{BDP}{P}\)

**Steps:**
1. Calculate \(BDP\) using the bottleneck bandwidth (\(B\)) and round trip delay (\(RTD\)).
2. Substitute \(BDP\) and \(P\) into the optimal window size formula.
3. Round the result to the nearest integer (since the window size must be an integer).

**Result:**
The optimal window size (\(W\)) is calculated to be 320. Therefore, the answer is option:

a. 320

---

Feel free to adjust the formatting as needed for your Obsidian notes.

