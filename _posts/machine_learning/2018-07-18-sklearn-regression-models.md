---
layout: post
category: software
class: Machine Learning 
title: Regression Models in Scikit-learn
description: Learn and understand the different regression models (algorithms) offered by scikit-learn to do Machine Learning.
author: Gogul Ilango
permalink: /software/sklearn-regression-models
image: https://drive.google.com/uc?id=1ECABtqd8BFW-2jBYMTMwvQ-CyMWRz-nV
---

<div class="sidebar_tracker" id="sidebar_tracker">
  <button onclick="closeSidebar('sidebar_tracker_content')">X</button>
  <p onclick="showSidebar('sidebar_tracker_content')">Contents</p>
  <ul id="sidebar_tracker_content">
  		<li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_1" href="#adaboostregressor">AdaBoostRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_2" href="#baggingregressor">BaggingRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_3" href="#decisiontreeregressor">DecisionTreeRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_4" href="#extratreeregressor">ExtraTreeRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_5" href="#extratreesregressor">ExtraTreesRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_6" href="#gaussianprocessregressor">GaussianProcessRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_7" href="#gradientboostingregressor">GradientBoostingRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_8" href="#huberregressor">HuberRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_9" href="#kneighborsregressor">KNeighborsRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_10" href="#mlpregressor">MLPRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_11" href="#multioutputregressor">MultiOutputRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_12" href="#passiveaggresiveregressor">PassiveAggresiveRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_13" href="#radiusneighborsregressor">RadiusNeighborsRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_14" href="#randomforestregressor">RandomForestRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_15" href="#ransacregressor">RANSACRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_16" href="#sgdregressor">SGDRegressor</a></li>
      <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_17" href="#theilsenregressor">TheilSenRegressor</a></li>
	</ul>
</div>

<p class="hundred-days"><span>#100DaysOfMLCode</span></p>

In machine learning, regression problems go hand in hand with classification problems. If you see the trend between <span class="coding">regression</span> and <span class="coding">classification</span> over the past 5 years, both have similar interest worldwide. In this page, I have collected all the available <span class="coding">regression</span> algorithms implemented in scikit-learn so that we can use it quickly and get to know the available algorithms easily.

<script type="text/javascript" src="https://ssl.gstatic.com/trends_nrtr/1480_RC02/embed_loader.js"></script> <script type="text/javascript"> trends.embed.renderExploreWidget("TIMESERIES", {"comparisonItem":[{"keyword":"regression machine learning","geo":"","time":"today 5-y"},{"keyword":"classification machine learning","geo":"","time":"today 5-y"}],"category":0,"property":""}, {"exploreQuery":"date=today%205-y&q=regression%20machine%20learning,classification%20machine%20learning","guestPath":"https://trends.google.com:443/trends/embed/"}); </script> 

### AdaBoostRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.AdaBoostRegressor.html){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/ensemble/weight_boosting.py#L853){:target="_blank"}

<div class="code-head">usage<span>code</span></div>

```python
from sklearn.ensemble import AdaBoostRegressor
model = AdaBoostRegressor(base_estimator=None, n_estimators=50, learning_rate=1.0, loss=’linear’, random_state=None)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">base_estimator</span>, <span class="coding">n_estimators</span>, <span class="coding">learning_rate</span>, <span class="coding">loss</span>, <span class="coding">random_state</span>.
</li>
<li><b>Attributes</b>: <span class="coding">estimators_</span>, <span class="coding">estimator_weights_</span>, <span class="coding">estimator_errors_</span>, <span class="coding">feature_importances_</span>
</li>
</ul>

---

### BaggingRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.BaggingRegressor.html#sklearn.ensemble.BaggingRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/ensemble/bagging.py#L797){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.ensemble import BaggingRegressor
model = BaggingRegressor(base_estimator=None, n_estimators=10, max_samples=1.0, max_features=1.0, bootstrap=True, bootstrap_features=False, oob_score=False, warm_start=False, n_jobs=1, random_state=None, verbose=0)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">base_estimator</span>, <span class="coding">n_estimators</span>, <span class="coding">max_samples</span>, <span class="coding">max_features</span>, <span class="coding">bootstrap</span>, <span class="coding">bootstrap_features</span>, <span class="coding">oob_score</span>, <span class="coding">warm_start</span>, <span class="coding">n_jobs</span>, <span class="coding">random_state</span>, <span class="coding">verbose</span>.
</li>
<li><b>Attributes</b>: <span class="coding">estimators_</span>, <span class="coding">estimators_samples_</span>, <span class="coding">estimators_features_</span>, <span class="coding">oob_score_</span>, <span class="coding">oob_prediction_</span>.
</li>
</ul>

---

### DecisionTreeRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeRegressor.html#sklearn.tree.DecisionTreeRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/tree/tree.py#L873){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.tree import DecisionTreeRegressor
model = DecisionTreeRegressor(criterion=’mse’, splitter=’best’, max_depth=None, min_samples_split=2, min_samples_leaf=1, min_weight_fraction_leaf=0.0, max_features=None, random_state=None, max_leaf_nodes=None, min_impurity_decrease=0.0, min_impurity_split=None, presort=False)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">criterion</span>, 
                  <span class="coding">splitter</span>,
                  <span class="coding">max_depth</span>,
                  <span class="coding">min_samples_split</span>,
                  <span class="coding">min_samples_leaf</span>,
                  <span class="coding">min_weight_fraction_leaf</span>,
                  <span class="coding">max_features</span>,
                  <span class="coding">random_state</span>,
                  <span class="coding">max_leaf_nodes</span>,
                  <span class="coding">min_impurity_decrease</span>,
                  <span class="coding">min_impurity_split</span>,
                  <span class="coding">presort</span>
</li>
<li><b>Attributes</b>: <span class="coding">feature_importances_</span>,
                  <span class="coding">max_features_</span>,
                  <span class="coding">n_features_</span>,
                  <span class="coding">n_outputs_</span>,
                  <span class="coding">tree_</span>
</li>
</ul>

---

### ExtraTreeRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.tree.ExtraTreeRegressor.html#sklearn.tree.ExtraTreeRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/tree/tree.py#L1306){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.tree import ExtraTreeRegressor
model = ExtraTreeRegressor(criterion=’mse’, splitter=’random’, max_depth=None, min_samples_split=2, min_samples_leaf=1, min_weight_fraction_leaf=0.0, max_features=’auto’, random_state=None, min_impurity_decrease=0.0, min_impurity_split=None, max_leaf_nodes=None)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">criterion</span>,
                  <span class="coding">splitter</span>,
                  <span class="coding">max_depth</span>,
                  <span class="coding">min_samples_split</span>,
                  <span class="coding">min_samples_leaf</span>,
                  <span class="coding">min_weight_fraction_leaf</span>,
                  <span class="coding">max_features</span>,
                  <span class="coding">random_state</span>,
                  <span class="coding">min_impurity_decrease</span>,
                  <span class="coding">min_impurity_split</span>,
                  <span class="coding">max_leaf_nodes</span>
</li>
</ul>

---

### ExtraTreesRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.ExtraTreesRegressor.html#sklearn.ensemble.ExtraTreesRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/ensemble/forest.py#L1501){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.ensemble import ExtraTreesRegressor
model = ExtraTreesRegressor(n_estimators=10, criterion=’mse’, max_depth=None, min_samples_split=2, min_samples_leaf=1, min_weight_fraction_leaf=0.0, max_features=’auto’, max_leaf_nodes=None, min_impurity_decrease=0.0, min_impurity_split=None, bootstrap=False, oob_score=False, n_jobs=1, random_state=None, verbose=0, warm_start=False)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">n_estimators</span>,
                  <span class="coding">criterion</span>,
                  <span class="coding">max_features</span>,
                  <span class="coding">max_depth</span>,
                  <span class="coding">min_samples_split</span>,
                  <span class="coding">min_samples_leaf</span>,
                  <span class="coding">min_weight_fraction_leaf</span>,
                  <span class="coding">max_leaf_nodes</span>,
                  <span class="coding">min_impurity_split</span>,
                  <span class="coding">min_impurity_decrease</span>,
                  <span class="coding">bootstrap</span>,
                  <span class="coding">oob_score</span>,
                  <span class="coding">n_jobs</span>,
                  <span class="coding">random_state</span>,
                  <span class="coding">verbose</span>
</li>
<li><b>Attributes</b>: <span class="coding">estimators_</span>,
                  <span class="coding">feature_importances_</span>,
                  <span class="coding">n_features_</span>,
                  <span class="coding">n_outputs_</span>,
                  <span class="coding">oob_score_</span>,
                  <span class="coding">oob_prediction_</span>
</li>
</ul>

---

### GaussianProcessRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.gaussian_process.GaussianProcessRegressor.html#sklearn.gaussian_process.GaussianProcessRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/gaussian_process/gpr.py#L21){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.gaussian_process import GaussianProcessRegressor
model = GaussianProcessRegressor(kernel=None, alpha=1e-10, optimizer=’fmin_l_bfgs_b’, n_restarts_optimizer=0, normalize_y=False, copy_X_train=True, random_state=None)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">kernel</span>,
                  <span class="coding">alpha</span>,
                  <span class="coding">optimizer</span>,
                  <span class="coding">n_restarts_optimizer</span>,
                  <span class="coding">normalize_y</span>,
                  <span class="coding">copy_X_train</span>,
                  <span class="coding">random_state</span>
</li>
<li><b>Attributes</b>: <span class="coding">X_train_</span>,
                  <span class="coding">y_train_</span>,
                  <span class="coding">kernel_</span>,
                  <span class="coding">L_</span>,
                  <span class="coding">alpha_</span>,
                  <span class="coding">log_marginal_likelihood_value_</span>
</li>
</ul>
---

### GradientBoostingRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingRegressor.html#sklearn.ensemble.GradientBoostingRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/ensemble/gradient_boosting.py#L1640){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.ensemble import GradientBoostingRegressor
model = GradientBoostingRegressor(loss=’ls’, learning_rate=0.1, n_estimators=100, subsample=1.0, criterion=’friedman_mse’, min_samples_split=2, min_samples_leaf=1, min_weight_fraction_leaf=0.0, max_depth=3, min_impurity_decrease=0.0, min_impurity_split=None, init=None, random_state=None, max_features=None, alpha=0.9, verbose=0, max_leaf_nodes=None, warm_start=False, presort=’auto’)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">loss</span>,
                  <span class="coding">learning_rate</span>,
                  <span class="coding">n_estimators</span>,
                  <span class="coding">max_depth</span>,
                  <span class="coding">criterion</span>,
                  <span class="coding">min_samples_split</span>,
                  <span class="coding">min_samples_leaf</span>,
                  <span class="coding">min_weight_fraction_leaf</span>,
                  <span class="coding">subsample</span>,
                  <span class="coding">max_features</span>,
                  <span class="coding">max_leaf_nodes</span>,
                  <span class="coding">min_impurity_split</span>,
                  <span class="coding">min_impurity_decrease</span>,
                  <span class="coding">alpha</span>,
                  <span class="coding">init</span>,
                  <span class="coding">verbose</span>,
                  <span class="coding">warm_start</span>,
                  <span class="coding">random_state</span>,
                  <span class="coding">presort</span>
</li>

<li><b>Attributes</b>: <span class="coding">feature_importances_</span>,
                  <span class="coding">oob_improvement_</span>,
                  <span class="coding">train_score_</span>,
                  <span class="coding">loss_</span>,
                  <span class="coding">init</span>,
                  <span class="coding">estimators_</span>
</li>
</ul>

---

### HuberRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.HuberRegressor.html#sklearn.linear_model.HuberRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/linear_model/huber.py#L125){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.linear_model import HuberRegressor
model = HuberRegressor(epsilon=1.35, max_iter=100, alpha=0.0001, warm_start=False, fit_intercept=True, tol=1e-05)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">epsilon</span>,
                  <span class="coding">max_iter</span>,
                  <span class="coding">alpha</span>,
                  <span class="coding">warm_start</span>,
                  <span class="coding">fit_intercept</span>,
                  <span class="coding">tol</span>
</li>
<li><b>Attributes</b>: <span class="coding">coef_</span>,
                  <span class="coding">intercept_</span>,
                  <span class="coding">scale_</span>,
                  <span class="coding">n_iter_</span>,
                  <span class="coding">outliers_</span>
</li>
</ul>

---

### KNeighborsRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsRegressor.html#sklearn.neighbors.KNeighborsRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/neighbors/regression.py#L19){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.neighbors import KNeighborsRegressor
model = KNeighborsRegressor(n_neighbors=5, weights=’uniform’, algorithm=’auto’, leaf_size=30, p=2, metric=’minkowski’, metric_params=None, n_jobs=1, **kwargs)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">n_neighbors</span>,
                  <span class="coding">weights</span>,
                  <span class="coding">algorithm</span>,
                  <span class="coding">leaf_size</span>,
                  <span class="coding">p</span>,
                  <span class="coding">metric</span>,
                  <span class="coding">metric_params</span>,
                  <span class="coding">n_jobs</span>
</li>
</ul>

---

### MLPRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPRegressor.html#sklearn.neural_network.MLPRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/neural_network/multilayer_perceptron.py#L1061){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.neural_network import MLPRegressor
model = MLPRegressor(hidden_layer_sizes=(100, ), activation=’relu’, solver=’adam’, alpha=0.0001, batch_size=’auto’, learning_rate=’constant’, learning_rate_init=0.001, power_t=0.5, max_iter=200, shuffle=True, random_state=None, tol=0.0001, verbose=False, warm_start=False, momentum=0.9, nesterovs_momentum=True, early_stopping=False, validation_fraction=0.1, beta_1=0.9, beta_2=0.999, epsilon=1e-08)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">hidden_layer_sizes</span>,
                  <span class="coding">activation</span>,
                  <span class="coding">solver</span>,
                  <span class="coding">alpha</span>,
                  <span class="coding">batch_size</span>,
                  <span class="coding">learning_rate</span>,
                  <span class="coding">learning_rate_init</span>,
                  <span class="coding">power_t</span>,
                  <span class="coding">max_iter</span>,
                  <span class="coding">shuffle</span>,
                  <span class="coding">random_state</span>,
                  <span class="coding">tol</span>,
                  <span class="coding">verbose</span>,
                  <span class="coding">warm_start</span>,
                  <span class="coding">momentum</span>,
                  <span class="coding">nesterovs_momentum</span>,
                  <span class="coding">early_stopping</span>,
                  <span class="coding">validation_fraction</span>,
                  <span class="coding">beta_1</span>,
                  <span class="coding">beta_2</span>,
                  <span class="coding">epsilon</span>
</li>
<li><b>Attributes</b>: <span class="coding">loss_</span>,
                  <span class="coding">coefs_</span>,
                  <span class="coding">intercepts_</span>,
                  <span class="coding">n_iter_</span>,
                  <span class="coding">n_layers_</span>,
                  <span class="coding">n_outputs_</span>,
                  <span class="coding">out_activation_</span>
</li>
</ul>

---

### MultiOutputRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.multioutput.MultiOutputRegressor.html#sklearn.multioutput.MultiOutputRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/multioutput.py#L201){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.multioutput import MultiOutputRegressor
model = MultiOutputRegressor(estimator, n_jobs=1)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">estimator</span>,
                  <span class="coding">n_jobs</span>
</li>
</ul>

---

### PassiveAggresiveRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.PassiveAggressiveRegressor.html#sklearn.linear_model.PassiveAggressiveRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/linear_model/passive_aggressive.py#L228){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.linear_model import PassiveAggressiveRegressor
model = PassiveAggressiveRegressor(C=1.0, fit_intercept=True, max_iter=None, tol=None, shuffle=True, verbose=0, loss=’epsilon_insensitive’, epsilon=0.1, random_state=None, warm_start=False, average=False, n_iter=None)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">C</span>,
                       <span class="coding">fit_intercept</span>,
                       <span class="coding">max_iter</span>,
                       <span class="coding">tol</span>, 
                       <span class="coding">shuffle</span>,
                       <span class="coding">verbose</span>,
                       <span class="coding">loss</span>,
                       <span class="coding">epsilon</span>,
                       <span class="coding">random_state</span>,
                       <span class="coding">warm_start</span>,
                       <span class="coding">average</span>,
                       <span class="coding">n_iter</span>
</li>
<li><b>Attributes</b>: <span class="coding">coef_</span>,
                       <span class="coding">intercept_</span>,
                       <span class="coding">n_iter_</span>
</li>
</ul>

---

### RadiusNeighborsRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.neighbors.RadiusNeighborsRegressor.html#sklearn.neighbors.RadiusNeighborsRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/neighbors/regression.py#L168){:target="_blank"}

<div class="code-head">usage<span>code</span></div>

```python
from sklearn.neighbors import RadiusNeighborsRegressor
model = RadiusNeighborsRegressor(radius=1.0, weights=’uniform’, algorithm=’auto’, leaf_size=30, p=2, metric=’minkowski’, metric_params=None, **kwargs)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">radius</span>,
                       <span class="coding">weights</span>,
                       <span class="coding">algorithm</span>,
                       <span class="coding">leaf_size</span>,
                       <span class="coding">p</span>,
                       <span class="coding">metric</span>,
                       <span class="coding">metric_params</span>
</li>
</ul>

---

### RandomForestRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html#sklearn.ensemble.RandomForestRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/ensemble/forest.py#L1019){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.ensemble import RandomForestRegressor
model = RandomForestRegressor(n_estimators=10, criterion=’mse’, max_depth=None, min_samples_split=2, min_samples_leaf=1, min_weight_fraction_leaf=0.0, max_features=’auto’, max_leaf_nodes=None, min_impurity_decrease=0.0, min_impurity_split=None, bootstrap=True, oob_score=False, n_jobs=1, random_state=None, verbose=0, warm_start=False)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">n_estimators</span>,
                       <span class="coding">criterion</span>,
                       <span class="coding">max_features</span>,
                       <span class="coding">max_depth</span>,
                       <span class="coding">min_samples_split</span>,
                       <span class="coding">min_samples_leaf</span>,
                       <span class="coding">min_weight_fraction_leaf</span>,
                       <span class="coding">max_leaf_nodes</span>,
                       <span class="coding">min_impurity_split</span>,
                       <span class="coding">min_impurity_decrease</span>,
                       <span class="coding">bootstrap</span>,
                       <span class="coding">oob_score</span>,
                       <span class="coding">n_jobs</span>,
                       <span class="coding">random_state</span>,
                       <span class="coding">verbose</span>,
                       <span class="coding">warm_start</span>
</li>
<li><b>Attributes</b>: <span class="coding">estimators_</span>,
                       <span class="coding">feature_importances_</span>,
                       <span class="coding">n_features_</span>,
                       <span class="coding">n_outputs_</span>,
                       <span class="coding">oob_score_</span>,
                       <span class="coding">oob_prediction_</span>
</li>
</ul>

---

### RANSACRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.RANSACRegressor.html#sklearn.linear_model.RANSACRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/linear_model/ransac.py#L54){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.linear_model import RANSACRegressor
model = RANSACRegressor(base_estimator=None, min_samples=None, residual_threshold=None, is_data_valid=None, is_model_valid=None, max_trials=100, max_skips=inf, stop_n_inliers=inf, stop_score=inf, stop_probability=0.99, residual_metric=None, loss=’absolute_loss’, random_state=None)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">base_estimator</span>,
                       <span class="coding">min_samples</span>,
                       <span class="coding">residual_threshold</span>,
                       <span class="coding">is_data_valid</span>,
                       <span class="coding">is_model_valid</span>,
                       <span class="coding">max_trials</span>,
                       <span class="coding">max_skips</span>,
                       <span class="coding">stop_n_inliers</span>,
                       <span class="coding">stop_score</span>,
                       <span class="coding">stop_probability</span>,
                       <span class="coding">residual_metric</span>,
                       <span class="coding">loss</span>,
                       <span class="coding">random_state</span>
</li>
<li><b>Attributes</b>: <span class="coding">estimator_</span>,
                       <span class="coding">n_trials_</span>,
                       <span class="coding">inlier_mask_</span>,
                       <span class="coding">n_skips_no_inliers_</span>,
                       <span class="coding">n_skips_invalid_data_</span>,
                       <span class="coding">n_skips_invalid_model_</span>
</li>
</ul>

---

### SGDRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.SGDRegressor.html#sklearn.linear_model.SGDRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/linear_model/stochastic_gradient.py#L1165){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.linear_model import SGDRegressor
model = SGDRegressor(loss=’squared_loss’, penalty=’l2’, alpha=0.0001, l1_ratio=0.15, fit_intercept=True, max_iter=None, tol=None, shuffle=True, verbose=0, epsilon=0.1, random_state=None, learning_rate=’invscaling’, eta0=0.01, power_t=0.25, warm_start=False, average=False, n_iter=None)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">loss</span>,
                       <span class="coding">penalty</span>,
                       <span class="coding">alpha</span>,
                       <span class="coding">l1_ratio</span>,
                       <span class="coding">fit_intercept</span>,
                       <span class="coding">max_iter</span>,
                       <span class="coding">tol</span>,
                       <span class="coding">shuffle</span>,
                       <span class="coding">verbose</span>,
                       <span class="coding">epsilon</span>,
                       <span class="coding">random_state</span>,
                       <span class="coding">learning_rate</span>,
                       <span class="coding">eta0</span>,
                       <span class="coding">power_t</span>,
                       <span class="coding">warm_start</span>,
                       <span class="coding">average</span>,
                       <span class="coding">n_iter</span>
</li>
<li><b>Attributes</b>: <span class="coding">coef_</span>,
                       <span class="coding">intercept_</span>,
                       <span class="coding">average_coef_</span>,
                       <span class="coding">average_intercept_</span>,
                       <span class="coding">n_iter_</span>
</li>
</ul>

---

### TheilSenRegressor

[official page](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.TheilSenRegressor.html#sklearn.linear_model.TheilSenRegressor){:target="_blank"} \| [source](https://github.com/scikit-learn/scikit-learn/blob/ed5e127b/sklearn/linear_model/theil_sen.py#L198){:target="_blank"}


<div class="code-head">usage<span>code</span></div>

```python
from sklearn.linear_model import TheilSenRegressor
model = TheilSenRegressor(fit_intercept=True, copy_X=True, max_subpopulation=10000.0, n_subsamples=None, max_iter=300, tol=0.001, random_state=None, n_jobs=1, verbose=False)
```
{: .code-class}

<ul class="code-class-ul">
<li><b>Parameters</b>: <span class="coding">fit_intercept</span>,
                       <span class="coding">copy_X</span>,
                       <span class="coding">max_subpopulation</span>,
                       <span class="coding">n_subsamples</span>,
                       <span class="coding">max_iter</span>,
                       <span class="coding">tol</span>,
                       <span class="coding">random_state</span>,
                       <span class="coding">n_jobs</span>,
                       <span class="coding">verbose</span>
</li>
<li><b>Attributes</b>: <span class="coding">coef_</span>,
                       <span class="coding">intercept_</span>,
                       <span class="coding">breakdown_</span>,
                       <span class="coding">n_iter_</span>,
                       <span class="coding">n_subpopulation_</span>
</li>
</ul>

<script type="text/javascript" src="/js/selectbox.js"></script>