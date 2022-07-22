Nested Conditionals
-------------------

.. index::
   single: nesting
   single: nested conditionals

In addition to chaining, you can also nest one conditional within
another. We could have written the previous example as:

.. activecode:: nested_conditionals_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Classifying an Integer

   This program classifies a number (x) as positive, negative, or zero,
   just like the program on the previous page.  However, this time, we are
   using nested conditionals.
   ~~~~
   #include <iostream>
   using std::cout;

   void classify (int value) {
       if (value == 0) {
           cout << "value is zero\n";
       } else {
           if (value > 0) {
               cout << "value is positive\n";
           } else {
               cout << "value is negative\n";
           }
      }
   }

   int main () {
       int x = 9;
       classify (x);
       x = x * -1;
       classify (x);
   }

There is now an outer conditional that contains two branches. The first
branch contains a simple output statement, but the second branch
contains another if statement, which has two branches of its own.
Fortunately, those two branches are both output statements, although
they could have been conditional statements as well.

.. note::
   There is not a limit to the number of times you can nest a conditional.
   However, you should try to limit this number, as it will reduce the
   complexity of your program structure.

   Too many nested conditionals is considered a bad practice.

Notice again that indentation helps make the structure apparent, but
nevertheless, nested conditionals get difficult to read very quickly. In
general, it is a good idea to avoid them when you can.

On the other hand, this kind of **nested structure** is common, so
it is important to be able read nested code, regardless of whether it
is a best practice or not.


.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: nested_conditionals_1
         :answer_a: Hey!
         :answer_b: Hi!
         :answer_c: Hello!
         :answer_d: Nothing will print.
         :correct: a
         :feedback_a: Correct!
         :feedback_b: Remember that the program would only enter the "else" if x was not equal to 0.
         :feedback_c: Remember that the program would only enter the "else" if x was not equal to 0.
         :feedback_d: Only one of the condtionals will execute, but something will print, regardless of which one it is.

         What will print?

         ::

             #include <iostream>

             int main () {
               int x = 0;
               if (x == 0) {
                 std::cout << "Hey!\n";
               } else {
                 if (x > 0) {
                   std::cout << "Hi!\n";
                 } else {
                   std::cout << "Hello!\n";
                 }
               }
             }

   .. tab:: Q2

      .. mchoice:: nested_conditionals_2
         :answer_a: Hey!
         :answer_b: Hi!
         :answer_c: Hello!
         :answer_d: Nothing will print.
         :correct: c
         :feedback_a: Remember that the program would only enter the first "if" if x was equal to 0.
         :feedback_b: Remember that the program would only enter the nested "if" if x was greater than 0.
         :feedback_c: Correct!
         :feedback_d: Only one of the condtionals will execute, but something will print, regardless of which one it is.

         What will print?

         ::

             #include <iostream>

             int main () {
               int x = -4;
               if (x == 0) {
                 std::cout << "Hey!\n";
               } else {
                 if (x > 0) {
                   std::cout << "Hi!\n";
                 } else {
                   std::cout << "Hello!\n";
                 }
               }
             }

   .. tab:: Q3

      .. mchoice:: nested_conditionals_3
         :answer_a: Back Left!
         :answer_b: Back Right!
         :answer_c: Front Left!
         :answer_d: Front Right!
         :answer_e: Error!
         :correct: b
         :feedback_a: Remember that the > opearator is not inclusive.
         :feedback_b: z > m is true, and m > m is false, so a student with these initials would be seated in the back right.
         :feedback_c: z > m is true because z comes after m.  Also, the > opearator is not inclusive.
         :feedback_d: z > m is true because z comes after m.
         :feedback_e: Character comparisons are legal, and useful in this case!

         Your school uses a system to arrange students in a large stadium using 
         their initials.  Look at the function definition below.  Where would a
         student with the initials "MZ" be seated?

         ::

             string seating_arrangement(char first, char last) {
               constexpr char center = 'm';
               if (last > center) {
                 if (first > center) {
                   return "Back Left!";
                 } else {
                   return "Back Right!";
                 }
               } else {
                 if (first > .) {
                   return "Front Left!";
                 } else {
                   return "Front Right!";
                 }
               }
             }




-----

.. admonition:: More to Explore

   - :lang:`if` from cppreference.com
   - `The 'Arrow anti-pattern' <http://wiki.c2.com/?ArrowAntiPattern>`__ from
     the Portland Pattern Repository (the very first wiki!)
   - `Flattening arrow code <https://blog.codinghorror.com/flattening-arrow-code/>`__
     from Jeff Atwood's blog.

