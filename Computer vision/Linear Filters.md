- linear filters 
- spatial domain vs frequency domain 
- convolution filter 
- ideal low and high filter , butterworth filter , gaussian filter 


# Linear Filters
weighted average of the samples in the window where the set of weights is called: **filter mask **
# Spatial Filter 
Filtering in the Spatial domain 
The output is typically a function of the samples in a window surrounding the considered pixel

#### Separable filters 
-  a filter is separable if $w(x,y)=w_x(x)w_y(y)$
- invariant to row and columns application 
- $O(MN(a+b))$ instad of $O(MNab)$ : **faster** 
###### ex Convolution separable filter
	![[Pasted image 20240114141501.png]]
##### 2D Convolution 
essentially the multiplication of a window times a constant between $[0,1]$ 
 ![[Pasted image 20240114142118.png]]
- 2D convolution in the spatial domain 
- essentially a low pass filter 
- reduces noise 
- destroys small details 
##### 1D Convolution 
essentially the same of the [[#2D Convolution]] but only by windows made of a row or a column


# Frequency Domain 
![[Pasted image 20240114142613.png]]
1. Implicit periodicity: **wraparound error**
	   ![[Pasted image 20240114142859.png]]
	   ![[Pasted image 20240114143007.png]]
2. Transformation function H(u,v) typically specified for spectrum centered in (M/2,N/2) 
3. Need zero phase shift filter $\rightarrow$ h() is even $\rightarrow$ can't be casual 
4. Images are functions with real values


## Padding
tecnique used to avoid wrap around errors
### 1D
- Image $f(x)$ : length A 
- Filter $h(x)$: length C
 ![[Pasted image 20240114143253.png]]
**Pad both image and filter to length P**
$P\geq A+C-1$ 
![[Pasted image 20240114143551.png]]
For faster computation it is possible to pad only the image but in this case some wrap around error remains
		

## 2D 
![[Pasted image 20240114144103.png]]
- Image $f(x,y)$ : length AxB
- Filter $h(x,y)$: length CxD
**Pad in both dimensions to**
$P\geq A+C-1$
$Q\geq B+D-1$
![[Pasted image 20240114144055.png]]

### Ringing 
![[Pasted image 20240114144723.png]]
is an after effect of the [[#Padding]] 


## Filtering in the frequency domain 
### Input 
- Image: $f(x,y)$ size MxN
  ![[Pasted image 20240114145516.png]]
- filter: $H(u,v)$ size PxQ
- output $g(x,y)=f(x,y)*h(x,y)$
## Procedure
1. Padding (P=2M,Q = 2N)
   ![[Pasted image 20240114150039.png]]
2. Multiply for $(-1)^{x+y}$ to center the FT
   ![[Pasted image 20240114150047.png]]
3. Compute the DFT $F(u,v)$
   ![[Pasted image 20240114150116.png]]
4. Get filter response $H(u,v)$ of size PxQ
   ![[Pasted image 20240114150134.png]]
5. G = FH
   ![[Pasted image 20240114150145.png]]
6. antitranfrom G and and reset the center
   $g_p(x,y)=[Re[ F^{-1}(G(u,v)) ] ](-1)^{x+y}$
   ![[Pasted image 20240114150155.png]]
7. plot only the real part of the upper-left MxN region 
   ![[Pasted image 20240114150206.png]]

## Types of filters in the frequency domain 

### Ideal Low-pass filter
![[Pasted image 20240114152447.png]]
- Response depends only on distance from the center(circular simmetry)
- Ideal filter: spatial response has infinite length
- Perfect frequency section 
- Ringing artifacts
- Single param : cut-off freq
![[Pasted image 20240114153432.png]]
### Butterworth Low Pass Filter
![[Pasted image 20240114153049.png]]
- the ringing effect grows with the order of the filter 
- n$\rightarrow \infty$ is closer to a low pass filter
- $n$ is the order 
- $D_0$ is the cut-off frequency
![[Pasted image 20240114153450.png]]
# Gaussian Filter 
![[Pasted image 20240114154010.png]]
- no [[#Ringing]]
- not very precise in frequecny selection 
- very commonly used in practice
 
 ## Spatial vs Frequency Representation 
![[Pasted image 20240114153729.png]]
![[Pasted image 20240114154116.png]]

#### Low pass sumup
![[Pasted image 20240114154143.png]]
### High pass Filters (sharpening)
![[Pasted image 20240114154255.png]]
#### Spatial domain 
![[Pasted image 20240114154438.png]]
![[Pasted image 20240114154707.png]]
## Band Pass 
![[Pasted image 20240114154759.png]]