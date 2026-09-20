Outputting Variables
--------------------

You can output the value of a variable using the same commands we used
to output simple values. After observing the output, try inputting your own time!


This program outputs the current time, according to the values you
provide for hour and minute.

.. tb-code:: cpp
   :name: output_vars_AC_1
   :caption: Time Output
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>

   int main () {
       using std::cout;

       int hour = 11;
       int minute = 59;
       char colon = ':';

       cout << "The current time is "
       cout << hour
       cout << colon
       cout << minute
       cout << '\n';
   }


This program creates two integer variables named hour and minute, and a
character variable named colon. It assigns appropriate values to each of
the variables and then uses a series of output statements to generate
the following:

::

    The current time is 11:59

When we talk about “outputting a variable,” we mean outputting the
*value* of the variable. To output the *name* of a variable, you have to
put it in quotes. For example: ``cout << "hour";``  The output of this
statement is as follows.

::

    hour

As we have seen before, you can include more than one value in a single
output statement, which can make the previous program more concise:


This program does the same thing as the previous, but the print
statements have been condensed to one line.  This is better style.

.. tb-code:: cpp
   :name: output_vars_AC_2
   :caption: Condensing The Code
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>

   int main () {
       int hour = 11;
       int minute = 59;
       char colon = ':';

       std::cout << "The current time is " 
                 << hour << colon << minute << '\n';
   }


On one line, this program outputs a string, two integers, a character,
and the special end of line character. Very impressive!

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: output_vars_1

          prints when the following code is run?



         int main () {
           char a;
           char b;
           a = 'z';
           b = '8';
           cout << "a";
         }


         - [x] a

           The string, not the variable, a will be printed.
         - [ ] b

           b will not be printed.
         - [ ] z

           The cout statement prints a, not the value of the variable a.
         - [ ] 8

           z is the value of a and will not be printed
         - [ ] Nothing! There will be a compile error!

           There is no type mismatch, so there will not be a compile error.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: output_vars_2

          what prints?



         int main () {
           char a;
           char b;
           a = 'z';
           b = '8';
           cout << b;
         }


         - [ ] a

           The string a will not be printed.
         - [ ] b

           The string b will not be printed.
         - [ ] z

           z is the value of a and will not be printed.
         - [x] 8

           8 is the value of b will be printed!
         - [ ] Nothing! There will be a compile error!

           There is no type mismatch, so there will not be a compile error.

   .. tb-tab:: Q3

      .. tb-choice::
         :name: output_vars_3

         now, what prints?



         int main () {
           int x;
           char y;
           x = '3';
           y = 'e';
           cout << 'y';
         }


         - [ ] x

           Take a look at the code again.
         - [ ] y

           Take a look at the code again.
         - [ ] 3

           Take a look at the code again.
         - [ ] e

           Take a look at the code again.
         - [x] Nothing! There will be a compile error!

           There is a type mismatch, so there will be a compile error!

   .. tb-tab:: Q4

      .. tb-match::
         :name: output_vars_4

         Match the variable initialization to its correct type.


         x = 2
            int
         y = "2"
            string
         z = '2'
            char

   .. tb-tab:: Q5

      .. tb-parsons::
         :name: output_vars_5

         Construct a main function that assigns "Hello" to the variable h, then prints out h's value.

         .. code-block:: cpp

            {{group}}
            #include <iostream>
            {{endgroup}}
            {{group}}
            #include <string>
            {{endgroup}}
            {{group}}
            int main () {
            {{endgroup}}
            {{group}}
             std::string h;
            {{endgroup}}
            {{distractor}}
            {{group}}
             char h;
            {{endgroup}}
            {{group}}
             h = "Hello";
            {{endgroup}}
            {{distractor}}
            {{group}}
             h = Hello;
            {{endgroup}}
            {{group}}
             std::cout << h;
            {{endgroup}}
            {{distractor}}
            {{group}}
             std::cout << "Hello";
            {{endgroup}}
            {{distractor}}
            {{group}}
             std::cout << "h";
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

.. admonition:: More to Explore

   - From cppreference.com

     - :io:`cout` and
       :lang:`escape sequences <escape>`


