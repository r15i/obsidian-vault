

## General idea 
**A Nash Equilibrium can be seen as the case where nobody has regrets on his/her choice** and can be more than one combination of strategies 

Definition: in a n-player game $G = \{s_1,...s_n;u_1,...,u_n\}$
strategies $(s^{*}_{1},...,s^{*}_{n})$ are **Nash Equilibrium** if, for any $i$, $s^{*}_{i}$ is the best response to player $i$ to $(s^{*}_{1},...,s^{*}_{i-1},s^{*}_{i+1},...,s^{*}_{n})$ (AKA the current combination of strategies except the considered one) that :

to review
$\forall s_i\in S_i$   $u_i(s^{*}_{1},...,s^{*}_{i-1},s^{*}_{i},s^{*}_{i+1},...,s^{*}_{n}) \geq  \,u_i(s^{*}_{1},...,s^{*}_{i-1},s_{i},s^{*}_{i+1},...,s^{*}_{n})$ with $s^{*}_i = argmax_s\,u_i(s^{*}_{1},...,s^{*}_{i-1},s_{i},s^{*}_{i+1},...,s^{*}_{n})$

or that means that does't exist:


## Use of the Nash Equilibrium
it is intended as a forecast of the outcome, **Not** as the final result of several move,(will be disprove by repeated games ):




# Find the Nash equilibrium
Finding the Nash equilibrium is not always garanteed, in pure strategies
but always garanteed in mixed strategies by the [[Nash Theorem]]


## in [[Strategy#pure Strategy|Pure strategy ]] 

- ### with [[best responses]]
![[Pasted image 20231130154235.png]]
	The combination of strategies considered Nash equilibrium is the one who contains the best responses for both of the players.
	
 a way to see this approach is that:
	- Everyone plays a best response to their beliefs 
	- everyone's beliefs are correct
	so they can't regret

- ### with [[Iterated elimination of strictly dominated strategies (IESDS) |IESDS]]

	if we eliminate all the [[Strictly Dominate strategy]] and there is only one combination of strategies, that combination is a nash equilibrium 
	
	Theorem:
	In a finite game, if $(s^{*}_1,...,s^{*}_n)$ is:
	- the only survivor of IESDS 
	- or the only rationalizable profile 
	than it is a *NE*
	
	Lemma : 
	a NE survives [[Iterated elimination of strictly dominated strategies (IESDS) |IESDS]] with any order


## in [[Strategy#Mixed Strategy|Mixed Strategies]]

Nash equilibrium in mixed strategies is found with the [[indifference principle]] 

$Example:$ 

if P1 plays $pA + (1-p)B$  and P2 can choose between $\{D,E\}$ 
$u_{p2}(p,D) = u_{p2}(p,E)$
$\downarrow$
$u_{p2}(pA + (1-p)B,D) = u_{p2}(pA + (1-p)B,E)$
$\downarrow$
$p\,u_{p2}(A,D)+ (1-p)\,u_{p2}(B,D) = p\,u_{p2}(A ,E)+ (1-p)\,u_{p2}(B,E)$



this equation allow us to find $p$ and than finding also  the corresponding 
probability $q$ for player 2 we can plot the NE as a graph of $p$ and $q$








