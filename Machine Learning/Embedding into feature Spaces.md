

Define a **non-linear** mapping 𝜓 ∶ 𝒳 → ℱ such that $F$ is a new Feature Space

$F$  is usually $R^{\,n}$ for some $n$ but can be an arbitrary Hilbert Space (even with $|F|  = \infty$)

$𝑆 = ((𝒙_𝟏, 𝑦_1) ,… , (𝒙_𝒎, 𝑦_𝑚))$  --F→ $𝑆^{'} = ( (𝜓(𝒙_𝟏) ,𝑦_1),… , (𝜓 (𝒙_𝒎) , 𝑦_𝑚))$





idea: 
- apply a non linear transformation to each point in the training set
- learn a linear predictor in the transformad space 
- make prediction for a new instance

SOLUTION:
Embedding into feature Spaces 
Define a non-linear mapping 𝜓 from the input space to a new (typically larger) space
1. Given a domain set 𝒳 and a learning task, find a mapping to a new feature space ℱ 𝜓 ∶ 𝒳 → ℱ • ℱ is usually ℝ 𝑛 for some n but can be an arbitrary Hilbert space (even of infinite size) 
2. Given a sequence of labeled examples 𝑆 = ( 𝒙𝟏, 𝑦1 ,… , (𝒙𝒎, 𝑦𝑚)) map them to 𝑆 = (𝜓 𝒙𝟏 , 𝑦1 ,… , (𝜓 𝒙𝒎 , 𝑦𝑚)) 
3. Train a linear predictor h over 𝑆መ 4. Predict the label of 𝒙 as ℎ(𝜓 𝒙 )

FIND 𝜓 (x) is a very computational intesive task that can be worked around with  [[Kernel-based learning#Kernel trick | kernel trick]]

