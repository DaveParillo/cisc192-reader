# CISC 192 C++ Course Reader
[![Docs](https://img.shields.io/github/actions/workflow/status/daveparillo/cisc192-reader/publish-docs.yml?branch=main&label=docs)](https://github.com/daveparillo/cisc192-reader/actions/workflows/publish-docs.yml)
[![License: CC BY-NC 4.0](https://img.shields.io/badge/license-CC%20BY--NC%204.0-blue.svg)](https://creativecommons.org/licenses/by-nc/4.0/)

This book is a modified version of 
*How to Think Like a Computer Scientist - C++ Edition*

The C++ version created by Barbara Ericson at the Unviersity of Michigan and
is based on [How to Think Like a Computer Scientist: C++](https://open.umn.edu/opentextbooks/textbooks/how-to-think-like-a-computer-scientist-c-version).


A textbook based on [sphinx-touchbook](https://github.com/DaveParillo/sphinx-touchbook).

This book tries to provide you with an interactive experience as you learn C++.
You can read the text, watch videos, answer questions, write and run code.

# Using this book
If you simply want to check it out, read it or whatever,
then you're done.
You can see and read this book [online](https://daveparillo.github.io/cisc192-reader).

# Building this book from source
We have tried to make it easy for you to build and use this book.  
You can build it and host it yourself in just a few simple steps.

## Install and make a Python virtualenv
 
* Documentation here:  https://virtualenv.pypa.io/en/stable/
* Video here:  https://www.youtube.com/watch?v=IX-v6yvGYFg
* For the impatient:

**Step 1: Create and load a virtual python environment**

```
$ python -m venv .venv
$ source .venv
```
     
**NOTE:**

You will need to do the last command **every time** you want to work on the
book in your virtual environment.

If you have not used Python virtual environments before I strongly recommend
reading the docs or watching the video
 
With the virtual environment installed and configured you can continue.

**Step 2: Install doc build dependencies and build HTML**
```
$ python -m pip install ".[docs]"
$ python -m sphinx -b html src build/html
```

Open your favorite web browser and open `build/html/index.html`.

Sphinx-touchbook supports all the HTML builders, plain text, and LaTeX
builders.
You can build PDF versions of the documentation if you have a LaTeX
engine installed.
