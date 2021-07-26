# Fashion_MNIST_ConvNet

The first layer uses 64 fairly large filters (7x7) but no stride since the input images are not very large. It also set the input shape as [28, 28, 1] since the images are monochromatic so only one channel.
Next we have a max pooling layer with a pooling size of 2. It divides the spatial dimensions of the image by a factor of 2.
Then we have repeat the same structure twice: two conv. layers followed by a max pooling layer. For larger images, we could repeat this structure several more times. the no. of repetitions is hyperparameter we can tune.
Note that the no. of filters grows as we climb up the network towards the output layer. It makes sense for it to grow as the no. of low level features are fairly low, whereas there are many different ways to combine them into high level features. It is a common practice to double the no.. of filters after each pooling layer. Since the pooling layer reduces the dimensions by a factor of two, we can increase the no. of filters without the fear of exploding the no. of parameters, memory usage or computational load.
Next is the fully connected network, composed of two hidden dense layers and a dense output layer. Note that we must flatten its inputs, since a dense network expects a 1D array of features for each instance. We have also addded 2 dropout layers with dropout rate of 50% to reduce overfitting.

# LeNet-5

![image](https://user-images.githubusercontent.com/44425260/126954549-9d5c28c2-9815-4bf9-bdd7-4ce2a143f463.png)


Most widely known CNN architecture. The MNIST images are 28x28 pixels but they are zero padded to 32x32 pixels and normalized before being fed to the network. the rest of the network doesn't use any padding, thats why the size of the image keeps shrinking as it progresses through the network.
The average pooling layers are complex than usual. Each neuron computes the mean of its inputs, then multiplies it by a learnable coefficient (one per map) and add it to a learnable bias (also one per map), then finally applies the activation function.
Most neurons in C3 maps are connected to only three or four of the neurons in S2 maps(instead of all 6)
In the ouput layer instead of computing the matrix multiplication of the input and weight vector, it outputs the Euclidian distance between the input and the weight vector. Each output measure how much the image belongs to a particular digit class. thus crossentropy cost func is much preferred as it penalizes the wrong predictions much more, thus creating larger gradients and converging faster.
