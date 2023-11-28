Kernel: inner product in the [[Embedding into feature Spaces| feature space]]

GENERIC 
Kernel function $𝐾 (𝒙, 𝒙′) =< 𝜓 (𝒙) , 𝜓 (𝒙′) >$



$𝐾()$: represent similarity of the samples in a space where the similarities are realized as inner products

Key Result: machine learning algorithms for halfspaces can be carried out just on the basis of the values of the kernel function without explicitly representing the points in the feature space 
Sometimes we can compute (in a faster way) 𝐾 (𝒙, 𝒙 ′) without explicitly computing 𝜓(𝒙) and 𝜓 (𝒙 ′)


# Kernel trick
![[Pasted image 20231127154424.png]]

COMPUTING $\psi(x)$ requires $\theta(d^2)$ time 
computing $K_{\psi}(x,x')$ from the last formula requires $\theta(d)$ 
when this is applicable for the kernel we don't need to calculate $\psi$






