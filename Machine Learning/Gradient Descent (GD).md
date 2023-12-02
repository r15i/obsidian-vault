Task : Need a general approach to minimize a differentiable convex function f(w) with respect to the (weights) vector w (that can be very large)

## IDEA OF THE ALGORITHM
given that the [[Gradient of a Convex function]] points to the direction of the largest increase of f in the region close to w, we move in the opposite direction until we find a minima 


![[Pasted image 20231201112859.png]]

GD algorithm:
1. Initialize w at 0 or at an initial guess
2. for t in range(0,T-1) with T = to the number of iteration
		compute $w^{(t+1)} = w^{(t)} - \eta \Delta f(w^{(t)})$ 
 3. return $w^{(T)}$	

## Theorem Gradient Descent
![[Pasted image 20231201113632.png]]
### Corollary 
![[Pasted image 20231201113809.png]]
which means that to achieve an accuracy we need to iterate at least 
a fixed number


## Variation of this Algorithm

1. [[Stochastic Gradient Descent ( SGD )]]: uses a single sample to estimate the gradient
2. Batch Gradient Descent (standard GD): compute the gradient over the complete training set 

3. Mini-batch Gradient Descent: compute the gradient over a small set of k samples (k: parameter, mini-batch size), **Used to train deep neural networks**
	!!!!!!!!!!!!!!!!!!










