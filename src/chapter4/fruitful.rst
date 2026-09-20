Fruitful functions
------------------

Some of the built-in functions we have used, like the math functions,
produce results. That is, the effect of calling the function is to
generate a new value, which we usually assign to a variable or use as
part of an expression. For example:

::

    double e = exp (1.0);
    double height = radius * sin (angle);

But so far all the functions we have written have been ``void``
functions; that is, functions that return no value. When you call a ``void``
function, it is typically on a line by itself, with no assignment:

::

    repeat_lines (3);
    countdown (n-1);

If you think about it, a function that takes no parameters and returns
nothing is pretty limited.
By definition, it can only do exactly one thing -- whatever the statements
in the function specify.
Void functions are difficult to test, reuse, and compose with other functions.

In addition, all the functions we have created so far were fairly
limited at least as far as lacking any ability to check certain
conditions and change the behavior of the program accordingly.

..	index::
	  pair: functions; fruitful functions

In this chapter, we are going to write functions that resolve both
of these shortcomings, which I will refer to as **fruitful** functions,
for want of a better name. 


