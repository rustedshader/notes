# PYPY

A fast, compliant alternative implementation of Python
It is a python compiler written in python which is faster than CPython

On average, PyPy is 4.4 times faster than CPython 3.7.
They currently support python 3.10 and 2.7.
Advantages and distinct Features:

- Speed: thanks to its Just-in-Time compiler, Python programs often run faster on PyPy. (What is a JIT compiler?)

- Memory usage: memory-hungry Python programs (several hundreds of MBs or more) might end up taking less space than they do in CPython.

- Compatibility: PyPy is highly compatible with existing python code. It supports cffi, cppyy, and can run popular python libraries like twisted, and django. It can also run NumPy, Scikit-learn and more via a c-extension compatibility layer.

- Stackless: PyPy comes by default with support for stackless mode, providing micro-threads for massive concurrency.

Specifically it is written in RPython which is restircted python

Mainly used for running pure python code which tends to run faster on it than regular cpython compiler of the python

Uses JIT Compiler (Just in time compiler)
