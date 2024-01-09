
IDEA : A decision tree is a model that predicts the label associated with a sample $x$ by traveling along a tree from the root to a leaf (For us only binary tree)

At each internal node we make a decision based on features of $x$ and split the **input space** (as simplest $x_i<\theta$ or $x_i\geq\theta$)

![[Pasted image 20240109121654.png]]

## Training the tree

Considering a **binary** classification setting and assume to have a gain (performance) measure:

- Start : A single leaf assigning the most common of the 2 labels i.e, the one of the majority of the samples 
- each generation :
	- Analyze the effect of splitting a leaf
	- Among tall possible splits choose the one leading to a better gain in performance measure and split the corresponding leaf (or NOT)
## Iterative Dichotomizer 3 (ID3)
![[Pasted image 20240109122329.png]]

## Gain
#### Gain Measure
[[Error|Training error]]  Define the gain as the decrease in the training error

### Gini Index
![[Pasted image 20240109122557.png]]
it's a measure of statistical dispersion in a frequency distribution:
- For binary classification case : $G=2p(0)p(1)=0$ 
	 if all samples are in the same class, $G=1/2$ for 50% spilts
- Measure of variance: higher variance more misclass
- refers to how "pure" is the distribution after the split
- Gini index is a smooth and concave upper bound of the train error
### Threshold based splitting 
Threshold based splitting rules for real valued features extend by creating a set of threasolds and testing all the varous combination and feature 

![[Pasted image 20240109123747.png]]

# Pruning
![[Pasted image 20240109123808.png]]
- Key issue of ID3 : the tree is typically very large with high risk of over fitting 
- Prune the tree to reduce its size without affecting too much the performance

## Random Forest (RF) 
Instead of using a single large tree construct an ensemble of simpler trees 

A Random forest (RF) is a classifier consisting of a collection of decision trees

The prediction is obtained by a majority voting over the prediction of the single trees

![[Pasted image 20240109123950.png]]

![[Pasted image 20240109124208.png]]

## Random Sampling with Replacement

![[Pasted image 20240109124405.png]]