[[Unsupervised learning]] technique

# Dimensionality Reduction
![[Pasted image 20240109115131.png]]
![[Pasted image 20240109115624.png]]

Take data from **highly** dimensional space and project to a lower dimensional one 

Lower dimensional data should be a **good Approximation** of the higher dimensional representations
## Good approximation 
minimize error obtained by re projecting the data back to the high dimensional space ($\rightarrow$ like a lossy compression)
LOWER dimensional data should allow for reconstructing the original data with a reasonable accuracy



Focus on on **linear mapping** of the data (represented by a matrix multiplication)

### Application 
- reduce number of feature 
- Capture most important aspects of the data for subsequent analysis
- Data visualization
By reducing dimensinality part of the information get lost

# Principal Component Analysis (PCA)
find the linear mapping that minimizes the mean squared error in the re projection when dimensionally reducing 


![[Pasted image 20240109120402.png]]
![[Pasted image 20240109120632.png]]
![[Pasted image 20240109120655.png]]
![[Pasted image 20240109120712.png]]
![[Pasted image 20240109120850.png]]
![[Pasted image 20240109121015.png]]
## Application
![[Pasted image 20240109120954.png]]

![[Pasted image 20240109120932.png]]