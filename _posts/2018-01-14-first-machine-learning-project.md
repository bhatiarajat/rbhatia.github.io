---
layout: post
title: Machine Learning with Python
date: 2018-01-14
---

There are countless tutorials for machine learning, however, I couldn't find one which could take me through the steps of not just the code but also of the math behind it. So here it goes.

To begin with, it is important to understand the concept of machine learning. Machine learning is a field of artificial intelligence, focused on training algorithms to (1) decipher patterns within data and (2) make predictions based on these patterns.

Amazon uses machine learning to make recommendations based on your past browsing history, Gmail uses machine learning to classify emails as spam or not-spam, and banks use machine learning to detect fraudulent transactions.

In essence, machine learning is nothing but a combination of various algorithms, such as: <br>
i. Linear Regression <br>
ii. Logistic Regression <br>
iii. Decision Trees <br>
iv. K-Nearest Neighbors <br>
v. K-Means Clustering, among others.

In this story, I will be talking about a few of these algorithms, including the logic behind each of them. The first project that we shall work on is a classification project, using a public dataset called Iris. This is a very popular dataset, widely used in data science for explaining and demonstrating concepts.

After installation of python (3.6) and a text editor (I use atom), the first step towards evaluating the dataset is importing the various libraries, all part of the SciPy platform. The best way to do this is by running the following script, by typing it in a text editor, saving the file in a xyz.**py** format, and then calling it in the terminal by a simple \\>>>python xyz.py\\ command.

```
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
