# Computing Resources

This page contains links to various resources that are relevant to programming. Some of the information is specific to my research but most of this information can be useful to anyone learning to program in Python or C++.

## Table of Contents

- [Computing Resources](#computing-resources)
  - [Table of Contents](#table-of-contents)
  - [Working Remotely](#working-remotely)
    - [Secure Shell (SSH)](#secure-shell-ssh)
    - [Linux/Bash](#linuxbash)
  - [Python](#python)
    - [Useful Libraries](#useful-libraries)
      - [General](#general)
      - [Research-Specific](#research-specific)
      - [Personal Projects](#personal-projects)
    - [Plotting with `matplotlib`](#plotting-with-matplotlib)
    - [Numba](#numba)
  - [Jupyter Notebooks & Lab](#jupyter-notebooks--lab)
    - [Useful commands](#useful-commands)
  - [High Throughput Computing (HTC)](#high-throughput-computing-htc)
    - [CRAB](#crab)
    - [Condor](#condor)
  - [ROOT](#root)
    - [Running C macros using ROOT](#running-c-macros-using-root)

## Working Remotely

### Secure Shell (SSH)

Secure Shell (SSH) is a network protocol that provides secure command-line access to remote machines. CERN provides a CERN UNIX cluster LXPLUS which can be accessed from the command line using the following

`ssh <username>@lxplus.cern.ch`

Kerberos credentials can be entered using the `kinit` command, which will allow you to remote into LXPLUS without having to enter your password each time.

### Linux/Bash

- List of Useful Commands

Command   | Action                                          | Example
----------|-------------------------------------------------|-----------------------------
`ls`      | Show directory contents                         | `ls -l`
`cd`      | Change directory                                | `cd ~`
`mkdir`   | Create a new folder/directory                   | `mkdir new_dir`
`touch`   | Create a new file                               | `touch new_file.txt`
`rm`      | Remove/delete a file                            | `rm new_file.txt`
`cat`     | Show contents of a file                         | `cat new_file.txt`
`pwd`     | Show full path to current directory             | `pwd`
`cp`      | Copy file/folder                                | `cp /path/to/old_file.txt path/to/new_file.txt`
`mv`      | Move file/folder                                | `mv /path/to/old_file.txt /new/path/to/old_file.txt`
`grep`    | Search for a specific phrase in file/lines      | `grep 'line' info.txt`
`find`    | Search files and directories                    | `find [starting directory] [options] [search term]`
`vi`      | Open VIM text editor                            | `vi file_to_edit.py`
`history` | Show last 50 used commands                      | `history [number of recent commands to show]`
`clear`   | Clear the terminal screen                       | `clear`
`tar`     | Create and unpack compressed archives           | `tar cvzf ArchiveName.tar.gz /path/to/dir` or `tar xvzf FileName.tar.gz`
`wget`    | Downlaod files from the internet                | `wget http://fileurl/filename.ext`
`du`      | Get file size                                   | `du [directory path] --max-depth=1`
`>`       | Redirect standard output away from command line | `ls > list_of_dirs_and_files.txt`


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
- [Numba](http://numba.pydata.org) - A high-performance, open source Python JIT compiler that translates a subset of Python and NumPy code into optimized machine code at runtime. See notes below.

#### Research-Specific

- [Uproot](https://github.com/scikit-hep/uproot4) - A reader and writer of the ROOT file format using NumPy and Awkward Array (AA is optional but highly recommended).
- [Awkward Array](https://pypi.org/project/awkward/) - A library for nested, variable-sized data, including arbitrary-length lists, records, mixed types, and missing data, using NumPy-like idioms.
- [PyROOT](https://pypi.org/project/awkward/) - PyROOT is a collection of ROOT's Python-C++ bindings, which allow the use of ROOT from Python. (*I prefer Uproot to PyROOT but felt it necessary to include this library, since it is widely used in HEP.*)

#### Personal Projects

- [TKinter](https://docs.python.org/3/library/tkinter.html) - The standard Python interface to the Tk GUI toolkit.

### Plotting with `matplotlib`

- [LateX in matplotlib](https://matplotlib.org/stable/tutorials/text/mathtext.html) - Writing mathematical expressions in `matplotlib`.

### Numba

[Numba](http://numba.pydata.org) is a high-performance, open source Python JIT compiler that translates a subset of Python and NumPy code into optimized machine code at runtime using the industry-standard [LLVM](https://llvm.org/) compiler library.

I implemented Numba into one of the modules I built to handle the construction and manipulation of training and testing sets during the development of neural network algorithms developed to aid my analysis. Numba is quite finicky, but seemingly well worth it. I was compelled to try it out when one of my functions was taking an exasperatingly long time to run. I successfully integrated Numba `@jit` decorators into my module after pruning all of the f-strings, replacing the Awkward Array `with array_builder.list()` calls with `array_builder.begin_list()` and `array_builder.end_list()`, and removing the need to unpack variables from a function I was calling (e.g., `var1, *the_rest = some_func()`) by having the function return a list (e.g., `return var1, [var2, var3, var4...]`). Numba would not compile my code until I replaced or removed these features (I'm sure there are ways to work around these requirements but since this was my first escapade into the realm of Numba, I took the "easy" route).

Some important notes about Numba:

- If your code fails while using `@jit` to speed it up, Numba is unable to indicate where the failure occurred. This appears to be a consequence of the process used to speed up the code. Commenting out the `@jit` will allow you to more precisely identify where the error occurred in your code.
- As mentioned above, Numba is finicky about what it can handle in your function. It is optimized for Python code and NumPy. If your code only consists of this type of code, one can use the decorator `@jit(nopython=True)`. However, if your code contains any other data types such as Panda DataFrames, etc., Numba will throw errors unless you remove the `nopython=True` argument from the decorator.

## Jupyter Notebooks & Lab

### Useful commands

- [autoreload](https://ipython.readthedocs.io/en/stable/config/extensions/autoreload.html) - IPython extension to reload modules before executing user code. `autoreload` reloads modules automatically before entering the execution of code typed at the IPython prompt.


## High Throughput Computing (HTC)

### CRAB

CRAB is a utility to submit CMSSW jobs to distributed computing resources.

### Condor

Condor is a software system that creates a high throughput computing environment. The user prepares a submit description file (extension either `.jdl` or `.sub`) containing the commands and keywords and uses the command `condor_submit file.jdl` to submit the job to HTCondor. An example of a submit description file may contain

~~~~
universe                = vanilla
executable              = welcome.sh
arguments               = $(ClusterId)$(ProcId)
output                  = output/welcome.$(ClusterId).$(ProcId).out
error                   = error/welcome.$(ClusterId).$(ProcId).err
log                     = log/welcome.$(ClusterId).log

initial_dir             = path/to/dir
should_transfer_files   = YES
when_to_transfer_output = ON_EXIT_OR_EVICT
+SpoolOnEvict           = False
transfer_input_files    = <input_file1>, <input_file2>
transfer_output_files   = <output_file>
stream_output           = True
request_memory          = 1 GB
getenv                  = True
queue
~~~~

Some of the above commands are probably not mandatory, but this is what it looked like when I first got my submission to work properly. The executable may look like this

~~~~
#!/bin/bash

echo "welcome to HTCondor tutorial"
~~~~

I found it very important to include the `#!/bin/bash` to make sure the executable can be run by Condor. The user can query using the command `condor_q`, which will show output like

~~~~
-- Schedd: submit.chtc.wisc.edu : <127.0.0.1:9618?... @ 12/31/69 23:00:00
OWNER    BATCH_NAME    SUBMITTED   DONE   RUN    IDLE   HOLD  TOTAL JOB_IDS
nemo     batch23       4/22 20:44      _      _      _      1      _ 3671850.0
nemo     batch24       4/22 20:56      _      _      _      1      _ 3673477.0
nemo     batch25       4/22 20:57      _      _      _      1      _ 3673728.0
nemo     batch26       4/23 10:44      _      _      _      1      _ 3750339.0
nemo     batch27       7/2  15:11      _      _      _      _      _ 7594591.0
nemo     batch28       7/10 03:22   4428      3      _      _   4434 7801943.0 ... 7858552.0
nemo     batch29       7/14 14:18   5074   1182     30     19  80064 7859129.0 ... 7885217.0
nemo     batch30       7/14 14:18   5172   1088     28     30  58310 7859106.0 ... 7885192.0

2388 jobs; 0 completed, 1 removed, 58 idle, 2276 running, 53 held, 0 suspended
~~~~



## ROOT

### Running C macros using ROOT

- One may run macros in C/C++ using root by calling `root -l -q my_script.c`, where the options `-l` and `-q` cause the splash screen to be suppressed and for root to quit after running the macro, successively. To pass arguments to the script using root, use the command `root -l -q 'my_script.c+("string_option",int_option,more_options)'`