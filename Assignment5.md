# CSCD439- Fall 2017
# Assignment 5 - Predicting Hand-Written Digits with Convolutional Networks

In this assignment, you will use tensorflow to build a Convolutional Neural Network to build a predictor for MNIST.  You should use the MNIST data available through tensorflow.


To complete this assugnment, you will want to do something like the network described [here](https://www.tensorflow.org/tutorials/layers).  

Try at least two different networks.  This may be a little difficult, but persist!  Getting results from a network like this is the key to building deeper systems.

Some possible things to try:

* A single conv2d layer with one pooling layer, a fully connencted layer, and a softmax layer.
* Two conv2d layers, one pooling layer, one fully connected layer, and a softmax layer.

There are many other things you can try as well.

You can build these models using either tensorflow or keras.  be careful! if your network is too deep it may run very slowly.

Find the results of the model using sklearn.metrics tools as with previous exercises.  You should show the precision, recall, f1, and the confusion matrix.

Questions to answer.

* how many hidden layers are in your network?
* how many convolutions are calculated in each convolution layer?
* run a single test example through the model and print some of the convolved images from the first layer.  Can you see any features from the image that are revealed by printing?
* Print  couple of the convolution kernels as matrices (no need to print images).  What kind of patterns can you see in the convolution kernels?


