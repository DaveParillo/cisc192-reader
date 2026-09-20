.. _chained-conditional:

Chained Conditionals
--------------------

.. index::
   single: chaining
   single: chained conditionals

Sometimes you want to check for a number of related conditions and
choose one of several actions. One way to do this is by **chaining** a
series of ifs and elses:

The following program classifies a number (x) as positive,
negative, or zero.  Feel free to change the value of x to 
make sure it works.

.. tb-code:: cpp
   :name: chained_conditionals_AC_1
   :caption: Classifying a Number as +, -, or 0.
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>

   int main () {
       int x = -4;
       if (x > 0) 
       {
           std::cout << "x is positive\n";
       }
       else if (x < 0) 
       {
           std::cout << "x is negative\n";
       }
       else 
       {
           std::cout << "x is zero\n";
       }
   }

Try changing the value of x above to see how the output is impacted.

.. note::
   If you have adjacent ``if`` statements, the program will go through 
   executing each conditional, regardless if the conditions are met.  
   However, as soon as you add an ``else`` or even an ``else if`` statement,
   the program will stop executing the chained conditionals as soon as a 
   condition is met.


These chains can be as long as you want, although they can be difficult
to read if they get out of hand. One way to make them easier to read is
to use standard indentation, as demonstrated in these examples. If you
keep all the statements and squiggly-braces lined up, you are less
likely to make syntax errors and you can find them more quickly if you
do.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: chained_conditionals_1

         What will print after the following code is executed?

         ::

             #include <iostream>
             using namespace std;

             int main () {
               int x = 10;
               if (x > 8) {
                 cout << "One! ";
               }
               if (x > 6) {
                 cout << "Two! ";
               }
               if (x > 3) {
                 cout << "Three!" << '\n';
               }
               return 0;
             }


         - [ ] Three!

           Make note of the use of "if" instead of "else if" or "else".
         - [ ] One!

           Make note of the use of "if" instead of "else if" or "else".
         - [ ] One! Two!

           Make note of the use of "if" instead of "else if" or "else".
         - [x] One! Two! Three!

           When we have "if" statments, but no "else if" or "else", every condition will be checked.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: chained_conditionals_2

         What will print after the following code is executed?

         ::

             #include <iostream>
             using namespace std;

             int main () {
               int x = 10;
               if (x > 8) {
                 cout << "One! " ;
               }
               else if (x > 6) {
                 cout << "Two! ";
               }
               else {
                 cout << "Three!" << '\n';
               }
               return 0;
             }


         - [ ] Three!

           Remember that only one action will be completed in a chain of "ifs", "else ifs", and "ifs"
         - [x] One!

           The chain of "ifs", "else ifs", and "elses" results in only one action being completed.
         - [ ] One! Two!

           Remember that a chain of "ifs", "else ifs", and "elses" will result in only one action being completed.
         - [ ] One! Two! Three!

           Remember that a chain of "ifs", "else ifs", and "elses" will result in only one action being completed.

   .. tb-tab:: Q3

      .. tb-choice::
         :name: chained_conditionals_3

         What will print after the following code is executed?

         ::

             #include <iostream>
             using namespace std;

             int main () {
               int x = 7;
               if (x > 8) {
                 cout << "One! " ;
               }
               if (x > 6) {
                 cout << "Two! ";
               }
               if (x > 3) {
                 cout << "Three!" << '\n';
               }
               return 0;
             }


         - [ ] Two!

           Make note of the use of "if" instead of "else if" or "else".
         - [x] Two! Three!

           When we have "if" statments, but no "else if" or "else", every condition will be checked.
         - [ ] One! Two!

           The first statement will not be executed because x > 8 is not true.  Also, make note of the use of "if" instead of "else if" or "else".
         - [ ] One! Two! Three!

           The first statement will not be executed because x > 8 is not true.

   .. tb-tab:: Q4

      .. tb-choice::
         :name: chained_conditionals_4

         What will print after the following code is executed?

         ::

             #include <iostream>
             using namespace std;

             int main () {
               int x = 7;
               if (x > 8) {
                 cout << "One! " ;
               }
               else if (x > 6) {
                 cout << "Two! ";
               }
               else {
                 cout << "Three!" << '\n';
               }
               return 0;
             }

         - [x] Two!

           Only one action will is completed in a chain of "ifs", "else ifs", and "ifs";
         - [ ] Two! Three!

           Remember that only one action will be completed in a chain of "ifs", "else ifs", and "ifs".
         - [ ] One! Two!

           The first condition will not be satisfied.  Also, a chain of "ifs", "else ifs", and "elses" will result in only one action being completed.
         - [ ] One! Two! Three!

           hge first condition will not be satisfied.  Also, a chain of "ifs", "else ifs", and "elses" will result in only one action being completed.

-----

.. admonition:: More to Explore

   - :lang:`if` and :lang:`comparison operators <operator_comparison>`
     from cppreference

