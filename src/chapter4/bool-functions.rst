.. _fruitful-functions-bool-functions:
.. _bool-functions:

Bool Functions
--------------
.. index::
   pair: functions; bool functions

Functions can return bool values just like any other type, which is
often convenient for hiding complicated tests inside functions. For
example:

::

    bool is_digit (int x) {
      if (x >= 0 && x < 10) {
        return true;
      } 
      return false;
    }

The name of this function is ``is_digit``. It is common to give boolean
functions names that sound like yes/no questions. The return type is
bool, which means that every return statement has to provide a bool
expression.

The code itself is straightforward, although it is a bit longer than it
needs to be. Remember that the expression ''x >= 0 && x < 10'' has type
bool, so there is nothing wrong with returning it directly, and avoiding
the if statement altogether:

::

    bool is_digit (int x) {
      return (x >= 0 && x < 10);
    }

In main you can call this function in the usual ways:

::

      std::cout << is_digit (2) << '\n';
      bool is_big = !is_digit (17);

.. tb-code:: cpp
   :name: bool_fun_AC_1
   :caption: Bool Functions

   #include <cmath>
   #include <iostream>

   bool is_digit (int x) {
     return (x >= 0 && x < 10);
   }

   int main () {
     std::cout << is_digit (2) << '\n';
     bool is_big = !is_digit (17);
     std::cout << is_big;
     return 0;
   }

The first line outputs the value true because 2 is a single-digit
number. Unfortunately, when C++ outputs bools, it does not display the
words true and false, but rather the integers 1 and 0.

The second line assigns the value true to ``is_big`` only if 17 is *not* a
single-digit number.

The most common use of bool functions is inside conditional statements

::

   if (is_digit (x)) {
     cout << "x is little\n";
   } 
   else {
     cout << "x is big\n";
   }

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-match::
         :name: bool_fun_1

         Match the conditional statement to its output, assuming it is outputted using cout and x = 3.

         (x%2 == 1 && x == 7)
            0
         (x%2 == 0 || x + 1 == 4)
            1

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: bool_fun_2

         Construct a block of code that first checks if a number is positive,
         then checks if it's even, and then prints out a message to classify
         the number.  It prints "both" if the number is both positive and even,
         "even" if the number is only even, "positive" if it is only positive,
         and "neither" if it is neither positive nor even. Use ``x`` for the number.

         .. code-block:: cpp

            {{group}}
            bool positive = (x > 0);
            {{endgroup}}
            {{distractor}}
            {{group}}
            bool positive = (x < 0); #distractor
            {{endgroup}}
            {{group}}
            bool even = (x % 2 == 0);
            {{endgroup}}
            {{distractor}}
            {{group}}
            bool even = (x % 2 != 0); #distractor
            {{endgroup}}
            {{group}}
            if (even && positive) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            if (even || positive) {  #distractor
            {{endgroup}}
            {{group}}
             cout << "both"; }
            {{endgroup}}
            {{group}}
            else if (even) {
            {{endgroup}}
            {{group}}
             cout << "even"; }
            {{endgroup}}
            {{group}}
            else if (positive) {
            {{endgroup}}
            {{group}}
             cout << "positive"; }
            {{endgroup}}
            {{group}}
            else {
            {{endgroup}}
            {{group}}
             cout << "neither"; }
            {{endgroup}}

-----

.. admonition:: More to Explore

   - From cppreference.com
     
     - :lang:`Keyword bool <types>`
     - :lang:`Function declarartions <function>`
     - Function :string:`isdigit <byte/isdigit>` is part of the
       byte string standard library in header :header:`cctype`.
     
