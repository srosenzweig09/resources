# Computing Resources

This page contains links to various resources that are relevant to programming. Some of the information is specific to my research but most of this information can be useful to anyone learning to program in Python or C++.

## Table of Contents

- [Computing Resources](#computing-resources)
  - [Table of Contents](#table-of-contents)
  - [Python](#python)
    - [Useful Libraries](#useful-libraries)
      - [General](#general)
      - [Research-Specific](#research-specific)
      - [Personal Projects](#personal-projects)
    - [Plotting with `matplotlib`](#plotting-with-matplotlib)
  - [ROOT](#root)
    - [Running C macros using ROOT](#running-c-macros-using-root)

## Python

### Useful Libraries

#### General

- [NumPy](https://numpy.org) - The fundamental package for scientific computing inPython, this library provides multidimensional array objects, as well as other useful objects. 
- [matplotlib](https://matplotlib.org) - Visualization with Python: A comprehensive library for creating static, animated, and interactive visualization with Python.
- [IceCream](https://github.com/gruns/icecream) - A library that makes print debugging a little sweeter.
- [Keras](https://keras.io) - An API designed for humans, this machine learning library follows best practices for reducing cognitive load, minimizing the number of user actions required for common use cases and providing clear and actionable error messages.
- [TensorFlow](https://www.tensorflow.org) - An end-to-end open source platform for machine learning, this library contains a comprehensive and flexible ecosystem of tools, libraries, and community resources that lets researchers push the state-of-the-art in machine learning.
- [SciPy](https://www.scipy.org) - An ecosystem of open-source software for mathematics, science, and engineering.
- [Pillow (PIL)](https://pillow.readthedocs.io/en/stable/) - This Python imaging library adds image processing capabilities to your Python interpreter.
- [Pandas](https://pandas.pydata.org/docs/reference/index.html) - A fast, powerful, flexible, and easy to use open source data analysis and manipulation tool.
- [PyQt](https://www.tutorialspoint.com/pyqt/index.htm) - One of the most popular Python bindings for the Qt cross-platform C++ framework. This library provides a GUI widgets toolkit.

#### Research-Specific

- [Uproot](https://github.com/scikit-hep/uproot4) - A reader and writer of the ROOT file format using NumPy and Awkward Array (AA is optional but highly recommended).
- [Awkward Array](https://pypi.org/project/awkward/) - A library for nested, variable-sized data, including arbitrary-length lists, records, mixed types, and missing data, using NumPy-like idioms.
- [PyROOT](https://pypi.org/project/awkward/) - PyROOT is a collection of ROOT's Python-C++ bindings, which allow the use of ROOT from Python. (*I prefer Uproot to PyROOT but felt it necessary to include this library, since it is widely used in HEP.*)

#### Personal Projects

- [TKinter]() -

### Plotting with `matplotlib`

- [LateX in matplotlib](https://matplotlib.org/stable/tutorials/text/mathtext.html) - Writing mathematical expressions in `matplotlib`.


## ROOT

### Running C macros using ROOT

- One may run macros in C/C++ using root by calling `root -l -q my_script.c`, where the options `-l` and `-q` cause the splash screen to be suppressed and for root to quit after running the macro, successively. To pass arguments to the script using root, use the command `root -l -q 'my_script.c+("string_option",int_option,more_options)'`