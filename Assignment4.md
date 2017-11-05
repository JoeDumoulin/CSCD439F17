# CSCD439- Fall 2017
# Assignment 4 - Predicting Hand-Written Digits Again!

In this assignment, you will use numpy, scikit-learn, and tensorflow to predict which digit is contained in pictures of hand-written digits.  This is a classic benchmark for multiclass learning.

Start by starting up your ubuntu system.  Start the virtual environment, and then create a folder for this assignment.

## Getting the Data

Next download the files found on [Yann Lecunn's webpage](http://yann.lecun.com/exdb/mnist/).  Download all four files.  Copy these files to your assignment folder.

Next, uncompress the files using the following command:

```
gunzip *-ubyte.gz
```

In order to use these files in a python script, we need to install the idx2numpy python module.  Be sure you have a terminal window with your virtual environment activated.  In this terminal, enter the following command line:

```
pip install idx2numpy
```


## Installing tensorflow in your vm

You can pretty easily add tensorflow to your vm to support some small deep learning projects.  Follow the instructions below.

First open a terminal in your vm and do 

```
sudo apt-get update
sudo apt-get upgrade
```

Next, make sure you are in a terminal in your virtual environment.  Mine is called "test" so I start with:

```
source test/bin/activate
```

Next, install tensorflow:

```
pip install --upgrade tensorflow
```

Test your installation with the following code (in a python repl or in a notebook):

```
import tensorflow as tf
hello = tf.constant('Hello, TensorFlow!')
sess = tf.Session()
print(sess.run(hello))
```

The output should be:

```
b'Hello, TensorFlow!'
```

## The Assignment itself
Create a notebook to contain your code.  Use idx2numpy to read the data.  you will want something lie this:

```
import idx2numpy

X_train = idx2numpy.convert_from_file('train-images-idx3-ubyte')
y_train = idx2numpy.convert_from_file('train-labels-idx1-ubyte')
X_test = idx2numpy.convert_from_file('t10k-images-idx3-ubyte')
y_test = idx2numpy.convert_from_file('t10k-labels-idx1-ubyte')
```

Be sure to check the shape of these matrices and remember to flatten the X matrices (use `reshape`) before trying to fit or predict from them.

You will use scikit learn to create some models of MNIST.  In each of the MLP cases, use `MPLClassifier` class with the following parameters:
```
mlp = MLPClassifier(solver='lbfgs', alpha=1e-5, hidden_layer_sizes=(<as specified below>), random_state=1)
```

    1. Logistic regression (be sure to use solver='lbfgs' for this as the default solver will take --forever-- to run)
    2. One hidden layer MLP with 50 nodes
    3. One hidden layer MLP with 100 nodes
    4. One hidden layer MLP with 400 nodes
    5. Two hidden layers MLP with 100 and 50 nodes respectively

In each of the 5 cases above, print the confusion matrix,the accuracy and the `classification_report`.

Questions:
1. Which model gives the best accuracy?  Which the best overall F1 score?
2. Which model gives the worst accuracy?  Which the worst overall F1 score?
3. What is the shape of the training set?  How many nodes are in the input layer of the network?
4. Look the documentation for MLPClassifier.  Why are we using lbfgs solver?  Look up l-bfgs and provide a description of what it does.
5. Why do you think the best/worst networks are that way?
6. Experiment and try to create a better performing network using tensorflow.  Explain what you tried and document the results.







