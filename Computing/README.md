# Computing Resources

This page contains links to various resources that are relevant to programming.

## Table of Contents

- [Computing Resources](#computing-resources)
  - [Table of Contents](#table-of-contents)
  - [Python](#python)
    - [Plotting with `matplotlib`](#plotting-with-matplotlib)
  - [ROOT](#root)
    - [Running C macros using ROOT](#running-c-macros-using-root)

## Python

### Plotting with `matplotlib`

- [LateX in matplotlib](https://matplotlib.org/stable/tutorials/text/mathtext.html) - Writing mathematical expressions in `matplotlib`.


## ROOT

### Running C macros using ROOT

- One may run macros in C/C++ using root by calling `root -l -q my_script.c`, where the options `-l` and `-q` cause the splash screen to be suppressed and for root to quit after running the macro, successively. To pass arguments to the script using root, use the command `root -l -q 'my_script.c+("string_option",int_option,more_options)'`