Classification problem with 2 classes:
Training data :
$S = ((x_1,y_1),...,(x_m,y_m))$ 
$x_i \in \mathbb{R}^{d}$  $Y = \{-1,1\}$
Hypothesis set $H = halfspaces$


*problem find the hyper plane which BETTER separates the points*

 *Assumptions:* 
 if the data is [[Linearly Separable Training Set| linearly separable]]   exist a halfspace that perfectly classify the training set

*Margin:* minimum distance from an example in the training set 

![[Pasted image 20231124162607.png]]

*Margin definintion:*
Given a separating hyperplane defined by 𝐿 = 𝒗: < 𝒗, 𝒘 > +𝑏 = 0 and given a sample x, the distance of x to L is 𝑑 𝒙, 𝐿 = min{ 𝒙 − 𝒗 : 𝒗 ∈ 𝐿 }

Theorem:
if $||w||  = 1$ $then \, d(x,L) = |<w,x> +b|$

In this case the margin is $min_i{|<w,x_i> +b|}, x_i \in S$
the closest examples are called **Support vector**

![[Pasted image 20231124163311.png]]





THE key point is that the best separating hyperplane is the most robust to noise









 
 
