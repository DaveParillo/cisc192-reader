.. _return_early:

Returning early
---------------

.. index::
   single: return early

The ``return`` statement allows you to terminate the execution of a function
before you reach the end. One reason to use it is if you detect an error
condition:

.. activecode:: return_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Terminating a Function with a Return

   This program will terminate with a return statement if the argument
   provided is not positive.  Try running the code as is.  If you get
   an error message, try changing the value of x.
   ~~~~
   #include <iostream>
   #include <cmath>

   void print_logarithm (double x) {
       if (x <= 0.0) {
           std::cout << "Positive numbers only, please.\n";
           return;
       }
       double result = log (x);
       std::cout << "The log of " << x << " is " << result;
   }

    int main() {
        double y = -9.8;
        print_logarithm(y);
        return 0;
    }

This defines a function named ``print_logarithm`` that takes a ``double`` 
named ``x`` as a parameter.
The first thing it does is check whether x is less than
or equal to zero, in which case it displays an error message and then
uses ``return`` to exit the function. The flow of execution immediately
returns to the caller and the remaining lines of the function are not
executed.

I used a floating-point value on the right side of the condition because
there is a floating-point variable on the left.

Remember that any time you want to use one a function from the math
library, you have to include the header file ``<cmath>``.

Since main is the first function on the call stack,
putting ``return 0;`` in your main ends your program.

.. tabbed:: return_early_tabbed

   .. tab:: Q1

      Let's look back at a program from the :ref:`chained-conditional` section.
      How would your answer change?

      .. mchoice:: return_1
         :answer_a: One! Two! Three!
         :answer_b: Two! Three!
         :answer_c: Three!
         :answer_d: Two!
         :answer_e: One!
         :correct: d
         :feedback_a: Try again! Remember the function of return 0.
         :feedback_b: Try again! Remember the function of return 0.
         :feedback_c: Try again! Remember the function of return 0.
         :feedback_d: 8 is not greater than 8, so the first condition will not be met.
         :feedback_e: Take a look at the first conditional statement more closely.

         What will print?

         ::

             #include <iostream>
             using std::cout;

             int main () {
               int x = 8;
               if (x > 8) {
                 cout << "One! ";
                 return 0;
               }
               if (x > 6) {
                 cout << "Two! ";
                 return 0;
               }
               if (x > 3) {
                 cout << "Three!\n";
                 return 0;
               }
               return 0;
             }

   .. tab:: Q2

      Compare Q1 to this example.
      Look it over carefully.
      At first glance it looks the same, but the logic is different.

      .. mchoice:: return_2
         :answer_a: One! Two! Three!
         :answer_b: Two! Three!
         :answer_c: Three!
         :answer_d: Two!
         :answer_e: One!
         :correct: b
         :feedback_a: Take a look at the first conditional statement more closely.
         :feedback_b: 8 is not greater than 8, so it doesn't meet the first condition.
         :feedback_c: All of the following are "if" statements, with no return. There are no "else" statements.
         :feedback_d: All of the following are "if" statements, with no return. There are no "else" statements.
         :feedback_e: Take a look at the first conditional statement more closely.

         What will print?

         ::

             #include <iostream>
             using namespace std;

             int main () {
               int x = 8;
               if (x > 8) {
                 cout << "One! ";
               }
               if (x > 6) {
                 cout << "Two! ";
               }
               if (x > 3) {
                 cout << "Three!\n";
               }
               return 0;
             }

Sometimes it is tempting to have multiple return statements,
one in each branch of a conditional:

::

    double absolute_value (double x) {
      if (x < 0) {
        return -x;
      } 
      else {
        return x;
      }
    }

Since these returns statements are in an alternative conditional, only
one will be executed. Although it is legal to have more than one return
statement in a function, you should keep in mind that as soon as one is
executed, the function terminates without executing any subsequent
statements.

.. warning::
   If you put return statements inside of a chain of conditionals, then 
   you have to guarantee that *every possible path* through the program 
   hits a return statement.  If you forget, your program will crash.

..	index::
	  pair: code; dead code

Code that appears after a return statement, or any place else where it
can never be executed, is called **dead code**. Some compilers warn you
if part of your code is dead.

.. activecode:: return_vals_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Return Values

   Notice that there are two return statements in the code below.
   What if we pass zero as an argument, and neither conditional
   returns true?
   ~~~~
   #include <iostream>

   double absolute_value (double x) {
       if (x < 0) {
           return -x;
       } 
       else if (x > 0) {
           return x;
       }                          // WRONG!!
   }

   int main () {
       std::cout << absolute_value(0);
       return 0;
   }

This program is not correct because if x happens to be 0, then neither
condition will be true and the function will end without hitting a
return statement. Unfortunately, the program compiles and runs, 
but the return value when ``x == 0`` could be anything, 
and will probably be different in
different environments.

By now you are probably sick of seeing compiler errors, but as you gain
more experience, you will realize that the only thing worse than getting
a compiler error is *not* getting a compiler error when your program is
wrong.

Here’s the kind of thing that’s likely to happen: you test ``absolute_value``
with several values of x and it seems to work correctly. Then you give
your program to someone else and they run it in another environment. It
fails in some mysterious way, and it takes days of debugging to discover
that the problem is an incorrect implementation of ``absolute_value``. If
only the compiler had warned you!

From now on, if the compiler points out an error in your program, you
should not blame the compiler. Rather, you should *thank* the compiler for
finding your error and sparing you days of debugging. Some compilers
have an option that tells them to be extra strict and report all the
errors they can find. You should turn this option on all the time. The
implementation below would fix the error in the code.


.. activecode:: return_vals_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Return Values

   This code fixes the error in the previoius implementation of
   absolute_value.  If we pass 0 as an argument, the function will
   return 0.  Thus, every route through the conditonal is satisfied.

   In almost all cases, when you see an ``else`` after a ``return`` the code
   can be simplified to eliminate the else block entirely:

   ~~~~
   #include <iostream>

   double absolute_value (double x) {
       if (x < 0) {
           return -x;
       } 
       return x;
   }

   int main () {
      std::cout << absolute_value(0);
      return 0;
   }

.. index:: ternary operator

The basic ``if-else`` construct appears so often in programming
that C defines an operator for it -- the *ternary operator*.
The basic form is:

::

   CONDITION ? TRUE_VALUE : FALSE_VALUE ;

It is called a ternary, because it is the only operator that is
split into 3 parts.
The ternary operator simplifies our function even further.

::

   #include <iostream>

   double absolute_value (double x) {
       return x < 0? -x : x;
   }

   int main () {
      std::cout << absolute_value(0);
      return 0;
   }


As an aside, you should know that there is a function in the math
library called :cmath:`fabs` that calculates the absolute value of a
double correctly.


.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: dead_code_printing_1
         :answer_a: You get a child discount yay! 
         :answer_b: Sorry you have to pay full price. 
         :answer_c: nothing gets printed
         :answer_d: 9.50
         :correct: c
         :feedback_a: The function returns goes to the else block as age is not less than 5.
         :feedback_b: The function returns 9.50 before reaching the output statment.
         :feedback_c: The return statement is encountered before the cout statement.
         :feedback_d: Although 9.50 is returned there is no printing of this value.

         What will print?

         ::

             #include <iostream>

             double ticket_price(int age) {
                if(age<5) {
                    return 5.50;
                    std::cout << " You get a child discount yay!\n";
                } else {
                    return 9.50;
                    std::cout << " Sorry you have to pay full price.\n";
                }
                return 0.0; //to avoid compiler error
             }

             int main () {
               int years = 5;
               double price = ticket_price(5);
               return 0;
             }

-----

.. admonition:: More to Explore

   - From cppreference.com

     - C++ math: :cmath:`abs` and :cmath:`fabs`
     - The :lang:`ternary operator <operator_other>`

   - Clang-tidy rule `avoid else after return <https://releases.llvm.org/14.0.0/tools/clang/tools/extra/docs/clang-tidy/checks/readability-else-after-return.html>`__

