
![[Pasted image 20231220164256.png]]
# Notation 
#### Graph notation
$G = (V,E)$ Denote the graph 
- $V$: neurons ($|V|$ is the size of the network)
- $E$: connections between neurons (**directed** edges )
- $w:E\rightarrow R$ is the weight function over the edges (the weights w are parameters to be learned)
#### Layers notation
Usually the network is organized in layers:
![[Pasted image 20231221145757.png]]
#### Layer Notation
- $V_t$ with $t = 0,...,T$ is the t-th layer
- $d^t+1$ number of nodes of layer t (the constant neuron is to avoid bias and incorporate as in homogeneous coordinates )
- $V_0$ is the **input** layer and $V_T$ the **output** layer 
- $T$ : depth of the network 
#### Neurons Notation
- $v_{t,i}$  for the i-th neuron in t-th layer 
- $v^{(t)}=(1,v_{t,1},...,v_{t,d^t})^T$  all neurons of the layer **t**
RIVEDO
- $w_{rj}^{(t+1)}=w(v_{t,r},v_{t+1,j})$ all weights of arc from neuron **r in t to neuron j in t+1**

RIVEDO
- $w_j^{(t)}=w(w^{(t)}_{0j},...,w^{(t)}_{d^{(t-1)}j})^T$: all weights of arcs in input to **neuro j of layer t** (from layer t-1 to t )
- $w^{(t)}$ : matrix of weights of all **arcs incoming to layer t**
![[Pasted image 20231220170421.png]]
## Neural network vs Deep Network
usually for $T=2$ we consider "classic NN"
for T>>2 we have [[Deep Networks]]
# Neuron working 
![[Pasted image 20231220164148.png]]
each neuron : 
1. Takes in input the sum of the outputs of the connected neurons from previous layer weighted by $w$
2. Applies to the result a simple scalar function ([[Activation Function]] $\sigma$)
### FROM HERE KEEP THE NOTATION IN VECTOR
![[Pasted image 20231220170627.png]]


# Elements Defining the NN
**reorganize**
Neural Network (NN)
- (V,E,$\sigma$,$w$) Corresponds to a function $h_{V,E,\sigma,w}: R^{|V_0 -1|}\rightarrow  R^{|V_T|}$ and it's hypothesis class of a network is defined by fixing it's architecture:
- $H_{V,E,\sigma}= \{h_{V,E,\sigma,w}:$ w is a mapping from E to R$\}$
- $V,E,\sigma$ defines the architecture of the network 
- $w$ contains the parameters that are going to be learned


# Training Neural Networks
**Training of the NN**: finding the optimal set of weights $w$
### Types of propagation in NN 
- [[Feedforward Neural Networks#Forward Propagation|Forward Propagation ]](**A neural network using Forward Propagation is sad [[Feedforward Neural Networks]]**)
- [[Backward Propagation]]

## Implement Conjunction and Disjunction with NN
#### Expressive Power of NN (boolean functions)
basically what can i model with this kind of algos (spoiler binary level lot)
![[Pasted image 20231220174136.png]]

![[Pasted image 20231220174239.png]]


![[Pasted image 20231220174401.png]]
## VC dimension of NN
![[Pasted image 20231220174456.png]]
## Optimization NN

![[Pasted image 20231220174650.png]]

## [[Stochastic Gradient Descent ( SGD )]] for NN
![[Pasted image 20231220174724.png]]
![[Pasted image 20231220174751.png]]

## The NN training algoritm 
**It's a combination of BackPropagation algorithm with SGD**
![[Pasted image 20231220175627.png]]
##### Details :
1.  Pre-processing : Typically, all inputs are normalized and centered in 0 and both local or global normalization stratigies
2. Initialization of the weights 
	![[Pasted image 20231220175856.png]]

#### ENDPOINT:
WHEN DO WE STOP:
- Small training error
- Small marginal imporvement in error at each step
- Upper bound on number of iterations

NOTE: **Loss function usually has multiple local minima**
- With highly dimensional speces the risk is smaller than in low dimensional ones, but no garantee
- Run Stochastic gradient descent (SGD) from diffeent (random) initial weights

![[Pasted image 20231220180248.png]]



# Issues with this model neural network
![[Pasted image 20231220180904.png]]
[[Convolutional Neural Networks]] try to solve these problems





