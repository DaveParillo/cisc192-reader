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
      cout << "x is positive" << endl;
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
instead of a double ``==``. Remember that = is the assignment operator, and
``==`` is a comparison operator. Also, there is no such thing as ``=<`` or ``=>``.

.. note::
   Both sides of a conditional operator have to be the same type.

Despite automatic type conversion, you can only compare ``int`` s to ``int`` s and
``double`` s to ``double`` s. Unfortunately, at this point you can’t compare ``string`` s
at all! There is a way to compare them, but we won’t get to it for a couple of
chapters.

Observe the conditional statement below.

.. activecode:: conditional_execution_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Testing Values of x

   This program shows how you can use conditional statements to
   assess true/false situations.
   ~~~~
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
       return 0;
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

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: conditional_execution_1
         :answer_a: Change the value of x to be anything less than 6.
         :answer_b: Change the value of x to 13.
         :answer_c: Change the sign of the last conditional statement to x > 6.
         :answer_d: Change the value of the return from 0 to "Bigger!"
         :correct: b
         :feedback_a: While "Bigger" would now print, the other two statements would not!
         :feedback_b: Now, none of the statements would print!
         :feedback_c: Now, all of the statements would print.
         :feedback_d: main returns an int, so trying to make it return a string will cause an error.

         Observe the code above. "Bigger" never prints! How can you modify this so that all of the statements print?

   .. tab:: Q2

      .. dragndrop:: conditional_execution_2
         :feedback: Try again!
         :match_1: x != y|||x = 10, y = 2
         :match_2: x <= y|||x = 5, y = 5
         :match_3: x < y|||x = 2, y = 10

         Match the operator to values of x and y that would return true.


   .. tab:: Q3

      .. dragndrop:: conditional_execution_3
         :feedback: Try again!
         :match_1: x == y|||x = 3, y = 3
         :match_2: x >= y|||x = 6, y = 2
         :match_3: x < y|||x = 2, y = 6

         Match the operator to values of x and y that would return true.

