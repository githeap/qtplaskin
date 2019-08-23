[![GitHub version](https://img.shields.io/github/v/release/erwanp/qtplaskin/all.svg)](https://img.shields.io/github/v/release/erwanp/qtplaskin/all.svg)
[![Tests](https://img.shields.io/travis/erwanp/qtplaskin.svg)](https://travis-ci.org/erwanp/qtplaskin)
[![Code coverage](https://codecov.io/gh/erwanp/qtplaskin/branch/master/graph/badge.svg)](https://codecov.io/gh/erwanp/qtplaskin)

# QtPlaskin

QtPlaskin is a graphical interface to analyze results from a plasma 
kinetic code such as ZdPlasKin (1).  It supports both a specific data
format based on HDF5 and importing directories with certain filesets
that can be written from a running FORTRAN code.

- QtPlaskin was created by A. Luque (see [original version](https://github.com/aluque))
- It was updated by E. Pannier (see end of this file for main changes)

# Install

QtPlaskin runs in Linux, Mac OS X and Windows. QtPlaskin is now a Python library. 
Install it from GitHub with:

```
git clone https://github.com/erwanp/qtplaskin.git
cd qtplaskin
pip install -e .
``` 

`-e` is for the editable version. Keep it up to date with `git pull` in the 
`qtplaskin` directory

If the install procedure does not work, please refer to the former installation procedure. 
See the file INSTALL.txt for information on the libraries that must be
installed in your system and how to obtain them.

# Use

## GUI 

Installing the library creates a script that you can use from the command line to 
start the QtPlaskin GUI. Just select the folder where ZdPlaskin created the `qt_*.txt` 
files (for instance `Results/TestCase/` in the example below):

```
qtplaskin Results/TestCase/
```

Remember that you need to tell your ZdPlaskin user code to generate the `qt_*.txt` files:
see the `Generate Qt Files` section below 


## Python

Without starting the QtPlaskin GUI interface, you can still use the functions 
defined in QtPlaskin to load the data generated by ZdPlaskin:

```python
from qtplaskin import FastDirData
d = FastDirData([results folder])
# access d attributes:
d.plot('CO')  # to plot 
d.get('...')  # to retrieve data
``` 


# Generate Qt Files

With the latest version of ZDPlaskin you can use 
```
  call ZDPlaskin_set_config(QTPLASKIN_SAVE=.true.)
```
Then you can import the data of your simulation into QtPlaskin by using
File -> Import from directory... in the program menu.


---
(1)  ZdPlaskin is a computer code developed by S. Pancheshnyi, B. Eismann, 
     G.J.M. Hagelaar and L.C. Pitchford, 
     http://www.zdplaskin.laplace.univ-tlse.fr (University of Toulouse, 
     LAPLACE, CNRS-UPS-INP, Toulouse, France, 2008).


---

# Features specific to this Fork: 

Improvements over A. Luque's initial version:

- Dynamic tooltips on plots to analyze graphs with dozens of different lines

- Synchronized timescales over all plots, and dynamic ticks to deal with 
nanosecond to microsecond ranges

- ported to PyQt5 to keep up with the latest Python environnements

- Python3 compatible

- Made qtplaskin an installable Python library

- call qtplaskin from the command line with with `qtplaskin $FOLDER` to analyze a given directory

- faster Results folder loading using Pandas instead of Numpy







