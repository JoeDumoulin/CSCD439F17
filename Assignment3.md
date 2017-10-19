# CSCD439- Fall 2017
# Assignment 3 - Predicting Hand-Written Digits

In this assignment, you will use pandas, statsmodels, and scikit-learn to predict which digit is contained in pictures of hand-written digits.  This is a classic benchmark for multiclass learning.

Start by starting up your ubuntu system.  Start the virtual environment, and then create a folder for this assignment.

Next start a new jupyter notebook in the new folder you created.  At the top of the folder, load the following code:

```
from sklearn.datasets import load_digits
digits = load_digits()
print(digits.data.shape)
```
When you run this block, you should see:

```
(1797, 64)
```

Next, display one of the digits:

```
import matplotlib.pyplot as plt 
plt.gray() 
plt.matshow(digits.images[3]) 
plt.show() 
```

You will see an 8x8 pixel image of the hand-written digit.  The loaded data set has 1794 examples.

Once you have loaded the data correctly, you will need to separate the predictor from the response data:

```
images_and_labels = list(zip(digits.images, digits.target))


for index, (image, label) in enumerate(images_and_labels[:4]):
    plt.subplot(2, 4, index + 1)
    plt.axis('off')
    plt.imshow(image, cmap=plt.cm.gray_r, interpolation='nearest')
    plt.title('Training: %i' % label)

plt.show()
```

You should see a couple of numbers and the label.

Next, we need to flatten the 8X8 image into 64 int inputs:

```
# flatten the image.
# turn the data into a (samples, feature) matrix:
n_samples = len(digits.images)
data = digits.images.reshape((n_samples, -1))
```
Separate the data into training and testing groups.

For the remainder of the assignment, look at the documentation for [LogisticRegression in sckit-learn](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html), and use that class to create a model from the prepared data above.

Next, use the [sklearn metrics](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html) module to calculate and display the confusion matrix.

Answer the following questions:

Which digits are most often confused by the model? 
What is the accuracy of the model?
Which digits are most often reognized correctly?
Which are recognized incorrectly?









