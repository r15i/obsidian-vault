IDEA aims to give spatial awarness of the data (context)
![[Pasted image 20231229153328.png]]
# Convolutional Neural Network (CNN)
![[Pasted image 20240109100618.png]]



![[Pasted image 20231229153611.png]]

## Local connectivity
receptive field for each neuron 
	![[Pasted image 20231229154018.png]]
	each neuron in connected only with related other neuron 
## Shared ("tied") weights
spatially invariant response
	![[Pasted image 20231229163534.png]]
	every connection to a neuron share the same weights but with a **different input window**
	that slides across all the neurons of lvl -1	

## Multiple feature maps
    ![[Pasted image 20231229163751.png]]
	each **feature map of neurons share the same weights and slide on the neurons** with a **input window**
     The destination neurons are called **FEATURE MAPS** and are used to compute different functions

## Convolution
    ![[Pasted image 20240109093728.png]]
	![[Pasted image 20240109093147.png]]
	We learn The **feature maps**(Filters)
	![[Pasted image 20240109093202.png]]
	![[Pasted image 20240109094333.png]]
	essentially we do a dot product sliding the filter on the matrix of the image keeping it in the image square and using the center to determine the objective of the result pixel
    **the stride** is how much me move between a pixel and another (**kinda sampling**)

     ![[Pasted image 20240109094725.png]]
#### Convolution vs Fully connected
![[Pasted image 20240109095055.png]]
Notice that the model size depends in :
- CNN only by the convolution size 
- NN on the data matrix size

we have less parameters
![[Pasted image 20240109095243.png]]
![[Pasted image 20240109095306.png]]
	
## Pooling Layer
![[Pasted image 20240109095410.png]]
Reduce resolution $\rightarrow$ next convolutional layer is applied at a larger scale

Crucial to improve performace in many applications since it increases the receptive field of the inner layers

## Max Pooling 
is the most common example of such layer: it works very well, it is quick, and can be efficiently implemented in hardware

![[Pasted image 20240109095740.png]]
## Receptive Size 
A small convolution window correspond a largere area in the previous layers
![[Pasted image 20240109100359.png]]![[Pasted image 20240109100422.png]]
## Flattening and Fully Connected layer at the end
![[Pasted image 20240109100504.png]]
In the final stage we apply still a NN fully connected layer cuz is needed for completeness


## Advanteges CNN
1.  Hierarchical representation: Low level features(stupid pixels) 
2.  **Weight Sharing**: huge reduction of complexity respect to NN 
3. CNN model "compress" a fully connected network in various ways:
	- reducing the number of connections
	- shared weights and edges
	- Max pooling further reduces the complexity

#note can be a dynamic way to set the pooled feature maps precision?


## CNN application 
- AlphaGo 
- Speech Recognition
	![[Pasted image 20240109101215.png]]
- Text classification 
	 ![[Pasted image 20240109101230.png]]

