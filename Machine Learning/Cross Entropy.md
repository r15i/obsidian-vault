Used in NN  for classification task the **cross entropy** is commonly used in place of [[0-1 loss]] 

for binary classification:
$L(f(x),y)=-ylog(f(x))-(1-y)log(1-f(x))$

The optimal $f(x)$ minimizing this loss function is $f(x)= P(y=1 |x)$, we are training the neural net output to **estimate conditional probabilities**

- works only for $f(x)\,\,\rightarrow\,[0,1]$ , undefined or infinite value would arise 
- To achieve this, the [[Loss Function#Common loss Functions|sigmoid]] is commonly used as activation for the output layer
- the functon is convex $\rightarrow$ works well with [[Gradient Descent (GD)]]

presented later in the course