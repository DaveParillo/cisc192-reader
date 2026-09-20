The Modulus Operator
--------------------

.. index::
   single: modulus operator

Not all math operators in C++ work on any numeric data type.
The modulus operator works on integers (and integer expressions) only and
yields the *remainder* when the first operand is divided by the second.
In C++, the modulus operator is a percent sign, ``%``. The syntax is exactly
the same as for other operators:

This program shows the difference between the division operator
and the modulus operator.

.. tb-code:: cpp
   :name: mod_operator_AC_1
   :caption: Modulus Operations
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>

   int main () {
       using std::cout;

       int quotient = 7 / 3;
       int remainder = 7 % 3;
       cout << "The quotient is: " << quotient
            << "\n_the remainder is: " << remainder << '\n';
   }

The first operator, integer division, yields 2. The second operator
yields 1. Thus, 7 divided by 3 is 2 with 1 left over.

Although modulus is a curiosity in a typical algebra class,
it has many useful applications in algorithms.
The modulus operator turns out to be surprisingly useful. For example,
you can check whether one number is divisible by another: if ``x % y`` is
zero, then x is divisible by y.

Also, you can use the modulus operator to extract the rightmost digit or
digits from a number. For example, ``x % 10`` yields the rightmost digit of
x (in base 10). Similarly ``x % 100`` yields the last two digits.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: mod_operator_1

         How do you know whether the variable x is odd?


         - [ ] Use x % 2, and if the result is 0, it is odd.

           If you divide a number by two and it has no remainder, that means it is an even number!
         - [x] Use x % 2, and if the result is  1, it is odd.

           If you divide a number by two and it has a remainder of one, that means it is an odd number!
         - [ ] Use x / 2, and if the result is 0, it is odd.

           Dividing a number by two won't give us the information we want.
         - [ ] Use x / 2, and if the result is  1, it is odd.

           Dividing a number by two won't give us the information we want.

   .. tb-tab:: Q2

      .. tb-match::
         :name: mod_operator_2

         Match the modulo expression to its result.

         3 % 2
            1
         2 % 3
            2
         6 % 2
            0
         9 % 6
            3

