Two-dimensional tables
----------------------

A two-dimensional table is a table where you choose a row and a column
and read the value at the intersection. A multiplication table is a good
example. Let’s say you wanted to print a multiplication table for the
values from 1 to 6.

A good way to start is to write a simple loop that prints the multiples
of 2, all on one line.

.. activecode:: 2D_tables_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Two-dimensional tables

   Run the active code below, which uses a simple loop that prints the multiples
   of 2, all on one line.
   ~~~~
   #include <iostream>
 
   int main() {
     int i = 1;
     while (i <= 6) {
       std::cout << 2*i << "   ";
       i = i + 1;
     }
     cout << endl;
     return 0;
   }

.. index::
   pair: loop; variable

The first line initializes a variable named ``i``, which is going to act
as a counter, or **loop variable**. As the loop executes, the value of
``i`` increases from 1 to 6, and then when ``i`` is 7, the loop
terminates. Each time through the loop, we print the value ``2*i``
followed by three spaces. By omitting the newline from the first output
statement, we get all the output on a single line.

The output of this program is:

::

   2   4   6   8   10   12

.. index::
   single: encapsulate
   single: generalize

So far, so good. The next step is to **encapsulate** and **generalize**.

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: 2D_tables_1
         :answer_a: counter
         :answer_b: loop variable
         :answer_c: Both a and b
         :answer_d: None of the above
         :correct: c
         :feedback_a: Try again!
         :feedback_b: Try again!
         :feedback_c: Correct!
         :feedback_d: Try again!

         What is a good name for the variable x, found in the code block below?

         .. code-block:: cpp

            #include <iostream>

            int main() {
              int x = 1;
              while (x <= 6) {
                std::cout << 2*x << "   ";
                x = x + 1;
              }
              cout << endl;
              return 0;
            }

   .. tab:: Q2

      .. mchoice:: 2D_tables_2
         :answer_a: Change the first output statement to say cout << 3*x << endl;
         :answer_b: Change the first output statement to say cout << 3*x << \n;
         :answer_c: Change the second output statement to say cout << endl << endl;
         :answer_d: This code already prints each multiple on its own line.
         :correct: a
         :feedback_a: The addition of the endl will print the multiples of three on separate lines.
         :feedback_b: A newline character must be used in conjunction with a string. In this case, we are outputting an integer. To use a newline character in this scenario you must use quotes around it. (ex. "\n")
         :feedback_c: This would simply print out two new lines after all of the multiples have already printed on one line.
         :feedback_d: This code prints all multiples out on one line.

         Currently, the code below prints all of the multiples of three on one line. How can you change the output so that each multiple prints on its own line?

         .. code-block:: cpp

            #include <iostream>
            using std::cout;
            using std::endl;

              int main() {
              int x = 1;
              while (x <= 6) {
                cout << 3*x << "  ";
                x = x + 1;
              }
              cout << endl;
              return 0;
            }
