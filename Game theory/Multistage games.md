
(Same players playing multiple games)

IDEA:  many real games have **intermediate** steps that give partial payoffs, valued on aggregate(Tournaments, Rounds of Cards, Partial Exams)

**We define a multistage game as a finite sequence of T normal form
Stage games** are defined independently of each other and include the same set of players.
They are complete but imperfect information games
Total payoffs are evaluated from the **sequence** of outcomes of the stage games
![[Pasted image 20231218223746.png]]
## Example on the Prisoner-Revenge
![[Pasted image 20231218224016.png]]
![[Pasted image 20231218224059.png]]

### Strategies of multistage games
A strategy for each player must specigy 
- what to do in the **first** stage (just one action)
- what to do in the subsequent game depending on the outcome of the previous game


#### SPE in multistage games
find [[Subgame-perfect Nash Equilibrium (SPE)]] we have to remember that is a joint strategy such that a NE is plaed in every subgame

#### TH.1 
If $s_j^*$ is a NE strategy profile for the $j^n$ stage of the game then there exists a SPE whose equilibrium path is $s_1^*,s_2^*,...,s_T^*$

#### TH.2 
Any NE $s*$ even if it is not SPE of a multistage game ($G_1,G_2,...,G_T$) must dictate a NE is played in stage game $G_T$
#### TH.3
If $G_1,G_2,...,G_T$ all have a unique NE, then($G_1,G_2,...,G_T$) has a unique SPE

## Note 
th.2 and th.3 imply that if the last stages have only one NE, **this will be played**



# Repeated Games

IDEA : A repeated game $G(T,δ)$ is a dynamic game where the same static game $G$ is played as a stage game $T$ times and payoff are discounted by δ and accumulated.

they may be:
- Finitely repeated games: finite horizon (same game played T times)
	
- Infinitely repeated games: infinite horizon (used to model random exit, also, if horizon is infinite, must be  δ <1)



### Example 
![[Pasted image 20231219134737.png]]

![[Pasted image 20231219134901.png]]
# Finitely repeated games 

### Finitely repeated games Theorems
Finitely repeated games: finite horizon (same game played T times)
#### Th1
The outcome of last stage is a NE
#### Th2
if stage game $G$ only has NE $s^*$ the $G(T,\delta)$ has a unique subgame-perfect outcome, IE $s^*$ is played in every stage

## Cooperation in Finitely repeated games
Repeated games tend to introduce cooperation(thou to a limited extent)

Cooperation is possible when punishment strategies are available, when punishment strategies are available; multiple punishment options are better
The sub-game-perfect outcome is (M,m) followed by (H,h): no better deviation.

# Infinitely reapeated games 
IDEA: stage game $G$ and discount factor $\delta$ : denoted as $G(\infty,\delta)$
remember we need to have discount $\delta<1$ if want the game to be *meaningful*
In infinitely repeated games we cannot apply [[backward induction]] (no "last" stage)

*this means we do not need "external" punishments respect to the finite horizon*
There may be SPE of $G(\infty,\delta)$ in which no stage's outcome is a NE of G

### Grim trigger strategy (GrT)
- Start playing M at stage 1
- At stage t>1, play M only if outcome of all t-1 previous stages was $(M,M)$, otherwise play F
#### Grt SPE 
for $\delta$ "close enough" to 1, the joint strategy where both users play GrT is a SPE 

## Friedman Theorem

The key result for infinitely repeated games
![[Pasted image 20231219141002.png]]
### Case of study Tit-for-Tat
![[Pasted image 20231219141106.png]]
![[Pasted image 20231219141211.png]]
## Reputation 
Building trust over sequential iterations
(TO expand if necessary)


# Dynamic bargain
Negotiation of resource sharing 

Assume two players need to split a give amount of resources 

we have 2 approaces :
- Nash bargaining (aximatic,static)
- Seen as a dynamic game (the one seen here):
	modeled as alternate stage where p1 and p2 exchange proposer/responder roles


