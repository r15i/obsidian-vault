
## Noise Models
- Gaussian 
- Rayleigh 
- Gamma 
- Exponential 
- Uniform 
- Salt & Pepper
# Based on order statistics 
### Median filter
prende il valore mediano di una window (only parameter)
	![[Pasted image 20240114155750.png]]
  NB : Destroys structures smaller than half of the window size   
### Min-max filter 
prende il valore massimo o minimo di una window (only parameter)
![[Pasted image 20240114160033.png]]
# Advanced edge-preserving filtering techniques 
### Bilateral filter 
Is a Smooting filter that allows us to preserve the edges

- Smoothing = making adjacent pixel similar
- Smoothing strategy $\rightarrow$ weighted average of its neighbors
### Simple average of a window
![[Pasted image 20240114160410.png]]

## Box Profile 
![[Pasted image 20240114160435.png]]
generates defects:
- Axis-aligned streaks 
- Blocky results 
solutions (Gaussian blur):
- isotropic window (i.e circular)
- smooth falloff (gaussian window)

## Gaussian Blur
![[Pasted image 20240114160646.png]]
![[Pasted image 20240114160704.png]]
![[Pasted image 20240114161027.png]]
![[Pasted image 20240114161105.png]]


## Properties of Gaussian Blur 
- linear convolution 
- well-known operation
- efficient computation (recursive algorithm, FFT...)

- smooths also the edges 
- No edge term 
![[Pasted image 20240114161840.png]]
## Bilateral filter 
- No Averaging across Edges 
![[Pasted image 20240114161926.png]]
![[Pasted image 20240114161940.png]]
![[Pasted image 20240114162250.png]]
![[Pasted image 20240114162300.png]]


