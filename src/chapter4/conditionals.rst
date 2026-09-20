.. _fruitful-functions-conditional-execution:

Conditional Execution
---------------------

.. index::
   single: conditional statement

In order to write useful programs, we almost always need the ability to
check certain conditions and change the behavior of the program
accordingly. **Conditional statements** give us this ability. The
simplest form is the if statement:

::

    if (x > 0) {
      cout << "x is positive\n";
    }

The expression in parentheses is called the condition. If it is true,
then the statements in brackets get executed. If the condition is not
true, nothing happens.

.. index::
   single: comparison operators

The condition can contain any of the **comparison operators**:

::

    x == y               // x equals y
    x != y               // x is not equal to y
    x > y                // x is greater than y
    x < y                // x is less than y
    x >= y               // x is greater than or equal to y
    x <= y               // x is less than or equal to y

Although these operations are probably familiar to you, the syntax C++
uses is a little different from mathematical symbols like :math:`=`,
:math:`\neq` and :math:`\le`. A common error is to use a single ``=``
instead of a double ``==``. Remember that ``=`` is the assignment operator, and
``==`` is a comparison operator.
Also, there is no such thing as ``=<`` or ``=>``.

.. note::
   Both sides of a conditional operator have to be the same type.

Despite automatic type conversion, you can only compare ``int``\s to ``int``\s,
``double``\s to ``double``\s, and ``string``\s to ``string``\s .

Observe the conditional statement below.

This program shows how you can use conditional statements to
assess true/false situations.

.. tb-code:: cpp
   :name: conditional_execution_AC_1
   :caption: Testing Values of x

   #include <iostream>
   using std::cout;

   int main () {
       int x = 12;
       if (x == 12) {
           cout << "Equal!\n";
       }
       if (x != 13) {
           cout << "Not equal!\n";
       }
       if (x < 6) {
           cout << "Bigger!\n";
       }
   }

.. note:: Forgetting to use ``==`` for equivalence is a common source of error!

   It is easy to forget and simply use ``=`` in a conditional:

   ::

       if (x = 12) {
           cout << "Equal!\n";
       }

   This is an assignment statment, which is legal here,
   but almost always not what you meant.
   This statement assigns 12 to x, then if the value is not zero,
   (12 is not 0), the if expression evaluates to true and
   execution continues into the if block.

   So in this case, it would print 'Equal!' even if the value of x
   was '3' before the if statement was executed.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: conditional_execution_1

         Observe the code above. "Bigger" doesn't print! How can you modify this so that all of the statements print?


         - [ ] Change the value of x to be anything less than 6.

           While "Bigger" would now print, the other two statements would not!
         - [ ] Change the value of x to 13.

           Now, none of the statements would print!
         - [x] Change the sign of the last conditional statement to x > 6.

           Now, all of the statements would print.
         - [ ] Change the value of the return from 0 to "Bigger!"

           main returns an int, so trying to make it return a string will cause an error.

   .. tb-tab:: Q2

      .. tb-match::
         :name: conditional_execution_2

         Match the operator to values of x and y that would return true.


         x != y
            x = 10, y = 2
         x <= y
            x = 5, y = 5
         x < y
            x = 2, y = 10

   .. tb-tab:: Q3

      .. tb-match::
         :name: conditional_execution_3

         Match the operator to values of x and y that would return true.


         x == y
            x = 3, y = 3
         x >= y
            x = 6, y = 2
         x < y
            x = 2, y = 6

-----

.. admonition:: More to Explore

   - :lang:`if` and :lang:`comparison operators <operator_comparison>`
     from cppreference.com

