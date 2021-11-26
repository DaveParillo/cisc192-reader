Tables
------

One of the things loops are good for is generating tabular data. For
example, before computers were readily available, people had to
calculate logarithms, sines and cosines, and other common mathematical
functions by hand. To make that easier, there were books containing long
tables where you could find the values of various functions. Creating
these tables was slow and boring, and the result tended to be full of
errors.

When computers appeared on the scene, one of the initial reactions was,
“This is great! We can use the computers to generate the tables, so
there will be no errors.” That turned out to be true (mostly), but
shortsighted. Soon thereafter computers and calculators were so
pervasive that the tables became obsolete.

Well, almost. It turns out that for some operations, computers use
tables of values to get an approximate answer, and then perform
computations to improve the approximation. In some cases, there have
been errors in the underlying tables, most famously in the table the
original Intel Pentium used to perform floating-point division.

Although a “log table” is not as useful as it once was, it still makes a
good example of iteration. 

.. activecode:: tables_AC_1
   :language: cpp
   :caption: Tables

   The active code below outputs a sequence of values in the left column 
   and their logarithms in the right column.
   ~~~~
   #include <cmath>
   #include <iostream>

   int main() {
      int x = 1;
      while (x < 10) {
          std::cout << x << '\t'
                    << std::log(x) << '\n';
          x = x + 1;
      }
      return 0;
   }

.. index::
   single: tab

The two character sequence ``\t`` represents a **tab** character.
The sequence ``\n`` represents a newline character.
These sequences can be included anywhere
in a string, although in these examples the sequence is the whole
string.

.. index::
   pair: tab; tab stops

A tab character causes the cursor to shift to the right until it reaches
one of the **tab stops**, which are normally every eight characters. As
we will see in a minute, tabs are useful for making columns of text line
up.

A newline character has the same effect as ``endl``; it causes
the cursor to move on to the next line. 
The ``endl`` function not only prints the newline,
but also flushes the output buffer.
If it is important to produce a line of output immediately,
then I use ``endl``.
But because ``endl`` always performs this extra task,
even when it not needed (and it is relatively expensive),
I typically use ``\n`` when possible and use ``endl``
when the situation requires it.

The output of this program is

::

   1      0
   2      0.693147
   3      1.09861
   4      1.38629
   5      1.60944
   6      1.79176
   7      1.94591
   8      2.07944
   9      2.19722

If these values seem odd, remember that the ``log`` function uses base
:math:`e`. Since powers of two are so important in computer science, we
often want to find logarithms with respect to base 2. To do that, we can
use the following formula:

.. math:: \log_2 x = \frac {log_e x}{log_e 2}

Changing the output statement to

::

         cout << x << "\t" << log(x) / log(2.0) << endl;

yields

::

   1      0
   2      1
   3      1.58496
   4      2
   5      2.32193
   6      2.58496
   7      2.80735
   8      3
   9      3.16993

We can see that 1, 2, 4 and 8 are powers of two, because their
logarithms base 2 are round numbers.

.. activecode:: tables_AC_2
   :language: cpp
   :caption: Tables

   If we wanted to find the logarithms of other powers of two, 
   we could modify the program like this. Run the active code below.
   ~~~~
   #include <cmath>
   #include <iostream>
  
   int main() {
     int x = 1;
     while (x < 100) {
       std::cout << x << "\t" 
                 << std::log(x) / std::log(2) << endl;
       x = x * 2;
     }
   }

.. index::
   single: geometric sequence

Now instead of adding something to ``x`` each time through the loop,
which yields an arithmetic sequence, we multiply ``x`` by something,
yielding a **geometric** sequence. The result is:

::

   1      0
   2      1
   4      2
   8      3
   16     4
   32     5
   64     6

Because we are using tab characters between the columns, the position of
the second column does not depend on the number of digits in the first
column.

Log tables may not be useful any more, but for computer scientists,
knowing the powers of two is! As an exercise, modify this program so
that it outputs the powers of two up to 65536 (that’s :math:`2^{16}`).
Print it out and memorize it.

.. tabbed:: self_check

   .. tab:: Q1

      .. activecode:: tables_AC_3
         :language: cpp
         :caption: Tables

         Modify the active code below so that it outputs the power of two
         up to 65536, which is :math:`2^{16}`. If you get stuck, you can 
         reveal the extra problem at the end for help. 
         ~~~~
         #include <iostream>
         #include <cmath>
         using namespace std;

         int main() {
           int x = 1;
           while (x < 100) {
                cout << x << "\t" 
                     << log(x) / log(2) << endl;
                x = x * 2;
           }
         }

      .. reveal:: 6_4_1
         :showtitle: Reveal Problem
         :hidetitle: Hide Problem

         .. parsonsprob:: tables_1
            :numbered: left
            :adaptive:
         
            Let's write the code that prints out the powers of two.
            -----
            int main() {
            =====
               int x = 1;
            =====
               while (x < 17) {
            =====
               while (x < 16) {                                #paired 
            =====
                  cout << x << "\t" << pow(2, x) << endl;
            =====
                  cout << x << "\t" << pow(x, 2) << endl;      #paired 
            =====
                  x++;
               }
            }


   .. tab:: Q2

      .. fillintheblank:: tables_2

          What is the equivalent of endl, and typically used at the end of a string?

          - :(?:(?:\\n)|(?:(?:n|N)ewline\s(?:c|C)haracter)): Is the correct answer!
            :.*: Try again!

   .. tab:: Q3

      .. fillintheblank:: tables_3

          How would you write a tab character?

          - :(?:\\t): Correct!
            :.*: Try again!

   .. tab:: Q4

      .. mchoice:: tables_4
         :practice: T
         :answer_a: Change ``pow(x,2)`` to ``pow(3,x)`` and change ``x = x + 1`` to ``x = x + 2``.
         :answer_b: Change ``pow(x,2)`` to ``pow(x,3)``.
         :answer_c: Change ``pow(x,2)`` to ``pow(x,3)`` and change ``x = x + 1`` to ``x = x + 2``.
         :answer_d: Change ``x < 11`` to ``x < 6`` and change ``pow(x,2)`` to ``pow(x,3)``.
         :correct: c
         :feedback_a: Check the order of the ``pow`` function!
         :feedback_b: This will print out the first ten perfect cubes.
         :feedback_c: Changing both the ``pow`` function and the increment in this way gives us the right answer.
         :feedback_d: This will print out the first five perfect cubes, but not the first five odd perfect cubes.

         How can we modify the code below to print out a table of the first five odd numbers and their perfect cubes?

         .. code-block:: cpp

            int main() {
              int x = 1;
              while (x < 11) {
                cout << x << "\t" << pow(x, 2) << endl;
                x = x + 1;
              }
            }

