# **Idea**:
Divide a set of objects represented by N-dimensional vectors into groups 
(sad **clusters**) of similar objects

# **Formal Definition**: Clustering
Clustering is the task of grouping a set of objects such that **similar objects end up in the same group** and dissimilar objects are **separated into different groups**

## Problem of Similarity:

What is the concept of similiarity?
![[Pasted image 20231209133242.png]]


## Application of clustering 

- Business and marketing: Market research , grouping of items, Customer Segmentation
- WWW : Search engines, Social network analysis
- Image segmentation 
- Medicine, Mediacl imagining
- Biology and bioinformatics
- Recommender systems
- Anomaly detection 
- Natural language processing



# Clustering Model 

### Lore: 
**m** :  num samples
**k** : clusters 
**n** : data dimensionality 

## Input
- Set of elements $x \in X$
- Distance function $d: X\times X \rightarrow R_{+}$ such that is [[symmetric]], $d(x,y)\geq \forall x,y$ and  $d(x,y)= 0$ , and grant the [[Triangle inequality]] ($d(x,z)\leq d(x,y)\,+\,d(y,z)$)
## Output

A partition $C = (C_1,C_2,...,C_k)$ of set $X$ into $k$ cluster:
- $\cup^{k}_{i=1} C_i = X$ : The union of $C_i$ must be equal to $X$  
- **$\forall i \neq : C_i \cap = X$** , All cluster are disjoined


# Distance(cost)-Based Clustering


usual work with clustering and main ideas:
- Define a cost function over possible partitions of the objects
- Find the partition ( $\rightarrow$ clustering) of minimal cost
### Assumtions we make 
- Data points come from a larger space $X'$ (typically $R^n$)
- Distance function  $d(x,x')\,for\,x,x'\,\in\,X$ and $X' = R^n$ and $d(x,x') = ||x-x'||_2$ (Basic Euclidean distance)


## Common Clustering Algo 

[[K-means]] and [[Linkage-based clustering]]


 
