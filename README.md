pyflann
=============

### 1. Introduction

pyflann is the python bindings for [FLANN - Fast Library for Approximate Nearest Neighbors](https://github.com/mariusmuja/flann).

### 2. Install

#### For python2

This package uses distutils, which is the default way of installing python modules. To install in your home directory, securely run the following:
```
git clone https://github.com/xiachufang/pyflann.git
cd pyflann
[sudo] python setup.py install
```

Or directly through `pip` to install it:
```
[sudo] pip install xiachufang-pyflann
```

### 3. Usage

Use it just like the following code:
```python
from pyflann import *
import numpy as np

dataset = np.array(
    [[1., 1, 1, 2, 3],
     [10, 10, 10, 3, 2],
     [100, 100, 2, 30, 1]
     ])
testset = np.array(
    [[1., 1, 1, 1, 1],
     [90, 90, 10, 10, 1]
     ])
flann = FLANN()
result, dists = flann.nn(
    dataset, testset, 2, algorithm="kmeans", branching=32, iterations=7, checks=16)
print result
print dists

dataset = np.random.rand(10000, 128)
testset = np.random.rand(1000, 128)
flann = FLANN()
result, dists = flann.nn(
    dataset, testset, 5, algorithm="kmeans", branching=32, iterations=7, checks=16)
print result
print dists
```
### 4. How to update
1. Download flann source from https://github.com/mariusmuja/flann
2. Compile according the [manual](http://www.cs.ubc.ca/research/flann/uploads/FLANN/flann_manual-1.8.4.pdf)
```
$ mkdir build
$ cd build
$ cmake ..
$ make
```
3. Copy relevant files from https://github.com/mariusmuja/flann/tree/master/src/python/pyflann
4. Copy the dynamic link library from `build/lib/libflann.so`
