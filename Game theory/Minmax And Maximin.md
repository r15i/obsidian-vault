Optimization approach to game theory

# Maximin
Considering a 2 player game (i vs -i)
we define $f_i:S_i \rightarrow R$ as $f_i(s_i)= min_{s_{-i}\in S_{-i}} u_i(s_i,s_{-i})$ 

$s_i^*=arg\,max_{s_{-i}\in S_{-i}} f_i(s_i)$ is a *SECURITY STRATEGY* (AKA maximinimizer) for i (and may be not be unique)

We say that
## $w_i=max_{s_{-i}\in S_{-i}}min_{s_{-i}\in S_{-i}} u_i(s_i,s_{-i})$
is the maximin of the security payoff of $i$

**A security strategy is a conservative approach allowing i to achieve the highest payoff in case of the worst move by -i**
# Minimax
Similarly:
$F_i:S_{-i}\rightarrow R$ as $F_i(s_{-i})=max_{s_{-i}\in S_{-i}}min_{s_{-i}}u_i(s_i,s_{-i})$ is called the **minimax** for player i 
IDEA: if i could move after -i , the minimax would be the minimum payoff wich is guaranteed to player i.

## Notes:
- if we have a [[Nash Equilibrium]] $minimax_i$ = $maxmin_i$ = $u_i(s_i,s_{-i})$  point of equilibria 

### EXAMPLE:
![[Pasted image 20231218152642.png]]

![[Pasted image 20231218153141.png]]
### Minimax Theorem for pure strategies
![[Pasted image 20231218154244.png]]
![[Pasted image 20231218154455.png]]

# Mixed maximin/minmax
![[Pasted image 20231218181256.png]]
Any mixed strategy $m_i^*$ maximizing $f_i(m_i)$ is a **mixed security strategy**
for i 
![[Pasted image 20231218181823.png]]

## Minmax Theorem for mixed strategies
![[Pasted image 20231218182110.png]]
## Linear Programming applied to search of Minimax 
the search of minimax solutions of a zero-sum game is a nice application of [[Linear Programming]]
![[Pasted image 20231218182417.png]]
