uses of deep learning:
- Image Classification
- Object Detection
- Semantic Segmentation

Simple CNN for Image Classification 
![[Pasted image 20240114165954.png]]
Typical (baseline):
- First a set of **convolutional** layers
	- ex 3 convolutional layers with 2x2 max-pooling 
- End Few fully connected layers
	  - The fully connected layers take in input 1D vectors and not the 2D structures 
	  - Since pooling has beed applied before they work on low resolution data (resulting )
- End Softmax Layer can be added
- The parameters' identification is a challenging task
![[Pasted image 20240114170440.png]]

this has links can be useful 
![[Pasted image 20240114170541.png]]
![[Pasted image 20240114170946.png]]
## Forward pass
![[Pasted image 20240114171019.png]]![[Pasted image 20240114171203.png]]

- to expand Alex Net
- GoogleNet
- inception Module
- VGGnet
- RESNET
- RESIDUAL LEARNING 
- DENSENET
- 