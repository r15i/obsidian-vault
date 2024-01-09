## Bandwidth W \[ Hz \]:
range of frequencies contained in a modulated signal or range of frequencies
a channel can pass with acceptable attenuatin 

## Bitrate $R_0$  \[Bit/s\] or \[bps\] :
maximum transmission peed at bit level of a link
usally for calculating speeds as $T = \frac{M}{R_0}$ 

## Throughput $S$ \[Bit/s\], \[pck/s\], \[pck/slots\]: 
Rate at which data is traversing a link

## Goodput: $S_g$ \[Bit/s\], \[pck/s\], \[pck/slots\]: 
Rate at which USEFUL data traverses a link determined by [[Protocol Data Unit (PDU)]]  and [[SDU]]
### $S_g(N) = \frac{\text{Len}(SDU(N))}{\text{Len}(PDU(N))}$

![[Pasted image 20231121190507.png]]
these values are always  $S_g \leq S \leq R_0$ since the user can't over saturate the channel and the good data are always less than the data sent

## BOTTLENECKS
Bottlencks accours when a link limits the flow of information and is rappresented from $min{(R_c,R_s)}$ as 
![[Pasted image 20231121185953.png]]


