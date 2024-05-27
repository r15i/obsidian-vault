	
	 ![[Pasted image 20231124161309.png]]
	![[Pasted image 20231127152303.png]]
	![[Pasted image 20231127152333.png]]

# Algorithm for Failed Learning

1. if there are tuned parameters , plot model-selection curve to make sure they are tuned appropriately

2. if **training error**   is excessively **large** consider:
   - enlarge hypothesis class $H$
   - change hypothesis class $H$
   - change feature representation of the data
   
3. if  $𝐿_𝑆(ℎ_𝑠)$ **training error** is small, use learning curves to understand whether problem is  $𝐿_D(ℎ_*)$ **approximation error** or **estimation error** ($𝐿_𝐷(ℎ_𝑠) − 𝐿_𝐷(ℎ_∗)$ ) :

   - if $𝐿_𝑉(ℎ𝑠)$ **validation error** seems to decrease (the error is large but the 2 curves get closer):
     -- get more data(if possible)
     -- reduce complexity of $H$
     
   - if the $𝐿_𝑉(ℎ𝑠)$ **validation error** remains large :
	 -- change $H$
	 -- change feature representation of the data