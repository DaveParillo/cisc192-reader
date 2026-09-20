.. index::
   pair: keyword; return

The ``return`` keyword
----------------------
The :lang:`return` keyword immediately returns from a function.
If the function returns a value, then an expression or value
may follow the return keyword.

The first example is area, which takes a double as a parameter,
and returns the area of a circle with the given radius:

::

    double area (double radius) {
      const double pi = 4*atan (1.0);
      double area = pi * radius * radius;
      return area;
    }

The first thing you should notice is that the beginning of the function
definition is different. Instead of ``void``, which indicates a ``void``
function, we see ``double``, which indicates that the return value from this
function will have type ``double``.

Void functions do not need a return statement, but all functions that declare
a return value **must** have at least one return statement, or the
program will crash when the function is called.

.. note::
   Functions can have any return type in C++.  The return type is always
   specified before the name of the function.

Also, notice that the last line is an alternate form of the return
statement that includes a return value. This statement means, “return
immediately from this function and use the following expression as a
return value.” The expression you provide can be arbitrarily
complicated, so we could have written this function more concisely:

::

    double area (double radius) {
      return 4*atan(1.0) * radius * radius;
    }

..	index::
	  pair: variables; temporary variables

On the other hand, **temporary** variables like ``area`` often make
debugging easier. In either case, the type of the expression in the
return statement must match the return type of the function. In other
words, when you declare that the return type is ``double``, you are making a
promise that this function will eventually produce a ``double``. If you try
to return with no expression, or an expression with the wrong type, the
compiler will take you to task.


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: return_vals_1

         What should the return type of the below function be?

         ::

             ________ weather (int temp) {
              string outside = "";
              if (temp < 50) {
                outside = "cold";
              }
              else {
                outside = "warm"
              }
              return outside;
             }


         - [ ] double

           There are no doubles used in this function.
         - [ ] int

           The parameter does not have to be the same type as the return type.
         - [x] string

           The variable "outside" is being returned, which is of string type.
         - [ ] char

           The return type is actually a string of chars.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: return_vals_2

         What will print?

         ::

             #include <iostream>
             using namespace std;

             int timesTwo(int x) {
               int y = x;
               return y;
               y = y * 2;
             }

             int main () {
               int i = 2;
               cout << timesTwo(i);
               return 0;
             }

         - [ ] 4

           The function returns y before reaching the line where y is doubled.
         - [x] 2

           Because the return statement in the timesTwo function returns prior to the modification of y, 2 is returned and then printed.
         - [ ] 16

           The function returns y before reaching the line where y is doubled.
         - [ ] The function does not return.

           The function has an integer return type, so it WILL return an int.

   .. tb-tab:: Q3

      .. tb-blank::
         :name: return_vals_3

         A variable that exists only inside a function, is called a {{blank}} variable.

         .. tb-answer::
            :match: temporary
            :feedback: Temporary variables are useful for calculating and returning values inside functions since they are short-lived.
            :incorrect: Try again!

-----

.. admonition:: More to Explore

   - The :lang:`return` keyword from cppreference.com

