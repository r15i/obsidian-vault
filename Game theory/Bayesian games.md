Equilibrium concepts were developed earlier as modeling players that are forming **consistent and correct beliefs**

IDEA:
Game of [[incomplete information]], beliefs over the characteristics of other players are captured by their [[types]]

Bayesian games model strategic interaction where the involved players have some degree of uncertainty that goes beyond not knowing the choice of the others

we will develop an equilibrium concept that still requires these beliefs to be consistent and correct (so we use the same procedures)

## Preliminary Nature's move 
Players may have different payoffs (each represented by a [[types|type]])

The timing of the game is as follow:
- Nature draws a type vector($t_1,....,t_n$) among all possibiliteies for all the players (**type assignment**) 
- Nature reveals type $t_i$ , to player i only 
- Players choose their actions
- Payoffs are computed
- IN this kind of dynamic game where the players do NOT know Nature's move in its entirety

## Assumption on independently drawn types
So in principle we should consider the **joint distribution** $p(t_1,....,t_N)$ for all players $1,2,....N$ with $t_j$ is the type of player J
However, it is very frequent to assume that types are drawn independently for each player as such that we can use the marginal distribution for 
$$p(t_1,....,t_N)=p_1(t_1)\cdotp_2(t_2)\cdot\cdot\cdot p_N(t_N)$$

because in reality independence is often assumed for **tractability** reasons


## Example
![[Pasted image 20231219144844.png]]
Now we can assume P2 :
- **Rational**: behaves as already discussed 
- **Crazy**: enjoys fighting and his/her payoff for (Enter,Fight) is actually 2 instead of -1
Is actually Nature that sets the type of 2: with probability p to be "Rational"
## Dynamic Game with types
![[Pasted image 20231219145356.png]]
### Representing Bayesian games
Normal-form games (TILL NOW):
- set of players $N$
- strategy space of each player $S_i$ (for i = 1..n)
- utilities of players $u_i:(S:1,S_2,...S_n)\rightarrow R$ (for i = 1..n)
Bayesian games add 3 additional characteristics:
1. [[types]] and type **space** of each player $T_i$ (for i = 1..n)
2. also, utilities are now **type-dependent**
3. finally, we need **beliefs** about other players types



## Common prior 
Is an adaptation to describe what the players knows about the game 
Therefore, in Bayesian game we need to set some **common ground** about what the players know about the game

. This means that the joint probability distribution $p(t_1,t_2,....,t_n)$ is [[Common Knowledge]]:
- players know their own type with cerainty
- have an estimate (the probability distribution) of what their type could possibly be
- we can assime that this PD is known by all players and is **the common prior assumption**


## Type agent 
**type-agent** representation of players with a type in which their strategy is modeled like if the player suffered from split personality.
These players plan in advance a strategic choice per each one of their types.

The correct modeling choice in order to represent the beliefs of the other players since they do not know the type of that Bayesian players instead, therefore can expect every sort of behaviour

## Types as mixed strategies 
Bayesian games give a very sensible interpretation to mixed strategies since for a given player it is clearly identical to assume that another player with 2 pure strategyes A,B can :
- player that playes a mixed strategy of A,B with probability $\alpha$ and $1-\alpha$ 
- A Bayesian player with 2 different types $t_A$ and $t_B$ with their probabilities as $\alpha$ and $1-\alpha$ 
finallt the type-agent representation of this bayesisna player chooses A when the type is $t_A$ and B when $t_B$ 

(to complete from the book)



## Bayesian Nash equilibrium (BNE)
The general framework of Bayesian games can be specified to many different contexts 
The solution concept used for each of these cases may change.
The straightforward extension of Nash equilibrium to the Bayesian case is known a s Bayesian Nash equilibrium (BNE)
## Perfect Bayesian equilibrium (PBE)
The equilibrium concept of PBE is relevant for sequential Bayesian games, dynamic games with incomplete information, as the proper extension of the simpler concept of BNE 