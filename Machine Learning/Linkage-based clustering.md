# **Idea**
1. Start from the trivial clustering : each data sample/ point is a single point cluster
2. Until "termination condition " : repeatedly merge the "closest" cluster of the previous clustering 

# Parameters:
## Distance definition
definition of **cluster-to-cluster** distance (not **point-to-point**): 
- single linkage:
![[Pasted image 20231209153856.png]]

- average linkage
 ![[Pasted image 20231209154033.png]]

- max linkage
![[Pasted image 20231209153952.png]]

## Termination condition

Common **termination** condition:
- data points are partitioned into **k** clusters
- minimum distance between pairs of clusters is > r, where r is a parameter provided in input 
- all points are in a cluster $\rightarrow$ output is a dendrogram
## Example

![[Pasted image 20231209154321.png]]
![[Pasted image 20231209154347.png]]