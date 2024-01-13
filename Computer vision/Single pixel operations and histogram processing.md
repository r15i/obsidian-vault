
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
The intesity of a pixel in the ouput image is a function $s = T(r)$ of only the corresponding pixel in the  input image
![[Pasted image 20240113135317.png]]
- **Negative** Trasformation: with $r,s \in [0,L-1]$
	   $s = T(r)=(L-1)-r$ 
	
- **Gamma** Trasformation:
  
- Contrast streching 
- Histogram equalization


- histograms
- Equalization/specifications
# Operations on the neighborhood of a point
- Linear and non linear filters
- 