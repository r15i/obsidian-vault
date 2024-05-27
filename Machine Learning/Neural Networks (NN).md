## Feed forward network 
the graph representing the network has no cycles (data flows only in one direction)

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
- $w_{rj}^{(t+1)}=w(v_{t,r},v_{t+1,j})$ all weights of arc from neuron **r in t to neuron j of layer t+1**
- $w_j^{(t)}=(w^{(t)}_{0j},...,w^{(t)}_{d^{(t-1)}j})^T$: all weights of arcs in input to **neuro j of layer t** (from layer t-1 to t )
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

## Forward Propagation
How the neural network computes with weights the results
Take an **input** sample and compute the output of the network.
each **layer sends it's output to the next**, through all the layers up to the **output layers**

- Input :
	$x=(x_1,.....,x_d)^T$ (a NN with 1 output node)
- Output:
	prediction $y$ of NN
- Algorithm
	$v^{(0)}\leftarrow(1,x_1,....,x_d)^T$            # input layer	
	for t in range(0,T)                     # for each layer 
	    # compute the current layer values  of each neuron (before activation)
		$a^{(t)}\leftarrow(w^{(t)})^T v^{(t-1)}$	
		# compute the actual activated neurons with the activation function
		# NOTE: THIS PART IS NOT LINEAR 
		# 1 is the bias
		$v^{(t)}\leftarrow(1,\sigma(a^{(t)})^T)^T$
	$y\leftarrow v^{(T)}$
	return $y$

**NOTE:
THE VALUE OF a() is what actually become value**
what is passed is $\sigma(a())$

![[Pasted image 20231220172750.png]]




# Elements Defining the NN
**reorganize**
Neural Network (NN)
- (V,E,$\sigma$,$w$) Corresponds to a function $h_{V,E,\sigma,w}: R^{|V_0 -1|}\rightarrow  R^{|V_T|}$ and it's hypothesis class of a network is defined by fixing it's architecture:
- $H_{V,E,\sigma}= \{h_{V,E,\sigma,w}:$ w is a mapping from E to R$\}$
- $V,E,\sigma$ defines the architecture of the network 
- $w$ contains the parameters that are going to be learned

## Expressive Power of NN (boolean functions)
basically what can i model with this kind of algos (spoiler binary level lot)
![[Pasted image 20231220174136.png]]

![[Pasted image 20231220174239.png]]
## [[VC-dimension]] of NN
![[Pasted image 20231220174456.png]]
# Optimization NN

![[Pasted image 20231220174650.png]]
# Target Erm
![[Pasted image 20231227124505.png]]

# The NN training algoritm 
**It's a combination of BackPropagation algorithm with SGD**
## F&B training NN
- input 
	$w^{(t)}_{ij}$ $\forall i,j,t$ which are all the weigts from neuron i in t-1 to neuron j in t
- Algorithm 
	for $s$ till convergence:
		- pick $(x_k,y_k)$ random from the training data
		- compute $v_{t,j}$ $\forall j,t$ with [[Neural Networks (NN)#Forward Propagation|forward propagation]] 
		   witch gives the last layer
		- compute $\delta^{(t)}_j$ $\forall j,t$ with [[Neural Networks (NN)#Back propagation|back propagation]]  wich gives us the error from the first layer for each layer
		- Update the weights reaching the current layer as [[Stochastic Gradient Descent ( SGD )|SGD]] 
	
			$w^{(t)[s+1]}_{ij} = w^{(t)[s]}_{ij} - \eta v_{t-1,i}\delta_j^{(t)}$
	if converged then return $w^{(t)[s]}_{ij}$  $\forall i,j,t$
	
![[Pasted image 20231229152039.png]]

##### Details :
1. Pre-processing : Typically, all inputs are normalized and centered in 0 and both local or global normalization stratigies
2. Initialization of the weights 
	- 0 will not work (0 activation)
	- random values around 0 (here is mostly linear)
	- uniform or normal distribution can be used
	- multiple initialization and tranings can be used to bruteforce a lower error
	- for [[Deep Networks]] we have [[Glorot]] inizialization
	
 	
## [[Stochastic Gradient Descent ( SGD )]] for Neural Networks
Handles the way we update the weights
#### [[Stochastic Gradient Descent ( SGD )|SGD]] Algorithm for NN
- Parameters
	$\tau$  : number iterations
	$\eta_1,\eta_2,..,\eta_{\tau}$ : series of learning rate make the step size
	$\lambda>0$ Regularization parameter
- Input 
	$G = (V,E)$ : Neural Network
	$\sigma:R\rightarrow R$ : [[Activation Function]]
	
- Algorithm 
	 choose $w^{[1]}\in R^{[E]}$ at random
	 for s in range($\tau$):
		 sample $(x,y) \sim D$ (prendi un sample dai dati)
		 calculate the gradient $\nu_s$ = [[Neural Networks (NN)#Back propagation|backpropagation]]$(x,y,w,(V,E),\sigma)$
		 **update $w^{[s+1]} =w^{[s]}-\eta_s(v_s+\lambda w^{[s]})$ (lambda is for regularization)**
- Output
	 $\bar w$ is the best performing  $w^{[s]}$ on the validation set

##### Update Rule [[Stochastic Gradient Descent ( SGD )|SGD]] in NN
![[Pasted image 20231220174751.png]]

- $w^{[s+1]} =w^{[s]}-\eta_s(v_s+\lambda w^{[s]})$ (lambda is for regularization)
- $w_{ij}^{(t)[s+1]} = w_{ij}^{(t)[s]}-\eta_s \frac{\partial L_s}{\partial  w_{ij}^{(t)[s]}}$ (TO NOTE IN RESPECT TO EACH WEIGHT)
- $\frac{\partial L_s}{\partial  w} = \frac{\partial}{\partial  w}(\frac{1}{m} \sum_{i=1}^{m} l(h,(x_i,y_i)) =\frac{1}{m} \sum_{i=1}^{m} \frac{\partial L(h(x_i,y_i))}{\partial w}$  
- $\delta^{(t)}=\frac{\partial L}{\partial  a^{(t)}}$  is the change in error w.r.t. to the weighted average before the non linear transformation 
TO NOTE we can compute the loss only on the last layer (since we have a way to understand if it is right or not)

 [[Feedforward Neural Networks#Forward Propagation|Forward Propagation ]](**A neural network using Forward Propagation is sad [[Feedforward Neural Networks]]**)
## Back propagation

![[Pasted image 20231220174834.png]]
![[Pasted image 20231220174855.png]]![[Pasted image 20231220175057.png]]

![[Pasted image 20231229150613.png]]
#### Complete algo back prop
![[Pasted image 20231220175129.png]]
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
Issues with Fully connected [[Neural Networks (NN)#Feed forward network|feed forward]]:
- each neuron of layer t-1 connected with each neuron of layer t
	**exponential and huge number of edges/weights (quadratic w.r.t. the number of neurons in each layer)
- The domain structure is not taken into account
	- the model does not consider that a neuron can be "closer" (more related) to some neurons and less to others
	- some domains have a structure
		ex, a grid of pixels in an image, the sequece of samples of an audio signal, the letters of a workd in a text 
		**need a way to rappresent that "near" data is related"
	
	- interesting features are often local, shift-invariant and deformation-invariant
	- by simply placing data in a vector we have a loss of spatial or temporal strucure
	- 
[[Convolutional Neural Networks]] try to solve these problems
# Problems NN
### Overfitting 
Fail to generalize to new examples (test data)
![[Pasted image 20240109101325.png]]![[Pasted image 20240109101346.png]]
Do not use a too complex network if training data is limited
#### Tecniques to avoid overfitting:
##### Dropout (killing neurons)
![[Pasted image 20240109101613.png]]
- Randomly drop neurons(along with their connection ) during training 
- Each unit retained with fixed probability $p$ as **hyper parameter** to be tuned
- Typically applied only at some layer 
- More stable/ less risk of overfitting
#### Regularization
![[Pasted image 20240109104438.png]]
- term added to the loss function 
- penalizes big weights and reduces risk of overfitting 
- Regularization parameter $\lambda$ determines how relevant regularization is during gradient computation 
- Big $\lambda \rightarrow$ big penalty for big weights (higher training error but less overfitting)
#### Early Stopping 

![[Pasted image 20240109104659.png]]
- Use validation error to decide when to stop training
- Stop when monitored loss has not improved after n subsequent epochs 
- parameter "n" is called **patience**
#### Data Augmentation 
![[Pasted image 20240109104812.png]]
Artificially create different samples 
- by noise 
- by random tranformation 
- by altering the colors / luminanace ...


### Gradient Descent for NN
1. [[Gradient Descent (GD)]]
2. [[Stochastic Gradient Descent ( SGD )]]
3. Mini-batch gradient descent
4. [[Momentum ]]
5. [[Adam(adaptive Moment Estimation)]]


## Loss function:[[Cross Entropy]]

# Multi-class
#### One-hot encoding 
Output: vector **y** with one component for each class
$y_i :=1$ if the sample class i , $y_i = 0$ else
Its an increased output data dimensionality 

#### Extension of cross-entropy to multi-class
- labels one-hot encoded, vector function $f$ to be estimated
- $f_i(x)$ estimated probability that x belong to class i 
$L(f(x),y)=-\sum_{i}{y_ilog(f_i(x))}$ 

# Tools

![[Pasted image 20240109111243.png]]




### Advances [[Deep Learning]] approaces




