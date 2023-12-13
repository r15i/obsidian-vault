# **Idea** of K-means
Find cluster center and point-cluster allocations in order to **minimize the error** made by approximating the points with the cluster centers
###### As an iterative algo:
1. **Fix cluster centers; assign each point to the closest cluster**
2.  **Fix allocations; compute best cluster centers**
3. iterate to 1 


# Notation
- $X \subset R^n$ Set of vectors to be clustered
- $x \in X$ Vector to be clustered
- $C_i$ $i = 1,...,k$ Clusters (each )
- $\mu_i$ $i = 1,...,k$ Centroids of the clusters
![[Pasted image 20231209152406.png]]


## Centroid Computation 
![[Pasted image 20231209151346.png]]

**Naive option**  : try all possible partitions of the m points into k clusters and evaluate each partition, to find the best one

**BAD!! :** 
- Number of possible partitions is exponential in m 
- NP-Hard problem

# K-Means : Algorithm
![[Pasted image 20231209152315.png]]
## Stopping Criteria
![[Pasted image 20231209152528.png]]
![[Pasted image 20231209152558.png]]

## examples
![[Pasted image 20231209153041.png]]
![[Pasted image 20231209153113.png]]
