.. index::
   pair: log; math
   pair: sin; math

Math Functions
--------------

In mathematics, you have probably seen functions like :numeric:`sin <math/sin>` and
:numeric:`log <math/log>`, and you have learned to evaluate expressions like
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
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Using the cmath Library

   This program performs calculations using some of the built-in functions 
   from the cmath library.
   ~~~~
   #include <cmath>
   #include <iostream>

   int main () {
       constexpr double result = log (17.0);
       constexpr double radians = 1.5;
       constexpr double height = sin (radians);
       std::cout << result << '\t'
                 << radians  << '\t'
                 << height << '\n';
       return 0;
   }


The first example sets log to the logarithm of 17, base :math:`e`.
There is also a function called :numeric:`log10 <math/log10>` that
takes logarithms base 10.

.. index::
   pair: cos; math
   pair: tan; math
   pair: atan; math
   pair: radian; math
   pair: atan; pi

The second example finds the sine of the value of the variable radians.
C++ assumes that the values you use with :numeric:`sin <math/sin>`
and the other trigonometric
functions (:numeric:`cos <math/cos>`, :numeric:`tan <math/tan>`)
are in *radians*. 

.. note::
   To convert from degrees to radians, you can multiply by :math:`\pi/180`.

If you don’t happen to know :math:`\pi` to 15 digits, you can calculate
it using the :numeric:`atan <math/atan>` function.
The arctangent (or inverse tangent) of 1 is
:math:`\pi/4`, and multiplying by ``4`` evaluates to :math:`\pi`.


.. activecode:: math_functions_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Working with Angles

   This program also uses built-in functions from the cmath library,
   specifically the functions that deal with angles.  As you can see,
   we have a line of code that converts the default radians value to
   degrees.
   ~~~~
   #include <cmath>
   #include <iostream>

   int main () {
       const double pi = 4*atan(1);
       constexpr double degrees = 90;
       const double radians = degrees * pi / 180.0;
       std::cout << pi << '\t'
                 << degrees  << '\t'
                 << radians << '\n';
       return 0;
   }

The value ``pi`` can't be declared :lang:`constexpr` here, because
the functions in the math library are not ``constexpr``.
We can only use constant expressions to initialize something as
``constexpr``.
This is a part of the language that is actively changing!
Starting in C++17, many more parts of the standard library
have started to include ``constexpr`` versions of types and functions.

Note that some compilers do return ``constexpr`` values for the math
library functions, but this is generally considered a bug and
should not be counted on.

.. note::
   Constants introduced in C++20.

   C++20 defines several numeric constants useful in engineering and
   math. The :numeric:`full list of constants <constants>` is available
   on cppreference.com and are located in the header ``numbers``.
   For example:

   ::

      #include <numbers>

      int main() {
         double radians = 90 * std::numbers::pi / 180.0;
      }

Prior to the official inclusion of these constants, programmers needed to
either define their own, or use a third party library such as
https::boost.org/.
Some compilers define a macro ``M_PI``, but it is not universal and
should not be relied on.

   

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

We have been using header files since chapter 1.
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
The original C version of this header is ``math.h``

.. admonition:: Use C++ headers in C++

   Use the C++ versions of C header files when writing C++.
   Although the language allows you to use either,
   it is considered a best practice to use the C++ headers
   when writing C++ code.

   There are some subtle differences in the guarantees that the
   different headers support.

For compatibility reasons, the functions in ``cmath`` are also in the ``std``
namespace, however, they are also in the *global namespace*.
For this reason, you often see math functions used without the 
``std::`` namespace prefix.

.. note::
   Fun fact!

   All of the original C headers, such as ``math.h`` have been deprecated
   since the first ISO standard, C++98.
   However, they are now slated to be 'undeprecated' as of C++23.

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

              +   This function computes the 'common' logarithm.

          -   ``pow``

              +   This function raises an expression to a power.

          -   ``ln``

              -   The natural log function is actually called ``log``.

-----

.. admonition:: More to Explore

   - From cppreference.com

     - C++ math: :numeric:`sin <math/sin>`,
       :numeric:`cos <math/cos>`,
       :numeric:`tan <math/tan>`,
       :numeric:`atan <math/atan>`,
       :numeric:`log <math/log>`
     - :numeric:`constants` (such as :math:`\pi`)
     - :cpp:`C++ Standard Library headers <header>`


