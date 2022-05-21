The Modulus Operator
--------------------

.. index::
   single: modulus operator

The modulus operator works on integers (and integer expressions) and
yields the *remainder* when the first operand is divided by the second.
In C++, the modulus operator is a percent sign, ``%``. The syntax is exactly
the same as for other operators:

.. activecode:: mod_operator_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Modulus Operations

   This program shows the difference between the division operator
   and the modulus operator.
   ~~~~
   #include <iostream>

   int main () {
       using std::cout;

       int quotient = 7 / 3;
       int remainder = 7 % 3;
       cout << "The quotient is: " << quotient
            << "\nThe remainder is: " << remainder << '\n';
       return 0;
   }

The first operator, integer division, yields 2. The second operator
yields 1. Thus, 7 divided by 3 is 2 with 1 left over.

The modulus operator turns out to be surprisingly useful. For example,
you can check whether one number is divisible by another: if ``x % y`` is
zero, then x is divisible by y.

Also, you can use the modulus operator to extract the rightmost digit or
digits from a number. For example, ``x % 10`` yields the rightmost digit of
x (in base 10). Similarly ``x % 100`` yields the last two digits.

.. tabbed:: tab_check

   .. tab:: Q1

      .. mchoice:: mod_operator_1
         :answer_a: Use x % 2, and if the result is 0, it is odd.
         :answer_b: Use x % 2, and if the result is  1, it is odd.
         :answer_c: Use x / 2, and if the result is 0, it is odd.
         :answer_d: Use x / 2, and if the result is  1, it is odd.
         :correct: b
         :feedback_a: If you divide a number by two and it has no remainder, that means it is an even number!
         :feedback_b: If you divide a number by two and it has a remainder of one, that means it is an odd number!
         :feedback_c: Dividing a number by two won't give us the information we want.
         :feedback_d: Dividing a number by two won't give us the information we want.

         How do you know whether the variable x is odd?


   .. tab:: Q2

      .. dragndrop:: mod_operator_2
          :feedback: Try again!
          :match_1:  3 % 2|||1
          :match_2: 2 % 3|||2
          :match_3: 6 % 2|||0
          :match_4: 9 % 6|||3

          Match the modulo expression to its result.
