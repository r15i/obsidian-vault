## Probabily Approximately Correct (PAC)

Since the training data is sampled accordingly to $D$
we can only be:
- **approximately** correct
- **probably** correct
and we measure this 2 aspect with 
- an   **accuracy** parameter $\epsilon$  such that the [[True Error]]  to be $L_{D,f}(h_{s})\leq \epsilon$ 
 - a **confidence parameter** $\delta$ that measure the probability $h_s$ (hypotesis of traing set s ) of beeing a good hypothesis with probability  $\geq 1-\delta$ 	
## Finite Hypothesis Classes are PAC Learnable
![[Pasted image 20231128133730.png]]

## Pac learnability 

![[Pasted image 20231128133956.png]]

## Corollary (PAC)
![[Pasted image 20231128134113.png]]

## Agnostic PAC Learnabilty

Dropping the [[Assumtions]] from the [[PAC learning#Probabily Approximately Correct (PAC) |PAC]]

![[Pasted image 20231128140816.png]]



## Agnostic PAC Learnabilty: General Loss Functions

![[Pasted image 20231128153141.png]]



