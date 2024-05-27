![[IMG-20240302-WA0001.jpg]]

the point is to find the weights that aren't that important (aka we have a good tradeoff between the loss of precision and the ability to compress such weights)


and convert this into a linear programmig problem to give this to a resolver 

- tips: probably would be easier to find a good idea in a 3 layer setup
- tips 2 : the weight effect need to be on the average of the sample we have since is a product of $a_i w_{j,i}$ enche is dependent on the activation of the sample in cause

- 

