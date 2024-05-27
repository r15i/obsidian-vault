Is a technique that can be used to analyze games where moves unfold over time

It corresponds to apllying sequential rationality but as the name suggest it processes backwards starting from the in-game situations where a last rational decision can be made.

Once the uncertainty related to it is removed the procedure goes by considering the penultimate rational decision (wich means removing the end branching of the tree and goes to the last decision before that one , and so on )

The backward induction algorithm starts by considering nodes at the end of the tree, such as those who are only followed by leaf nodes. Some of there can be removed using rationality 

the strategic gameplay is planned by inducing further rational decision in the tree, and doing so by going backwards in the order of the decisions to be made.
This way the best decision path is eventually found 


## Iterative process 
1.  remove all the not rational leaves 
2. if it has an unique solution 
	- translate the resulting game in normal form 	find the ne , if they are unique 
	- Found the unique spe
	
1. back to 1 


the outcome of the backward induction process is usually the SPE




1. when it's his turn p2 sees p1 move $a_1^h$ and solves the optimization problem 
 ![[Pasted image 20231218143253.png]]
2. Call $R_2(a_1^h)$ the argmax solving the problem, $a_2$ yelding the max .
	due to complete info, 1 anticipates 2's reaction and solves:![[Pasted image 20231218143538.png]]
3. 1's solution $a_1*$ , the outcome is $a_1^*\,,R_2(a_1^*)$ is **is the NASH equilibrium in pure strategies**





[[equilibrium path]]
