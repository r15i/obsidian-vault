## Probabily Approximately Correct (PAC)
Since the training data is sampled accordingly to $D$ ([[Machine Learning#Probability distribution|Probability distribution]] on $X$)
we can only be:
- **approximately** correct
- **probably** correct
and we measure this 2 aspect with 
- an   **accuracy** parameter $\epsilon$  such that the [[True Error]]  to be $L_{D,f}(h_{s})\leq \epsilon$ 
 - a **confidence parameter** $\delta$ that measure the probability $h_s$ (hypotesis of traing set s ) of beeing a good hypothesis with probability  $\geq 1-\delta$ 	
## Finite Hypothesis Classes are PAC Learnable
IDEA: for sure if we have a finite class of Hypothesis Classes these are PAC

TH Prerequisite:
- $H$ hypothesis class
- $\delta\in(0,1)$, $\epsilon\in(0,1)$ and $m\in N$ (size of Training set)
- If it holds that: $$m\geq\frac{log(\frac{|H|}{\delta})}{\epsilon}$$ (the proportionality  m $\uparrow$  as $|H|\uparrow$ and $\delta,\epsilon, \downarrow$  )
- for all $f$ and any $D$ considered the [[Realizability Assumption]]  and with a probability $\geq 1-\delta$ 
- the [[Empirical Risk Minimization (ERM)|ERM]] hypothesis $h_s = ERM_H$ is computed on $S$ training set of size m **SAMPLED [[iid]] from $D$**  

It holds that:
$$L_{D,f}(h_s)\leq\epsilon$$ 
 
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



