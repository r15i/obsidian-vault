We have to choose among multiple possible hypotheses set ℋ𝑖 Approach → split the data in 3 parts: 
1. Training set: used to learn the best model ℎ𝑖 𝐸𝑅𝑀 inside each class ℋ𝑖 
2. Validation set: used to pick one hypothesis ℎ ∗ from ℎ1, ℎ2, … .
3. Test set: used to estimate the true risk 𝐿𝐷(ℎ ∗ ) 

so we have 3 types of sets
![[Pasted image 20231124215330.png]]
training set to train 

validation set to pick a h* from h_1.....

test set to estimate the true risk L_D(h*)


The estimate from the test set has the guarantees provided by the proposition on estimate of 𝐿𝐷(ℎ ∗ ) for one class 
The test set is not involved in the choice of ℎ ∗ 
if after using the test set to estimate 𝐿𝐷(ℎ ∗ ) we decide to choose another hypothesis (because we have seen 𝐿𝐷(ℎ ∗ ) ...) we cannot use the test set again to estimate 𝐿𝐷(ℎ ∗ ) 

who to spare data and keep this validation? [[K-fold cross Validation]]
