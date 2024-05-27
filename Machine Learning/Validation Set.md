Idea: divide the training set in 2 parts, use the first to pick an hypothesis, and the second (not used to train ) to estimate its true error 

given $h$ prediction (obtained by [[Empirical Risk Minimization (ERM)]] rule on  $H_d$ ):

## $V = ((x_1,y_1),....,(x_{m_v},x_{m_v}))$ 
is the set of m_v samples from D not used for training (validation set)
## $L_v$  
loss computed on V (loss \[0,1\])

$Theorem :$
for every 𝛿 ∈ (0,1) , with probabililty $\leq 1-𝛿$ (over the choice of V)
we have :
![[Pasted image 20231124151159.png]]
This bound depends : 
- on validation set size, not on the training set size
- Does not depend on the [[VC-dimension]]

THE [[Empirical Risk Minimization (ERM)| empirical risk ]] on the validation set is NOT an estimate of the true risk,  in particular if we choose among many models


