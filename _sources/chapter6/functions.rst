Functions
---------
In the last section I mentioned “all the things functions are good for.”
About this time, you might be wondering what exactly those things are.
Here are some of the reasons functions are useful:

-  By giving a name to a sequence of statements, you make your program
   easier to read and debug.

-  Dividing a long program into functions allows you to separate parts
   of the program, debug them in isolation, and then compose them into a
   whole.

-  Functions facilitate both recursion and iteration.

-  Well-designed functions are often useful for many programs. Once you
   write and debug one, you can reuse it.

For example, instead of writing the 53 lines of code below...

.. activecode:: functions_AC_1
   :language: cpp
   :caption: Two-dimensional tables

   #include <iostream>
   using std::cout;
 
   int main() {
      int x = 4;
      x = x * 2;
      x = x / 2;
      x = x + 2;
      x = x - 2;
      cout << x << '\n';
      x = 13;
      x = x * 2;
      x = x / 2;
      x = x + 2;
      x = x - 2;
      cout << x << '\n';
      x = 100;
      x = x * 2;
      x = x / 2;
      x = x + 2;
      x = x - 2;
      cout << x << '\n';
      x = 22;
      x = x * 2;
      x = x / 2;
      x = x + 2;
      x = x - 2;
      cout << x << '\n';
      x = 220;
      x = x * 2;
      x = x / 2;
      x = x + 2;
      x = x - 2;
      cout << x << '\n';
      x = 0;
      x = x * 2;
      x = x / 2;
      x = x + 2;
      x = x - 2;
      cout << x << '\n';
      x = 1000;
      x = x * 2;
      x = x / 2;
      x = x + 2;
      x = x - 2;
      cout << x << '\n';
      x = 254;
      x = x * 2;
      x = x / 2;
      x = x + 2;
      x = x - 2;
      cout << x << '\n';
   }

A function allows you to reduce it to the 21 lines of code below.
The function makes it easier to read, debug, and use
the function many times without rewriting it each time.

.. activecode:: functions_AC_2
  :language: cpp
  :caption: Two-dimensional tables

  #include <iostream>

  void all_operators(int x) {
      x = x * 2;
      x = x / 2;
      x = x + 2;
      x = x - 2;
      std::cout << x << '\n';
  }

  int main() {
      all_operators(4);
      all_operators(13);
      all_operators(100);
      all_operators(22);
      all_operators(220);
      all_operators(0);
      all_operators(1000);
      all_operators(254);
  }


  .. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: functions_1
         :practice: T
         :answer_a: A named sequence/group of statements that perform a particular task.
         :answer_b: Any sequence of statements.
         :answer_c: A mathematical expression that calculates a value.
         :answer_d: A statement of the form x = 5 + 4.
         :correct: a
         :feedback_a: Yes, a function is a named sequence of statements.
         :feedback_b: While functions contain sequences of statements, not all sequences of statements are considered functions.
         :feedback_c: While some functions do calculate values, the python idea of a function is slightly different from the mathematical idea of a function in that not all functions calculate values.  Consider, for example, the turtle functions in this section.   They made the turtle draw a specific shape, rather than calculating a value.
         :feedback_d: This statement is called an assignment statement.  It assigns the value on the right (9), to the name on the left (x).

         What is a function in C++?


   .. tab:: Q2

      .. parsonsprob:: functions_2
         :numbered: left
         :adaptive:

         Create a function called ``absoluteValue``, which returns the absolute value of a parameter ``num``. Assume you do not have access to ``#include <cmath>``.
         -----
         int absoluteValue (int num) {
         =====
         void absoluteValue (int num) { #distractor
         =====
         int absoluteValue (int num) #distractor
         =====
         void absoluteValue (int num) #distractor
         =====
           if (num > 0) {
         =====
             return num; 
           }
         =====
           else {
         =====
             int absNum = -(num);
         =====
             return absNum;
           } 
         }


   .. tab:: Q3

      .. mchoice:: functions_3
         :practice: T
         :answer_a: Once you write and debug a function, you can reuse it.
         :answer_b: Makes your program easier to read and debug.
         :answer_c: Functions facilitate both recursion and iteration.
         :answer_d: None of the above.
         :correct: d
         :feedback_a: The reusability of functions is very useful.
         :feedback_b: By abstracting blocks of code, functions make your code easier to read and understand.
         :feedback_c: Recursive functions and iterative functions are useful.
         :feedback_d: All of the choices above are reasons for why functions are useful.

         What is of these is NOT a reason that functions are useful?

