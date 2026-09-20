.. _iteration-two-dimensional-tables:

Two-dimensional tables
----------------------

A two-dimensional table is a table where you choose a row and a column
and read the value at the intersection. A multiplication table is a good
example. Let’s say you wanted to print a multiplication table for the
values from 1 to 6.

A good way to start is to write a simple loop that prints the multiples
of 2, all on one line.

Run the active code below, which uses a simple loop that prints the multiples
of 2, all on one line.

.. tb-code:: cpp
   :name: two_d_tables_ac_1
   :caption: Two-dimensional tables

   #include <iostream>

   int main() {
     int i = 1;
     while (i <= 6) {
       std::cout << 2*i << "   ";
       i = i + 1;
     }
     cout << '\n';
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

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: mce_5_1

         What should be the return type of the function ``convert_to_celsius``?

         .. code-block:: cpp

           ______ convert_to_celsius (double fahrenheit) {
             double celsius;
             celsius = (fahrenheit - 32) * 5 / 9;
             return celsius;
           }

         - [ ] ``int``

           - What variable are we returning in the function, and what is the variable's type? 

         - [x] ``double``

           + The function returns ``celsius``, which is a ``double``.

         - [ ] ``string``

           - What variable are we returning in the function, and what is the variable's type? 

         - [ ] ``void``

           - Since we are returning something in the function, the function is not ``void``.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: mce_5_2

         What would be returned by ``secret_function`` if the input was 14?

         .. code-block:: cpp

           int secret_function (int input) {
             if (input % 2 == 0) {
               return 3 * input - 2;
             }
             else {
               if (input % 7 == 0) {
                 return input;
               }
               return 2 * input + 9;
             }
             return input + 4;
           }  

         - [ ] 14

           - Although 14 is divisible by 7, take another look at the conditionals. 

         - [ ] 18

           - The flow of code would never reach the last return statement.

         - [ ] 36

           - Check your order of operations! 

         - [ ] 37

           - Take a closer look at the conditional statements. 

         - [x] 40

           + Since 14 is divisible by 2, the function returns two less than three times 14.

