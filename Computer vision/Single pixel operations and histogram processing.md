
# Geometric transform 
A geometric transform modify the spatial ralationships between the image pixels
steps:
1. Spatial transform of the coordinates   $$(x,y)=T{(v,w)}$$
2. A resampling of the pixels values to compute the new image values

## Affine Transforms 
a linear transform followed by a translation such as rotation,translation and scaling

### Single Matrix Rappresentation 
Homogeneus coordinates allow to rappresent both linear tranformation and translation in a single matrix 


![[Pasted image 20240113133551.png]]

![[Pasted image 20240113133820.png]]
## Forward and Backward mapping
![[Pasted image 20240113133928.png]]

# Single-pixel operations
## Intensity tranforms
The intesity of a pixel in the ouput image is a function
$s = T(r)$ of only the corresponding pixel in the input image
- L rappresent the intensity level with regards to the pixel intensity ex $L/2$ half the intesity
![[Pasted image 20240113154854.png]]

###  **Negative** Trasformation: with $r,s \in [0,L-1]$
	   $s = T(r)=(L-1)-r$ 
### **Gamma** Trasformation:
**can be used to enhance details in the very bright**
returns   $s = cr^{\gamma}$ wich is a function of $\gamma$     
from the constraints on max level $L-1 = c(L-1)^{\gamma}\implies c = (L-1)^{1-\gamma}$ 
Luminous intesity of monitor and cameras  $I = V^{\gamma}$
![[Pasted image 20240113155552.png]]
##### Different effects of gamma
- with $\gamma<1\rightarrow$ image gets brighter (we are in the second half upper half of the graph) 
- with $\gamma>1\rightarrow$ image gets darker (we are in the lower half of the image)	
### **Contrast** stretching 
Allows to improve the **dynamic range of images**
(needs to be **tuned**)
**Dynamic range**:  the interval between the highest grey scale value and the lowest 
- high dynamic range $\rightarrow$  high contrast
- low dynamic range $\rightarrow$ poor contrast
**Continuos curve**
   ![[Pasted image 20240113155001.png]]
   **Sampled as**
   ![[Pasted image 20240113160935.png]]
   
### **Thresholding** function 
![[Pasted image 20240113155053.png]]
### Histogram equalization
##### *Normalized* Histogram : 
- $r_k$ intesity of level in the image
- $h(r_k)=n_k$ number of pixels with intesity equal to $r_k$
$$p(r_k) = \frac{h(r_k)}{MN} = \frac{n_k}{MN}$$similar to a PDF function, and used for : image statistics, Compression, Segmentation, **image enhancement**

#### histogram Equalization/specifications![[Pasted image 20240113162029.png]]
Transform the intensity values in order to obtain an histogram as flat as possible 
##### Invertible 
This transform is invertible only if strictly monotonically increasing (if not i would have no clue where other pixel would go)	
	 ![[Pasted image 20240113162315.png]]
	Only for : 	
		1. $T(r)$ monotonic not decreasing 
		2. $0\leq T(r) \leq L-1$ for $0\leq r \leq L-1$
		3. $T(r)$ continuous and differentiable 
#### Equalization function 
1. realization of a random variable $r$ representing the intensity value for each pixel  as such $p_r(r)\rightarrow s=T(r)\rightarrow p_s(s)$ 
2. from probability theory we have that : 
   - given $T(r)$ continuous and differentiable $\rightarrow \exists T'(r)=\frac{ds}{dr}$ 
       $\downarrow$
   - $p_s(s) = p_r(r)|\frac{dr}{ds}|$
3. Consider the following $T(r)$ function (that is multiplied by the **Cumulative Distributon Function,CDF**)
   $$s = T(r) = (L-1)\int_0^r{p_r(w)\,\,dw}$$

	satisfies 3 conditions: 
	- it is **positive** as integral of a positive function 
	- area below the PDF IS 1 $\rightarrow$ T(L-1) = L-1
	- it is derivable since is just a constant * the integral 

![[Pasted image 20240113164852.png]]
#### Equalization Function: Discrete Case
![[Pasted image 20240113164931.png]]
![[Pasted image 20240113170703.png]]
#### Example of histogram equalization 
![[Pasted image 20240113171442.png]]
here: 
- $r_k$ is the possible levels  
- $n_k$ number of instance 
- $p_r(r_k)= n_k/MN$ 
- $s_i$ is the corresponding intensity 
#### Histogram specification 
Allows to bring different PDF , probability distributions in different images 
#### Continuous Case:
$p_r(r)$ Normalized histogram of the input image 
$p_z(z)$: target normalized histo
1. Equalize input image: $s = T(r)=(L-1)\int_0^r{p_r(w)dw}$ 
2. Compute G(z): function that equalizes $p_z(z)$
	   $G(z) = (L-1)\int_0^z{p_z(t)dt}=s$ (same uniform distribution)
3. G(z) and s : same uniform distribution (the inverse is not always doable )
	   $s = T(r) = G(z) \rightarrow z = G^{-1}(T(r))$
4. Apply $G^{-1}$ to the equalized image $T(r)$
#### Discrete Case:
$p_r(r_j)$ Normalized histogram of the input image 
$p_z(z_q)$: target normalized histo
1. Equalize input image: $s_k = T(r_k)=(L-1)\sum^q_{i=0}p_r(r_j)=\frac{L-1}{MN}\sum^k_{j=0}n_j$ 
   (same distribution) 
2. Compute G(z): function that equalizes $p_z(z_q)$ (target)
	   $G(z_q) = (L-1)\sum_0^q{p_z(z_i)}(same uniform distribution)
3. G(z) and s : same uniform distribution (the inverse is not always doable )
	   $G(z_q)=s_k \rightarrow z_q = G^{-1}(s_k) = G^{-1}(T(r_k))$
   ![[Pasted image 20240113173619.png]]
   
   ![[Pasted image 20240113173706.png]]
   ![[Pasted image 20240113173746.png]]
![[Pasted image 20240113173825.png]]
#### Histogram Specification example 
![[Pasted image 20240113173928.png]]

![[Pasted image 20240113174240.png]]


### HISTOGRAM EXCERCIZE
![[Pasted image 20240113174432.png]]![[Pasted image 20240113174449.png]]
![[Pasted image 20240113174500.png]]


#### Processing based on the neighbourhood of a pixel 
- [[Linear Filters]]
- [[non-Linear Filters]]
