implementatio of siren optimized for the gpu 
TO DO : 

1. probabli to apply somenthing from this i need some course in reinforcement learning
1. PROBLEM OF USING K MEANS: how to tell that that pixel belongs to a cluster? 
		 if we use 1 nn for predicting the values for each  cluster we need also find a way to tell when ouputting each pixel to wich cluster belongs (ex pixel 523 is assigned to cluster 1 and need to be predicted with nn_predicting cluster 1, this one will have in input only the number of the pixel (of the complete image, or relative to the selected cluster ex or the 512 if the image or the 12 of the cluster)
		 Another simpler alternative could be to only insert the number of the cluster into as a feature inside a single nn that memorize the whole image instead of training multiple nn(remember occam razor) 

2. also can be useful change the type of clustering (we don't care to make clusters of similar colors, we care about making clusters that allow us to reduce to the minimum the error when training)
		
		 

	
	  
	  (enche memorizing in some way the "shape of the cluster") and than when outputting from the nn for that cluster we need a map that says wich pixel belongs to which cluster
1. try using a different coordinate dimentsion (actual is a 2d coordinate system (why not use only 1) or use more? maybe for the index of clustering ? )
2. augment the size of the image
3. another idea is using kmeans to find the best stuff to memorize and than use only that
4. Augment the  data of the image by looping it  or by serving each pixel in a different order
5. look at actual ways to memorize an image 
6. CHANGE THE SHAPE OF THE NETWORK to **speed up the training** with gpu (make test rig for chainging the shape and confront it with the original structure)
	   
	   i think i need to experiment with different shapes but seem that can be a problem 
	   of scaling the a proportion of a structure of the image keeping the details in 
	   such as 


![[Pasted image 20240211223339.png]]

how much we set the first layers tells us how much **big** details we want from the image  and the smaller ones how much **small** details we want from the image , 

Scaling all the layers allow us to scale the whole number of neurons without losing the proportion of details 

Others to do    
2. think about the size to respect to each pixel and in respect to a jpeg image and how to ouput 
3. make a test rig with error differences from the original implementation 
4. start to think how to output the pixels as a file
5. use a denoiser to avoid strange things
6. can be useful to think to a data augmentation trick to speed up the training on gpu(fill the dataset with a repeated image)
7. HOW TO COMPRESS THE WEIGHTS (can we have a tradeoff between the size of the weights and the precision that we are getting?)


# results 300 iteration vs 100 our 
# increase batch size
the aumgment of the batch size din't increase the speed of training of the net
# scaling the network
major factor of speed up was the change of the net from by adding new neuron keeping the same structure only streching the number of neurons along the y axis 
  
``` python 

mult = 2

learn = Learner(

    dls,
	#from
    #siren_model([2, 256, 128, 64, 32, 3]).cuda(),
	#to 
    siren_model([2, 256*mult, 128*mult, 64*mult, 32*mult, 3]).cuda(),
	
	#as if a scaling
  

    loss_func=MSELossFlat(),

    opt_func=ranger,

)
```

as a scaling 


# IDEA 

1. use the average color of the image and compute the difference for each pixel  with the average 
2. train the net with the differences associated with each pixel 
3. than reconstruct the image by using the average pixel and the differece given by the net







