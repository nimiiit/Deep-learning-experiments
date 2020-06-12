# Autoencoders

Autoencoders (AE) are unsupervised learning techniques used for representation learning from the data (for dimentionality reduction). It is unsupervised because the input and output to AEs are the same and there is no extra labeling as in classification required to train such a network.

There are different types of AE in literature and we will try to cover some of it in the next project. 
Here we concentrate on multi-layer perceptron (MLP) based simple AE (consisting of an encoder and decoder as shown below). It intakes an image and using the encoder map it to a latent space which is of a much lower dimension than that of the input data. The decoder then maps from this compressed latent space back to the input space. The ideal goal is to recover back the input image.
<img width="679" alt="Capture1" src="https://user-images.githubusercontent.com/9528369/84504633-e3ec0d00-acd9-11ea-8eb4-3d2e8682e183.PNG">

pic credit: https://towardsdatascience.com/deep-inside-autoencoders-7e41f319999f

The model is trained with a mean squared (MSE) loss which indcates how close the decoded image is to the actual input image.
If no activation functions are used (like 'relu', 'tanh' etc) which introduce non-linearity to the network, the AE can be considered equivalent to Principal component analysis (PCA).

## What does the code section cover
* Define a MLP based AE architecture with Encoder and Decoder
* Load the MNIST dataset and reshape it into vectors for the architecture compatiibility
* Define the training parameters like loss functions,learning rate, optimizers, batch size and the number of epochs that you want to train your network for
* We also have a parameter called bottleneck size which indicates the size of the latent representation

 -- The more you reduce it,the more compression you achieve but then there will be a reduction in the quality of the reconstricted image
* Train the model 
* Next we plot the inputs and the reconstructed outputs for the test set and see the performance of our model
* To give more intution on the image space and latent space, we next do a TSNE plot of both

-- TSNE plots are a way to represent the high dimensional data in a 2 or 3d space by preserving the inter datapoints distances.
Read more on TSNE : https://towardsdatascience.com/t-sne-python-example-1ded9953f26

-- Observation: We expect the encoded latent space to a good compressed representation of our data with least redundancy. Hence the classes should have better separability than in the image space. Even in the TSNE plot we can see this reflected.

* Next we move on to the latent space and try to see what happens if we linearly interpolate the latent vectors. The same interpolation is performed in the image space as well.

-- Observation: As image in interpolated we see a gosty transition from one image to another, while in the latent space the interpolation when decoded you see that the transition is very smooth. 
I got inspired to try this out after reading the article in :  https://hackernoon.com/latent-space-visualization-deep-learning-bits-2-bd09a46920df

-- Input space interpolation
<img src="inputinterpolation.gif?raw=true" width="200px">

--Latent space interpolation
<img src="latentsinterpolation.gif?raw=true" width="200px">





 
     
