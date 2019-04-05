---
layout: post
category: software
class: Machine Learning
title: Scikit-learn Basics for Machine Learning
description: Understand what is machine learning, what not is machine learning and learn the basics of Scikit-learn using Python.
author: Gogul Ilango
permalink: /software/sk-learn-ml-basics
image: https://drive.google.com/uc?id=19uk0Myc4a0H6vx4K4K7Z_zB4Smkv_NpB
---

<div class="sidebar_tracker" id="sidebar_tracker">
  <button onclick="closeSidebar('sidebar_tracker_content')">X</button>
  <p onclick="showSidebar('sidebar_tracker_content')">Contents</p>
  <ul id="sidebar_tracker_content">
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_1" href="#what-is-machine-learning">What is Machine Learning</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_2" href="#what-is-not-machine-learning">What is not Machine Learning?</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_3" href="#types-of-machine-learning">Types of Machine Learning</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_4" href="#what-is-scikit-learn">What is Scikit-learn?</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_5" href="#quick-example">Quick example</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_6" href="#commonly-used-functions">Commonly used functions</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_7" href="#how-to-start-ml">How to start ML?</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_8" href="#resources">Resources</a></li>
  </ul>
</div>

<p class="hundred-days"><span>#100DaysOfMLCode</span></p>

In this blog post, we will learn the basics of machine learning and scikit-learn. We will understand different types of machine learning algorithms and finally build our first machine learning model using scikit-learn and Python.

<h3 id="what-is-machine-learning">What is Machine Learning?</h3>
According to Wikipedia, [Machine Learning](https://en.wikipedia.org/wiki/Machine_learning){:target="_blank"} is a subset of artificial intelligence in the field of computer science that often uses statistical techniques to give computers the ability to "learn" (i.e., progressively improve performance on a specific task) with data, without being explicitly programmed.

According to Tom Mitchell, "A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

From an implementation perspective, machine learning is the beautiful process of
* Gathering real-world data and processing it for machines to understand.
* Building a model (algorithm) based on the problem to solve.
* Training the model with the gathered data (training data).
* Making the model understand the underlying patterns or structure in the past data.
* Predicting the future outcomes using the trained model on unseen data.

<figure>
  <img class="typical-image" src="/images/software/machine-learning/ml-sk-learn-basics/ml_intro.png">
  <figcaption>Figure 1. Machine Learning - Introduction</figcaption>
</figure>

<h3 id="what-is-not-machine-learning">What is not Machine Learning?</h3>
There is a misconception that machine learning means fully automated algorithm or a machine is capable to program themselves on their own without any human help. It's not! Machine Learning is a semi-automated process where human intelligence plays a crucial role.
* ML is not a fully automated process.
* ML is not a replacement for programming.
* ML is not an easy task as you might think.
* ML is not a solution to every problem in the industry.

<h3 id="types-of-machine-learning">Types of Machine Learning</h3>

#### 1. Supervised Learning
  * Data with clearly defined output is provided for the model.
  * Model is built to learn explicitly from training data and labels.
  * Solves classification (output is a category) and regression (output is a real value) problems.
  * *Classification algorithms*: Decision Trees, Random Forests, Support Vector Machines, Logistic Regression, Linear Discriminant Analysis, k-Nearest Neighbors, Naive Bayes.
  * *Regression algorithms*: Linear Regression, Ridge Regression, LASSO Regression, Elastic Net Regression, k-Nearest Neighbors, Decision Trees, Support Vector Machines. 

> In supervised learning, the model needs to learn a mapping function between the input data (X) and the output prediction (Y).

<figure>
  <img class="typical-image" src="/images/software/machine-learning/ml-sk-learn-basics/supervised-learning.png">
  <figcaption>Figure 2. Supervised Learning</figcaption>
</figure>

#### 2. Unsupervised Learning
  * Training data is provided without the output for the model.
  * Model understands the data and identifies pattern or structure in the data.
  * *Algorithms*: K-means clustering, Hierarchical clustering, Gaussian mixture models, Self-organizing maps, Hidden Markov models.

> In unsupervised learning, the model needs to find the underlying pattern or structure in the data using only the input data (X).

<figure>
  <img class="typical-image" src="/images/software/machine-learning/ml-sk-learn-basics/unsupervised-learning.png">
  <figcaption>Figure 3. Unsupervised Learning</figcaption>
</figure>


#### 3. Semi-supervised Learning
  * It is a technique that sits between supervised and unsupervised learning.
  * Some training data is defined with output for the model.
  * Both supervised and unsupervised algorithms can be used here.
  * As labelling data is a time-consuming task, majority of real-world problems belong to this category.

> In semi-supervised learning, the model is provided with partially labelled training data (X) to find the mapping function for output prediction (Y) or to find the underlying pattern or structure in the data.

<h3 id="what-is-scikit-learn">What is Scikit-learn?</h3>
Machine Learning in Python becomes a breeze with the help of [scikit-learn](http://scikit-learn.org/stable/index.html){:target="_blank"} library. Scikit-learn is built on the Scientific Python compute stack which includes NumPy, SciPy, matplotlib and Pandas. It provides a wide range of supervised and unsupervised machine learning algorithms using Python as we discussed above.

<h3 id="quick-example">Quick example</h3>

Models (or algorithms) in scikit-learn are implemented with the following core functions.
* <span class="coding">fit</span> - Trains a model.
* <span class="coding">predict</span> - Predicts the output for one or more instances using the trained model.
* <span class="coding">predict_proba</span> - Predicts the probability of all classes for one or more instances (classification) using the trained model.
* <span class="coding">transform</span> - Preprocesses the training data (i.e normalize or scale the data).

Below is a simple supervised classification example using scikit-learn. It uses the famous [iris dataset](https://en.wikipedia.org/wiki/Iris_flower_data_set){:target="_blank"} (provided as a [toy dataset](http://scikit-learn.org/stable/datasets/index.html){:target="_blank"} by scikit-learn), trains a decision tree classifier, make predictions on the training dataset itself and exports the decision tree as an image to understand how the algorithm works behind the scenes.

<div class="code-head">iris_demo.py<span>code</span></div>

```python
# organize imports
from sklearn import datasets
from sklearn import metrics
from sklearn.tree import DecisionTreeClassifier
from sklearn.tree import export_graphviz
import pydot
from sklearn import tree
import os

# load the iris dataset
train_data = datasets.load_iris()
print ("[INFO] train features shape : {}".format(train_data.data.shape))
print ("[INFO] train label shape    : {}".format(train_data.target.shape))
print ("[INFO] classes              : {}".format(train_data.target_names))

# define the model
model = DecisionTreeClassifier()

# fit the model
model.fit(train_data.data, train_data.target)

# predict using model
expected  = train_data.target
predicted = model.predict(train_data.data)

# analyze the metrics of the model
print ("[INFO] displaying classification_report and confusion_matrix")
print(metrics.classification_report(expected, predicted))
print(metrics.confusion_matrix(expected, predicted))

# visualize the tree
with open("iris_tree.dot", "w") as f:
	f = tree.export_graphviz(model, out_file=f)
os.system ('dot -Tpng iris_tree.dot -o iris_tree.png')
```

* Lines 2-8 imports all the necessary packages to be used. Line 4 imports the Decision Tree classifier algorithm in scikit-learn. Line 5 imports the package for visualizing the decision tree after training.
* Line 11 loads the iris dataset provided as a toy dataset in scikit-learn. As these are numpy arrays, you can check the shape of these 2d-arrays as shown in lines 12-14.
* Line 17 defines the decision tree classifier model.
* Line 20 fits the training data and corresponding training labels to the decision tree model.
* Line 23 stores the training labels as <span class="coding">expected</span> and line 24 demands the model to predict the output on training data itself.
* Line 27-29 displays the performance of the decision tree model using <span class="coding">classification_report()</span> and <span class="coding">confusion_matrix()</span> offered by scikit-learn.
* Line 32-34 outputs the decision tree as an image using <span class="coding">expor_graphviz()</span>.

Open up a text editor, insert the python code given above and name it as <span class="coding">iris_demo.py</span>. Run it using a command prompt and you will get the following results.

<div class="code-head">Output<span>terminal</span></div>

```
[INFO] train features shape : (150, 4)
[INFO] train label shape    : (150,)
[INFO] classes              : ['setosa' 'versicolor' 'virginica']
[INFO] displaying classification_report and confusion_matrix
             precision    recall  f1-score   support

          0       1.00      1.00      1.00        50
          1       1.00      1.00      1.00        50
          2       1.00      1.00      1.00        50

avg / total       1.00      1.00      1.00       150

[[50  0  0]
 [ 0 50  0]
 [ 0  0 50]]
```

<figure>
	<img class="typical-image" src="/images/software/machine-learning/ml-sk-learn-basics/iris_tree.png">
	<figcaption>Figure 1. Decision Tree for Iris Dataset</figcaption>
</figure>


<h3 id="commonly-used-functions">Commonly used functions</h3>

Most of the functions in scikit-learn revolve around preprocessing data, feature selection, model selection, instantiating model and performance metrics. Following code snippets displays the commonly used scikit-learn functions to solve a machine learning problem.

<div class="code-head">machine learning models<span>imports</span></div>

```python
# classification models
from sklearn.svm import SVC
from sklearn.linear_model import LogisticRegression
from sklearn.linear_model import PassiveAggressiveClassifier
from sklearn.linear_model import RidgeClassifier
from sklearn.linear_model import RidgeClassifierCV
from sklearn.linear_model import SGDClassifier
from sklearn.naive_bayes import GaussianNB
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis
from sklearn.neighbors import KNeighborsClassifier
from sklearn.neighbors import RadiusNeighborsClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.tree import ExtraTreeClassifier
from sklearn.gaussian_process import GaussianProcessClassifier
from sklearn.multiclass import OneVsRestClassifier
from sklearn.multiclass import OneVsOneClassifier
from sklearn.multiclass import OutputCodeClassifier
from sklearn.multioutput import ClassifierChain
from sklearn.multioutput import MultiOutputClassifier
from sklearn.neural_network import MLPClassifier

# regression models
from sklearn.linear_model import LinearRegression
from sklearn.linear_model import Lasso
from sklearn.linear_model import Ridge
from sklearn.linear_model import PassiveAggressiveRegressor
from sklearn.linear_model import HuberRegressor
from sklearn.linear_model import ElasticNet
from sklearn.linear_model import RANSACRegressor
from sklearn.linear_model import SGDRegressor
from sklearn.linear_model import TheilSenRegressor
from sklearn.tree import DecisionTreeRegressor
from sklearn.tree import ExtraTreeRegressor
from sklearn.neighbors import KNeighborsRegressor
from sklearn.neighbors import RadiusNeighborsRegressor
from sklearn.svm import SVR
from sklearn.gaussian_process import GaussianProcessRegressor
from sklearn.multioutput import MultiOutputRegressor
from sklearn.neural_network import MLPRegressor

# ensemble classification models
from sklearn.ensemble import RandomForestClassifier
from sklearn.ensemble import AdaBoostClassifier
from sklearn.ensemble import VotingClassifier
from sklearn.ensemble import BaggingClassifier
from sklearn.ensemble import ExtraTreesClassifier
from sklearn.ensemble import GradientBoostingClassifier

# ensemble regression models
from sklearn.ensemble import RandomForestRegressor
from sklearn.ensemble import GradientBoostingRegressor
from sklearn.ensemble import ExtraTreesRegressor
from sklearn.ensemble import AdaBoostRegressor
from sklearn.ensemble import BaggingRegressor
from sklearn.ensemble import ExtraTreesRegressor
```

<div class="code-head">model selection<span>imports</span></div>

```python
from sklearn.model_selection import train_test_split
from sklearn.model_selection import cross_val_score
from sklearn.model_selection import KFold
from sklearn.model_selection import LeaveOneOut
from sklearn.model_selection import ShuffleSplit
from sklearn.model_selection import GridSearchCV
```

<div class="code-head">preprocessing data<span>imports</span></div>

```python
from sklearn.preprocessing import MinMaxScaler
from sklearn.preprocessing import Normalizer
from sklearn.preprocessing import Binarizer
from sklearn.preprocessing import StandardScaler
from sklearn.preprocessing import Imputer
from sklearn.preprocessing import OneHotEncoder
from sklearn.preprocessing import LabelEncoder
```

<div class="code-head">feature selection<span>imports</span></div>

```python
# principle component analysis
from sklearn.decomposition import PCA

# univariate selection
from sklearn.feature_selection import SelectKBest
from sklearn.feature_selection import chi2

# recursive feature elimination
from sklearn.feature_selection import RFE
```

<div class="code-head">metrics<span>imports</span></div>

```python
from sklearn.metrics import confusion_matrix
from sklearn.metrics import classification_report
from sklearn.metrics import mean_squared_error
```

<h3 id="how-to-start-ml">How to start ML?</h3>

Few of the challenging decisions in ML are choosing the right Machine Learning model for a problem based on problem type and amount of data. Fortunately, there is a [cheat sheet](http://scikit-learn.org/dev/tutorial/machine_learning_map/index.html){:target="_blank"} built by [Andreas C. Muller](http://amueller.github.io/){:target="_blank"} to select a machine learning model based on the amount of data and the problem type. This cheat sheet could be used as a beginner's step on solving a machine learning problem using scikit-learn. 

<figure>
  <img class="typical-image" src="/images/software/machine-learning/ml-sk-learn-basics/ml_map.png">
  <figcaption>Figure 2. Machine Learning Scikit-learn Cheat Sheet</figcaption>
</figure>

In addition, the cheat sheets given below are provided by [DataCamp](https://www.datacamp.com/){:target="_blank"} which are much useful if you wanna quickly use the scientific python stack.
* [Scikit-learn cheat sheet](https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Scikit_Learn_Cheat_Sheet_Python.pdf){:target="_blank"}
* [NumPy cheat sheet](https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Numpy_Python_Cheat_Sheet.pdf){:target="_blank"}
* [SciPy cheat sheet](https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Python_SciPy_Cheat_Sheet_Linear_Algebra.pdf){:target="_blank"}
* [Pandas cheat sheet](https://s3.amazonaws.com/assets.datacamp.com/blog_assets/PandasPythonForDataScience.pdf){:target="_blank"}
* [matplotlib cheat sheet](https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Python_Matplotlib_Cheat_Sheet.pdf){:target="_blank"}

<h3 id="resources">Resources</h3>

1. [Scikit-learn official page](http://scikit-learn.org/stable/index.html){:target="_blank"}
2. [An introduction to machine learning with scikit-learn](http://scikit-learn.org/stable/tutorial/basic/tutorial.html){:target="_blank"}
3. [Machine Learning in Python with scikit-learn](https://www.youtube.com/playlist?list=PL5-da3qGB5ICeMbQuqbbCOQWcS6OYBr5A){:target="_blank"}
4. [Scikit-learn Machine Learning with Python and SKlearn](https://www.youtube.com/playlist?list=PLQVvvaa0QuDd0flgGphKCej-9jp-QdzZ3){:target="_blank"}
5. [Machine Learning with Scikit-Learn](https://www.youtube.com/playlist?list=PLonlF40eS6nynU5ayxghbz2QpDsUAyCVF){:target="_blank"}
6. [Machine Learning with scikit-learn - Andreas Mueller & Alexandre Gram](https://www.youtube.com/watch?v=2kT6QOVSgSg){:target="_blank"}
7. [Deploying scikit learn models in production](https://www.youtube.com/watch?v=AwjeRg1u5VI){:target="_blank"}
8. [Deploying Python Machine Learning Models in Production](https://www.youtube.com/watch?v=6TI-gQhsf40){:target="_blank"}