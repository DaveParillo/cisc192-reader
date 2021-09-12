Math Functions
--------------

In mathematics, you have probably seen functions like :math:`\sin` and
:math:`\log`, and you have learned to evaluate expressions like
:math:`\sin(\pi/2)` and :math:`\log(1/x)`. First, you evaluate the
expression in parentheses, which is called the argument of the
function. For example, :math:`\pi/2` is approximately 1.571, and
:math:`1/x` is 0.1 (if :math:`x` happens to be 10).

Then you can evaluate the function itself, either by looking it up in a
table or by performing various computations. The :math:`\sin` of 1.571
is 1, and the :math:`\log` of 0.1 is -1 (assuming that :math:`\log`
indicates the logarithm base 10).

This process can be applied repeatedly to evaluate more complicated
expressions like :math:`\log(1/\sin(\pi/2))`. First we evaluate the
argument of the innermost function, then evaluate the function, and so
on.

C++ provides a set of built-in functions that includes most of the
mathematical operations you can think of. The math functions are invoked
using a syntax that is similar to mathematical notation:


.. activecode:: math_functions_AC_1
   :language: cpp
   :caption: Using the cmath Library

   This program performs calculations using some of the built-in functions 
   from the cmath library.
   ~~~~
   #include <cmath>
   #include <iostream>
   using namespace std;

   int main () {
       double result = log (17.0);
       double angle = 1.5;
       double height = sin (angle);
       cout << result << endl;
       cout << angle << endl;
       cout << height << endl;
       return 0;
   }


The first example sets log to the logarithm of 17, base :math:`e`. There
is also a function called ``log10`` that takes logarithms base 10.

The second example finds the sine of the value of the variable angle.
C++ assumes that the values you use with ``sin`` and the other trigonometric
functions (``cos``, ``tan``) are in *radians*. 

.. note::
   To convert from degrees to radians, you can divide by 360 and multiply
   by 2 * pi.

If you don’t happen to know :math:`\pi` to 15 digits, you can calculate
it using the ``acos`` function. The arccosine (or inverse cosine) of -1 is
:math:`\pi`, because the cosine of :math:`\pi` is -1.


.. activecode:: math_functions_AC_2
   :language: cpp
   :caption: Working with Angles

   This program also uses built-in functions from the cmath library,
   specifically the functions that deal with angles.  As you can see,
   we have a line of code that converts the default radians value to
   degrees.
   ~~~~
   #include <cmath>
   #include <iostream>
   using namespace std;

   int main () {
       double pi = acos(-1.0);
       double degrees = 90;
       double angle = degrees * 2 * pi / 360.0;
       cout << pi << endl;
       cout << degrees << endl;
       cout << angle << endl;
       return 0;
   }

.. index::
   single: header file

.. index::
   single: include
   single: include statement

Before you can use any of the math functions, you have to include the
math header file. **Header files** contain information the compiler
needs about functions that are defined in other source files. For
example, in the “Hello, world!” program we included a header file named
iostream using an **include** statement:

::

    #include <iostream>
    using namespace std;

iostream contains information about input and output (I/O) streams,
including the object named ``cout``. 
C++ has a powerful feature called namespaces,
that are used to avoid naming conflicts between function or
types that might otherwise have the same name, like ``cout``.
Technically ``cout`` is declared in the namespace ``std``,
making its fully qualified name ``std::cout``.
We can pull all of the names from the standard name space into the
global namespace with the statement:

::

    using namespace std;

All of the facilities defined in the C++ *Standard Library*
are defined in the namespace ``std``.
More on namespaces in a few sections.

Similarly, the math header file contains information about the math
functions. You can include it at the beginning of your program along
with iostream:

::

    #include <cmath>

Such header files have an initial ‘c’ to signify that these header files
have been derived from the **C** language.


.. tabbed:: tab_check

   .. tab:: Q1

      .. dragndrop:: dnd1
          :feedback: This is feedback.
          :match_1: cmath|||allows the use of functions like log and sin
          :match_2: iostream|||contains information about input and output streams
          :match_3: namespace std|||the standard implementation of cout

          Match the statement to its description.


   .. tab:: Q2

      .. fillintheblank:: math_functions_2

         What are the units used by sinusoidal functions (sin, asin, e.t.c.) in C++?
          
         - :[Rr][Aa][Dd][Ii][Aa][Nn][Ss]?: If you need to convert to degrees, just multiply by 360 and divide by 2pi.
           :[Dd][Ee][Gg][Rr][Ee][Ee][Ss]?: This is a unit sometimes used for sinusoidal functions, but not the one used by C++.
           :.*: Try again!


   .. tab:: Q3

      .. mchoice:: math_functions_3

          **Multiple Response** Select all correct cmath functions.

          -   ``cos``

              +   This function computes the cosine of an angle.

          -   ``arctan``

              -   The arc tangent function is actually called ``atan``.

          -   ``log10``

              +   This function computes the common logarithm.

          -   ``pow``

              +   This function raises an expression to a power.

          -   ``ln``

              -   The natural log function is actually called ``log``.
