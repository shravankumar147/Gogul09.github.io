---
layout: post
category: software
class: Machine Learning
title: Data loaders and file formats in Machine Learning
description: Learn how to load data to solve a machine learning problem using Python, Numpy and Pandas.
author: Gogul Ilango
permalink: /software/data-loaders-and-file-formats-in-ml
image: https://drive.google.com/uc?id=1OdUIXkvVj1jbUkTvDAnkcHOZZSqPiWj8
---

<div class="sidebar_tracker" id="sidebar_tracker">
  <button onclick="closeSidebar('sidebar_tracker_content')">X</button>
  <p onclick="showSidebar('sidebar_tracker_content')">Contents</p>
  <ul id="sidebar_tracker_content">
		<li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_1" href="#csv-files">CSV files</a></li>
		<li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_2" href="#load-csv-using-python">Load CSV using Python</a></li>
		<li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_3" href="#load-csv-using-numpy">Load CSV using Numpy</a></li>
		<li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_4" href="#load-csv-using-pandas">Load CSV using Pandas</a></li>
		<li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_5" href="#hdf5-files">HDF5 files</a></li>
		<li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_6" href="#save-using-h5py">Save HDF5 using h5py</a></li>
		<li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_7" href="#load-using-h5py">Load HDF5 using h5py</a></li>
		<li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_8" href="#save-group-using-h5py">Save group using h5py</a></li>
		<li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_9" href="#load-group-using-h5py">Load group using h5py</a></li>
	</ul>
</div>

<p class="hundred-days"><span>#100DaysOfMLCode</span></p>

**First step in any machine learning problem is to load data. In this blog post, we will learn what are the different data loaders and file formats available in Python to do machine learning.**

Common file formats used to store data in machine learning as well as deep learning are <span class="coding">.csv</span>, <span class="coding">.h5</span> and <span class="coding">.pickle</span>. Apart from these, there are some other ways to handle large data files as discussed [here](https://machinelearningmastery.com/large-data-files-machine-learning/){:target="_blank"}.

<h3 id="csv-files">CSV files</h3>

CSV is the most common file format in machine learning. **CSV** means **C**omma **S**eparated **V**alues. Each row in the file represents an instance and each column represents an attribute or feature. 

When working with CSV files, you need to consider the following factors.
* Does your csv file have **headers** which represent column names?
* Does your csv file have **comments** specified using any symbol?
* Does your csv file have **delimiter** apart from the standard **,** delimiter?
* Does your csv file have **quotes** to represent string values separated by space?

For this tutorial, we will consider the famous [Iris dataset](https://en.wikipedia.org/wiki/Iris_flower_data_set){:target="_blank"}. You can download the <span class="coding">iris.data</span> csv file [here](https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data){:target="_blank"}. Go to that page, hit <span class="coding">ctrl+a</span>, <span class="coding">ctrl+c</span>, <span class="coding">ctrl+v</span> and save it as **iris_dataset.csv**. Below is the first 10 rows of Iris dataset which is represented in <span class="coding">.csv</span> format. 

<div class="code-head">iris_dataset.csv<span>csv</span></div>

```
5.1,3.5,1.4,0.2,Iris-setosa
4.9,3.0,1.4,0.2,Iris-setosa
4.7,3.2,1.3,0.2,Iris-setosa
4.6,3.1,1.5,0.2,Iris-setosa
5.0,3.6,1.4,0.2,Iris-setosa
5.4,3.9,1.7,0.4,Iris-setosa
4.6,3.4,1.4,0.3,Iris-setosa
5.0,3.4,1.5,0.2,Iris-setosa
4.4,2.9,1.4,0.2,Iris-setosa
4.9,3.1,1.5,0.1,Iris-setosa
```

<h3 id="load-csv-using-python">Load CSV using Python</h3>

<span class="coding">csv</span> module in Python provides a method called <span class="coding">reader()</span> to read <span class="coding">.csv</span> files. You can specify the delimiter used in your csv file as well as quoting constraints as shown below. You can also convert the data read by csv reader into a numpy array and then use it to do machine learning. The below example prints the shape of the iris dataset using python's csv reader and numpy.

<div class="code-head">load_using_python.py<span>code</span></div>

```python
import csv
import numpy as np

# load iris dataset using csv package
file_path = "iris_dataset.csv"
f = open(file_path, "r")
data = csv.reader(f, delimiter=",", quoting=csv.QUOTE_NONE)
d = list(data)

# use numpy to print the shape
data = np.array(d)
print(data.shape) # prints (150, 5)
```

<h3 id="load-csv-using-numpy">Load CSV using Numpy</h3>

[Numpy](http://www.numpy.org/){:target="_blank"} offers two handy functions to load csv files. <span class="coding">numpy.loadtxt()</span> works only if the data present in csv file is of same datatype. <span class="coding">numpy.genfromtxt()</span> works for multiple datatype in a single csv file using the argument <span class="coding">dtype=None</span>.
* [numpy.loadtxt()](https://docs.scipy.org/doc/numpy/reference/generated/numpy.loadtxt.html){:target="_blank"}
* [numpy.genfromtxt()](https://docs.scipy.org/doc/numpy/reference/generated/numpy.genfromtxt.html){:target="_blank"}

<div class="code-head">load_using_numpy.py<span>code</span></div>

```python
import numpy as np

# load iris dataset using numpy
file_path = "iris_dataset.csv"
f = open(file_path, "r")
data = np.genfromtxt(f, delimiter=",", dtype=None)
print(data) # prints the iris dataset
```

<h3 id="load-csv-using-pandas">Load CSV using Pandas</h3>

[Pandas](https://pandas.pydata.org/){:target="_blank"} offers comprehensive and easier ways to load csv files. <span class="coding">pandas.read_csv()</span> method loads the csv data as a pandas dataframe which could directly be used for visualization and machine learning. In the below example, I have specified header names for each column in the csv file and assigned it using <span class="coding">names</span> argument in <span class="coding">pd.read_csv()</span> function.

* [pandas.read_csv()](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html){:target="_blank"}

<div class="code-head">load_using_pandas.py<span>code</span></div>

```python
import pandas as pd

# load iris dataset using pandas
file_path = "iris_dataset.csv"
header_names = ["sepal_length", "sepal_width", "petal_length", "petal_width", "class"]
data = pd.read_csv(file_path, names=header_names)
print(data.shape) # prints (150, 5)
print(type(data)) # prints <class 'pandas.core.frame.DataFrame'>
```

<h4 id="advantages-of-csv">Advantages of CSV</h4>
* Human-readable format.
* Easy to edit manually.
* Easy to implement and parse.
* Faster to handle for smaller dataset.

<h4 id="disadvantages-of-csv">Disadvantages of CSV</h4>
* Takes huge time to load large data.
* Takes huge time to save large data.
* No standard way to represent binary data and control characters.
* No distinction between numeric and text values.
* No way to represent complex hierarchical data.

<h3 id="hdf5-files">HDF5 files</h3>
An alternative to CSV file format is the [HDF5](){:target="_blank"} file format which is now widely used in Deep Learning. HDF5 is a hierarchical data format to store and manage large chunks of data. It is similar to a filesystem data format which can store complex hierarchical data. Please read [this](https://support.hdfgroup.org/HDF5/Tutor/HDF5Intro.pdf){:target="_blank"} introduction about HDF5 file format and then start using it.

HDF5 includes two major object types.
1. **Groups** - Container like structures to hold datasets and other groups.
2. **Datasets** - Multi-dimensional arrays of a homogeneous type (You could think of a standard numpy array). 

<h3 id="save-using-h5py">Save HDF5 using h5py</h3>
You can save any number of numpy arrays in <span class="coding">.h5</span> file format and load it again using a python library called <span class="coding">h5py</span>. If you have installed Python via Anaconda, then you should get it by default. Otherwise install it using <span class="coding">pip</span> [(installing h5py)](http://docs.h5py.org/en/latest/build.html){:target="_blank"}.

The following example creates two random numpy arrays and saves a <span class="coding">demo_data.h5</span> file locally. Notice that we pass the numpy array as a <span class="coding">data</span> argument to the <span class="coding">create_dataset()</span> function. You can create as many dataset as you want with unique name to each dataset.

If you execute the below code, you would get a <span class="coding">demo_data.h5</span> file which is of size 9.6MB in your localdisk.

<div class="code-head">save_h5.py<span>code</span></div>

```python
import numpy as np
import h5py

# create two random numpy arrays
a1 = np.random.random(size = (500, 500))
a2 = np.random.random(size = (1000, 1000))

# save it as a HDF5 file
with h5py.File("demo_data.h5", "w") as f:
	f.create_dataset("dataset1", data=a1)
	f.create_dataset("dataset2", data=a2)
```

<h3 id="load-using-h5py">Load HDF5 using h5py</h3>
You can access the list of keys in the <span class="coding">.h5</span> file using <span class="coding">keys()</span> function directly on the file. This returns the list of keys you have created. 

You can access the stored dataset using <span class="coding">get()</span> function with the dataset's name passed as the argument. After loading the dataset, you can easily use <span class="coding">np.array()</span> function to convert it back to a numpy array.

The following example displays the keys, loads the <span class="coding">demo_data.h5</span> file, loads <span class="coding">dataset1</span>, convert it back to numpy array and prints out its shape.

<div class="code-head">load_h5.py<span>code</span></div>

```python
import numpy as np
import h5py

# load the saved .h5 file
with h5py.File("demo_data.h5", "r") as f:
	
	# display the list of keys in this file
	keys = list(f.keys())
	print("{0} keys in this file: {1}".format(len(keys), keys))
	# prints 2 keys in this file: ['dataset1', 'dataset2']
	
	# load the numpy array
	data = f.get("dataset1")
	a1   = np.array(data)
	print("Shape of dataset1: {0}".format(a1.shape)) 
	# prints Shape of dataset1: (500, 500)
```

<h3 id="save-group-using-h5py">Save group using h5py</h3>
Similar to dataset which holds multi-dimensional numpy arrays, you can create groups to hold datasets and other groups. To do that, you need to use <span class="coding">create_group()</span> function and pass in an unique group name.

The following example creates two random numpy arrays, creates two groups with its corresponding dataset. Running this example generates <span class="coding">demo_group.h5</span> file locally that is of size 3.9MB.

<div class="code-head">save_group_h5.py<span>code</span></div>

```python
import numpy as np
import h5py

# create two random numpy arrays
a1 = np.random.random(size= (500, 500))
a2 = np.random.random(size= (500, 500))

# create groups and datasets
with h5py.File("demo_group.h5", "w") as f:
	group1 = f.create_group("group1")
	group1.create_dataset("dataset1", data=a1)

	group2 = f.create_group("group2")
	group2.create_dataset("dataset2", data=a2)
```

<h3 id="load-group-using-h5py">Load group using h5py</h3>
To load group from a <span class="coding">.h5</span> file, you need to use the same <span class="coding">get()</span> function with the group's name as the argument. As <span class="coding">keys()</span> gave datasets in the file, <span class="coding">items()</span> will provide the list of groups in the file.

The following example loads the <span class="coding">demo_group.h5</span> file, loads the list of groups in the file using <span class="coding">items()</span> function and prints out the contents of <span class="coding">group1</span>.

<div class="code-head">load_group_h5.py<span>code</span></div>

```python
import numpy as np
import h5py

# read groups and datasets
with h5py.File("demo_group.h5", "r") as f:

	# get the list of items in the file
	groups = list(f.items())
	print("{0} items in this file - {1}".format(len(groups), groups))

	# load group1 and print the items
	group1 = f.get("group1")
	group1_items = list(group1.items())
	print("{0} item in group1 - {1}".format(len(group1_items), group1_items))

	# load dataset1 from group1 and print its shape
	data1 = group1.get("dataset1")
	a1    = np.array(data1)
	print("Shape of dataset1 in group1: {0}".format(a1.shape))
```

<div class="code-head">output<span>terminal</span></div>

```
2 items in this file - [('group1', <HDF5 group "/group1" (1 members)>), ('group2', <HDF5 group "/group2" (1 members)>)]
1 item in group1 - [('dataset1', <HDF5 dataset "dataset1": shape (500, 500), type "<f8">)]
Shape of dataset1 in group1: (500, 500)
```