The while statement
-----------------------

Using a ``while`` statement, we can rewrite ``countdown``:

.. activecode:: the_while_statement_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Multiple assignment

   Try running the active code below! Afterwards, try changing 9 to a different
   integer to see how the function works!
   ~~~~
   #include <iostream>
   using std::cout;

   void countdown (int n) {
     while (n > 0) {
       cout << n << endl;
       n = n-1;
     }
     cout << "Blastoff!" << endl;
   }

   int main() {
     countdown (9);
   }

You can almost read a ``while`` statement as if it were English. What
this means is, “While ``n`` is greater than zero, continue displaying
the value of ``n`` and then reducing the value of ``n`` by 1. When you
get to zero, output the word ‘Blastoff!’”

More formally, the flow of execution for a ``while`` statement is as
follows:

#. Evaluate the condition in parentheses, yielding ``true`` or
   ``false``.

#. If the condition is false, exit the ``while`` statement and continue
   execution at the next statement.

#. If the condition is true, execute each of the statements between the
   squiggly-braces, and then go back to step 1.

.. index::
   single: loop
   pair: loop; body

This type of flow is called a **loop** because the third step loops back
around to the top. Notice that if the condition is false the first time
through the loop, the statements inside the loop are never executed. The
statements inside the loop are called the **body** of the loop.

The body of the loop should change the value of one or more variables so
that, eventually, the condition becomes false and the loop terminates.
Otherwise the loop will repeat forever, which is called an **infinite
loop**. An endless source of amusement for computer scientists is the
observation that the directions on shampoo, “Lather, rinse, repeat,” are
an infinite loop.

.. warning::
   Make sure your while loops don't loop forever! If they are
   meant to terminate, make sure to change the value of a variable, like
   incrementing or decrementing a counter.

.. index::
   single: iteration

In the case of ``countdown``, we can prove that the loop will terminate
because we know that the value of ``n`` is finite, and we can see that
the value of ``n`` gets smaller each time through the loop (each
**iteration**), so eventually we have to get to zero. In other cases it
is not so easy to tell:

::

     void sequence (int n) {
       while (n != 1) {
         cout << n << endl;
         if (n%2 == 0) {           // n is even
           n = n / 2;
         } else {                  // n is odd
           n = n*3 + 1;
         }
       }
     }

The condition for this loop is ``n != 1``, so the loop will continue
until ``n`` is 1, which will make the condition false.

At each iteration, the program outputs the value of ``n`` and then
checks whether it is even or odd. If it is even, the value of ``n`` is
divided by two. If it is odd, the value is replaced by :math:`3n+1`. For
example, if the starting value (the argument passed to ``sequence``) is
3, the resulting sequence is 3, 10, 5, 16, 8, 4, 2, 1.

Since ``n`` sometimes increases and sometimes decreases, there is no
obvious proof that ``n`` will ever reach 1, or that the program will
terminate. For some particular values of ``n``, we can prove
termination. For example, if the starting value is a power of two, then
the value of ``n`` will be even every time through the loop, until we
get to 1. The previous example ends with such a sequence, starting with
16.

Particular values aside, the interesting question is whether we can
prove that this program terminates for *all* values of n. So far, no one
has been able to prove it *or* disprove it!

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: while_statement_1
         :practice: T
         :answer_a: n = 2
         :answer_b: n != 0
         :answer_c: n % 2 == 1
         :correct: a
         :feedback_a: A single equal sign is the assignment operator, not comparison.
         :feedback_b: This would be valid because it means the loop would run while n is not equal to 0.
         :feedback_c: This would be valid because it mean the loop would run until n was an even number.


         Which of the following is NOT a valid condition for a while statement?

   .. tab:: Q2

      .. mchoice:: while_statement_2
         :practice: T
         :answer_a: n starts at 10 and is incremented by 1 each time through the loop, so it will always be positive.
         :answer_b: The answer starts at 1 and is incremented by n each time, so it will always be positive.
         :answer_c: You cannot compare n to 0 in while loop.  You must compare it to another variable.
         :answer_d: In the while loop body, we must set n to False, and this code does not do that.
         :correct: a
         :feedback_a: The loop will run as long as n is positive. In this case, we can see that n will never become non-positive as the while statement condition will never be met.
         :feedback_b: While it is true that answer will always be positive, answer is not considered in the loop condition.
         :feedback_c: It is perfectly valid to compare n to 0. Though indirectly, this is what causes the infinite loop.
         :feedback_d: The loop condition must become False for the loop to terminate, but n by itself is not the condition in this case.

         The following code contains an infinite loop.  Which is the best explanation for why the loop does not terminate?

         .. code-block:: cpp

            int n = 10;
            int answer = 1;
            while (n > 0) {
              answer = answer + n;
              n = n + 1;
            }
            cout << answer;
           
   .. tab:: Q3

      .. mchoice:: while_statement_3
         :practice: T
         :answer_a: n % 2 = 0 and n = n + 1
         :answer_b: n % 2 != 0 and ++n
         :answer_c: n % 2 == 0 and n++
         :answer_d: n == "even" and n = n + 2
         :correct: c
         :feedback_a: A single equal sign is the assignment operator, not comparison.
         :feedback_b: The code is meant to print the **even** numbers from 0-20
         :feedback_c: The condition checks whether a number is even and increments the variable n
         :feedback_d: n is an int and here you are comparing it to a string.

         The following code is a program to print the **even numbers from 0 to 20**. The code contains blanks. What is the correct while statement condition and iteration needed in order for the code to run successfully.

         .. code-block:: cpp

            int n = 0;
            while (_____) {  // while statement condition
              cout << n << endl;
              _______; // iteration of the variable
            }

   .. tab:: Q4

      .. mchoice:: while_statement_4
         :practice: T
         :answer_a: 4 7
         :answer_b: 5 7
         :answer_c: 7 15
         :correct: c
         :feedback_a: Setting a variable so the loop condition would be false in the middle of the loop body does not keep the variable from actually being set.
         :feedback_b: Setting a variable so the loop condition would be false in the middle of the loop body does not stop execution of statements in the rest of the loop body.
         :feedback_c: After n becomes 5 and the test would be False, but the test does not actually come until after the end of the loop - only then stopping execution of the repetition of the loop.


         What is printed by this code?

         .. code-block:: cpp

            int n = 1;
            int x = 2;
            while (n < 5) {
              n = n + 1;
              x = x + 1;
              n = n + 2;
              x = x + n;
            }
            cout << n;
            cout << x;


