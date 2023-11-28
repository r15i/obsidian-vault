![[Pasted image 20231124153318.png]]


Steps to utilize: 
1. Partition(training ) set of m samples into k folds of size m/k 
2. for each fold : 
   - train on the union of the other folds
   -  Estimate error (for learned hypothesis) on the selected fold
3. estimate the true error as the average of the estimated errors

Model Selection with Cross Validation 
![[Pasted image 20231124160205.png]]




Error decomposition
![[Pasted image 20231124215641.png]]


 

