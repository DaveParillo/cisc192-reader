Containers for strings
----------------------

We have seen five types of values—booleans, characters, integers,
floating-point numbers and strings—but only four types of
variables—``bool``, ``char``, ``int`` and ``double``. So far we have no
way to store a string in a variable or perform operations on strings.

In fact, there are several kinds of variables in C++ that can store
strings. One is a basic type that is part of the C++ language, sometimes
called "a native C string." The syntax for C strings is a bit ugly, and
using them requires some concepts we have not covered yet, 
so we will avoid them when we can.

The string type we are going to use is called ``string``, which is one
of the classes that belong to the C++ Standard Library.

Unfortunately, it is not possible to avoid C strings altogether. In a
few places in this chapter I will warn you about some problems you might
run into using ``string``\ s instead of C strings.
