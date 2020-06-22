---
layout: post
title: Machine Learning with Python
date: 2018-01-14
published: true
---

There are countless tutorials for machine learning, however, I couldn't find one which could take me through the steps of not just the code but also of the math behind it. So here it goes.

To begin with, it is important to understand the concept of machine learning. Machine learning is a field of artificial intelligence, focused on training algorithms to (1) decipher patterns within data and (2) make predictions based on these patterns.

Amazon uses machine learning to make recommendations based on your past browsing history, Gmail uses machine learning to classify emails as spam or not-spam, and banks use machine learning to detect fraudulent transactions.

In essence, machine learning is nothing but a combination of various algorithms, such as: <br>
i.    Linear Regression <br>
ii.   Logistic Regression <br>
iii.  Decision Trees <br>
iv.   K-Nearest Neighbors <br>
v.    K-Means Clustering, among others.

In this story, I will be talking about a few of these algorithms, including the logic behind each of them. The first project that we shall work on is a classification project, using a public dataset called Iris. This is a very popular dataset, widely used in data science for explaining and demonstrating concepts.

After installation of python (3.6) and a text editor (I use atom), the first step towards evaluating the dataset is importing the various libraries, all part of the SciPy platform. The best way to do this is by running the following script, by typing it in a text editor, saving the file in a xyz.**py** format, and then calling it in the terminal by a simple $ python xyz.py command.

```python
import sys
print('Python: {}'.format(sys.version))
import scipy
print('scipy: {}'.format(scipy.__version__))
import numpy
print('numpy: {}'.format(numpy.__version__))
import matplotlib
print('matplotlib: {}'.format(matplotlib.__version__))
import pandas
print('pandas: {}'.format(pandas.__version__))
import sklearn
print('sklearn: {}'.format(sklearn.__version__))
```

##### Loading Data<br>
To load data from the Iris dataset into terminal, the following code would work. This can be used for any data import from the web or from a local directory.

```python
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data"
names = ['sepal-length', 'sepal-width', 'petal-length', 'petal-width', 'class']
dataset = pandas.read_csv(url, names=names)
print(dataset)
```

In line 3 of above script, we are instructing python to read the csv file at given url, name the columns as per listed 'names', and then save the data as 'dataset'. In line 4, we are instructing python to print the dataset. Since the dataset is pretty big, terminal would not print the entire thing but would give the first 30 and last 30 rows, along with the size of the table in the end as [150 rows x 5 columns].

##### Summarizing Data<br>
It is always a good idea to start the analysis with a summary of every dataset, and python makes it very easy with the following simple and self explanatory command:

```python
print(dataset.describe())
```

This would give the following result which is very useful in understanding the dataset:

|      | sepal-length | sepal-width | petal-length | petal-width |
|------|--------------|-------------|--------------|-------------|
|count |   150.000000 |  150.000000 |   150.000000 |  150.000000 |
|mean  |     5.843333 |    3.054000 |     3.758667 |    1.198667 |
|std   |     0.828066 |    0.433594 |     1.764420 |    0.763161 |
|min   |     4.300000 |    2.000000 |     1.000000 |    0.100000 |
|25%   |     5.100000 |    2.800000 |     1.600000 |    0.300000 |
|50%   |     5.800000 |    3.000000 |     4.350000 |    1.300000 |
|75%   |     6.400000 |    3.300000 |     5.100000 |    1.800000 |
|max   |     7.900000 |    4.400000 |     6.900000 |    2.500000 |


##### Visualizing Data <br>
After getting a grasp of the data, it would be useful to visualize each input variable with the help of box-plots and histograms. To do this, we run the following script:

```python
import matplotlib.pyplot as plt
dataset.plot(kind='box', subplots=True, layout=(2,2), sharex=False, sharey=False)
plt.show()

dataset.hist()
plt.show()
```
To get the following results: <br>
<a href="/images/posts/Figure_1.png"><img src="/images/posts/Figure_1.png"></a> <br>

<a href="/images/posts/Figure_2.png"><img src="/images/posts/Figure_2.png"></a>

After visualizing each variable individually, we shall create *multivariate* plots: scatterplots for all pairs of attributes, in order to identify relationships between these variables.

```python
scatter_matrix(dataset)
plt.show()
```
Result: <br>
<a href="/images/posts/Figure_3.png"><img src="/images/posts/Figure_3.png"></a>

The grouping of points on scatterplots for certain pairs of attributes shows a high correlation. This prompts us to go further with our evaluation.

##### Creating and Fitting Models<br>
This is the most important step in the entire process. It begins with separating out the data into a training set and a validation set, running statistical methods on the test data, and then selecting the best fitting model based on evaluation on the validation data. It is usual practice to divide the dataset into 80:20 where 80% of the data is used to train the models and 20% is used for validation. Python gives a simple way of doing this:

```python
from sklearn import model_selection
from sklearn.metrics import classification_report
from sklearn.metrics import confusion_matrix
from sklearn.metrics import accuracy_score

array = dataset.values
X = array[:,0:4]
Y = array[:,4]
validation_size = 0.20
seed = 7
X_train, X_validation, Y_train, Y_validation = model_selection.train_test_split(X, Y, test_size=validation_size, random_state=seed)

scoring = 'accuracy'
```

After creating the training dataset and validating it using the scoring command, we shall run and evaluate each of the algorithms with which we wish to test our data. Python makes this very easy too, and because of this ease, we can build as many algorithms as we want with just a line of code as shown below:

```python
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.neighbors import KNeighborsClassifier
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis
from sklearn.naive_bayes import GaussianNB
from sklearn.svm import SVC

models = []
models.append(('LR', LogisticRegression()))
models.append(('LDA', LinearDiscriminantAnalysis()))
models.append(('KNN', KNeighborsClassifier()))
models.append(('CART', DecisionTreeClassifier()))
models.append(('NB', GaussianNB()))
models.append(('SVM', SVC()))

results = []
names = []
for name, model in models:
	kfold = model_selection.KFold(n_splits=10, random_state=seed)
	cv_results = model_selection.cross_val_score(model, X_train, Y_train, cv=kfold, scoring=scoring)
	results.append(cv_results)
	names.append(name)
	msg = "%s: %f (%f)" % (name, cv_results.mean(), cv_results.std())
	print(msg)
```

This script throws the following result, with the value outside bracket giving the mean of accuracy and the value inside bracket for standard deviation of accuracy:

```python
LR: 0.966667 (0.040825)
LDA: 0.975000 (0.038188)
KNN: 0.983333 (0.033333)
CART: 0.983333 (0.033333)
NB: 0.975000 (0.053359)
SVM: 0.991667 (0.025000)
```

