Outputting Variables
--------------------

You can output the value of a variable using the same commands we used
to output simple values. After observing the output, try inputting your own time!


.. activecode:: output_vars_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Time Output
   
   This program outputs the current time, according to the values you
   provide for hour and minute.
   ~~~~
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


.. activecode:: output_vars_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Condensing The Code

   This program does the same thing as the previous, but the print
   statements have been condensed to one line.  This is better style.
   ~~~~
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

.. tabbed:: tab_check

   .. tab:: Q1

      .. mchoice:: output_vars_1
         :practice: T
         :answer_a: a
         :answer_b: b
         :answer_c: z
         :answer_d: 8
         :answer_e: Nothing! There will be a compile error!
         :correct: a
         :feedback_a: The string, not the variable, a will be printed.
         :feedback_b: b will not be printed.
         :feedback_c: The cout statement prints a, not the value of the variable a.
         :feedback_d: z is the value of a and will not be printed
         :feedback_e: There is no type mismatch, so there will not be a compile error.

         What prints when the following code is run?

         ::

             int main () {
               char a;
               char b;
               a = 'z';
               b = '8';
               cout << "a";
             }


   .. tab:: Q2

      .. mchoice:: output_vars_2
         :practice: T
         :answer_a: a
         :answer_b: b
         :answer_c: z
         :answer_d: 8
         :answer_e: Nothing! There will be a compile error!
         :correct: d
         :feedback_a: The string a will not be printed.
         :feedback_b: The string b will not be printed.
         :feedback_c: z is the value of a and will not be printed.
         :feedback_d: 8 is the value of b will be printed!
         :feedback_e: There is no type mismatch, so there will not be a compile error.

         Now, what prints?

         ::

             int main () {
               char a;
               char b;
               a = 'z';
               b = '8';
               cout << b;
             }


   .. tab:: Q3

      .. mchoice:: output_vars_3
         :practice: T
         :answer_a: x
         :answer_b: y
         :answer_c: 3
         :answer_d: e
         :answer_e: Nothing! There will be a compile error!
         :correct: e
         :feedback_a: Take a look at the code again.
         :feedback_b: Take a look at the code again.
         :feedback_c: Take a look at the code again.
         :feedback_d: Take a look at the code again.
         :feedback_e: There is a type mismatch, so there will be a compile error!

         And now, what prints?

         ::

             int main () {
               int x;
               char y;
               x = '3';
               y = 'e';
               cout << 'y';
             }


   .. tab:: Q4

      .. dragndrop:: output_vars_4
         :feedback: Try again!
         :match_1:  x = 2|||int
         :match_2: y = "2"|||string
         :match_3: z = '2'|||char

         Match the variable initialization to its correct type.


   .. tab:: Q5

      .. parsonsprob:: output_vars_5
         :numbered: left
         :adaptive:
         
         Construct a main function that assigns "Hello" to the variable h, then prints out h's value.
         -----
         #include <iostream>
         =====
         #include <string>
         =====
         int main () {
         =====
          std::string h;
         =====
          char h; #paired
         =====
          h = "Hello";
         =====
          h = Hello; #paired
         =====
          std::cout << h;
         =====
          std::cout << "Hello"; #paired
         =====
          std::cout << "h"; #paired
         =====
         }

.. admonition:: More to Explore

   - From cppreference.com

     - :io:`cout` and
       :lang:`escape sequences <escape>`


