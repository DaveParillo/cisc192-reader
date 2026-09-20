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

.. tb-code:: cpp
   :name: functions_AC_1
   :caption: Two-dimensional tables
   :compileargs: ['-Wall', '-std=c++11']

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

.. tb-code:: cpp
   :name: functions_AC_2
   :caption: Two-dimensional tables
   :compileargs: ['-Wall', '-std=c++11']

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


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: functions_1

         What is a function in C++?


         - [x] A named sequence/group of statements that perform a particular task.

           Yes, a function is a named sequence of statements.
         - [ ] Any sequence of statements.

           While functions contain sequences of statements, not all sequences of statements are considered functions.
         - [ ] A mathematical expression that calculates a value.

           While some functions do calculate values, the python idea of a function is slightly different from the mathematical idea of a function in that not all functions calculate values.  Consider, for example, the turtle functions in this section.   They made the turtle draw a specific shape, rather than calculating a value.
         - [ ] A statement of the form x = 5 + 4.

           This statement is called an assignment statement.  It assigns the value on the right (9), to the name on the left (x).

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: functions_2

         Create a function called ``absoluteValue``, which returns the absolute value of a parameter ``num``. Assume you do not have access to ``#include <cmath>``.

         .. code-block:: cpp

            {{group}}
            int absoluteValue (int num) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void absoluteValue (int num) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            int absoluteValue (int num) #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            void absoluteValue (int num) #distractor
            {{endgroup}}
            {{group}}
              if (num > 0) {
            {{endgroup}}
            {{group}}
                return num;
              }
            {{endgroup}}
            {{group}}
              else {
            {{endgroup}}
            {{group}}
                int absNum = -(num);
            {{endgroup}}
            {{group}}
                return absNum;
              }
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-choice::
         :name: functions_3

         What is of these is NOT a reason that functions are useful?

         - [ ] Once you write and debug a function, you can reuse it.

           The reusability of functions is very useful.
         - [ ] Makes your program easier to read and debug.

           By abstracting blocks of code, functions make your code easier to read and understand.
         - [ ] Functions facilitate both recursion and iteration.

           Recursive functions and iterative functions are useful.
         - [x] None of the above.

           All of the choices above are reasons for why functions are useful.

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Function definitions <definition>` and
       :lang:`declarations`
     - :lang:`Functions <functions>`
     - :lang:`Arithmetic operators <operator_arithmetic>`
     - :lang:`Assignment operators <operator_assignment>`

