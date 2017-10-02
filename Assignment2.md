# CSCD439- Fall 2017
# Assignment 2 - Predicting King County Housing Prices

In this assignment, you will use pandas, statsmodels, and scikit-learn to predict housing prices in different areas o fKing County, Washington based on actual data of home sales in 2014-2015.  This assignment comprises three parts:

1. Download and check the data for issues.  Prepare the data for training.  Create some basic plots to view the data and understand potentially dependant features.
2. Create a model using some subset of the data.  Hold out part of the data so that you can use it for validation.  Create this regression model using only one feature (the "sqft_living" feature for example) and the price of the home.  Identify the accuracy of the resulting model using the held-out data.  Identify the weights learned by the model.
3. Re-create the model using multiple features.  Check the model using a held out set of data as before.  Compare the results.  Print some plots showing the statistical quality of the model.

Here are some guidelines for getting started.

### Getting the Data
download the data from [kaggle](https://www.kaggle.com/harlfoxem/housesalesprediction/data) as a csv file.  

### Download the housing data
From your ubuntu system, use the browser to download the data for the housing as above.  Copy the zip file ```housesalesprediction.zip``` from your Dowload folder to your project folder.  then unzip the file: ```unzip housesalesprediction.zip```.

### Start your virtual environment
Now open a terminal session and start you virtual environment.  If you have created a virtul environment 

### Create a Jupyter Notebook for the Assignment
Go to your virtualenv project folder and start ```jupyter notebook```.  In the browser window that opens up, create a new notebook and do your work on the created page.

Start by opening the data file on the notebook and checking its shape.

![jupyter notebook](https://github.com/JoeDumoulin/CSCD439F17/blob/master/images/2017-10-01T12.15.28PM.png "Check the shape of house sales data")

Check the columns that were imported with this data set:

```df.columns```

You can check the meaning of each column label [on the kaggle site](https://www.kaggle.com/harlfoxem/housesalesprediction/data).

Another thing to do is to plot the scatter of each pair of columns.  This can tell you if you have certain data that highly predicts other data or that will make a good part of the regression.

```
import matplotlib.pyplot as plt
from pandas.plotting import scatter_matrix

# you can exclude some rows which may not fit in the regression.
testdf = df.drop(['id', 'date', 'zipcode', 'lat', 'long'], axis=1)
scatter_matrix(testdf, figsize=(16,16), diagonal='kde')
plt.show()
```

Finally, check the data for missing values:

```
nulldf = df.isnull()
nulldf.sum(axis=0)
```

**The first task in the homework is to answer the following questions:**

* Is there any data missing (Nan)?  If so, how would you remove it?
* What columns appear to offer the best hope of a linear approximation?
* Which columns data are categorical?  Which are numerical?
* Which is the "best" column to use for prediction?  This is a judgement call, but I'd like to know how you justify it.

**To complete the second task**, you will want to select one of the columns to use to try to predict price.  You will see how to measure the accuracy of the model using a test set created from the full data set.

In order to train the regression model, you need to change the data from a pandas DataFrame or Series type to a numpy vector.  For example, you may choose "grade" as a predictor of price.  Then you will do something like this:

```
#load data 
import pandas as pd
df = pd.read_csv('kc_house_data.csv')

# make the predictor matrix and label vector
X = df[['grade']].as_matrix()  # This will change to whatever column you are using
y = df[['price']].as_matrix()
```
Next you will want to create an object that will contain the model you train.

```
# make the linear regression object
from sklearn.linear_model import LinearRegression
lr = LinearRegression()
```
Next, split the data into training data and testing data.  This randomly separates 20% of the X and y values for testing the model

```
# split the data for validation
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
```

Next, train the model:

```
lr.fit(X_train, y_train)
```

Check the weights created for the model.

```

```

Questions for this part of the exercise are:

* How might you choose which column is best for the predictive model?
* Can you compare the quality of the different columns as predictors before you train a model?  How? 
* how many rows are in the training data?  How many rows in the test data?


**The final part of the exercise