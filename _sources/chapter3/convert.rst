Converting from ``double`` to ``int``
----------------------------------------
As I mentioned, C++ converts ``int`` to ``double`` automatically if necessary,
because no information is lost in the translation. 
This is called a **widening conversion**.

On the other hand,
going from a ``double`` to an ``int`` requires truncation. C++ doesn't perform
this operation automatically, in order to make sure that you, as the
programmer, are aware of the loss of the fractional part of the number.
This is called a **narrowing conversion**.
does this mean that once you have an ``int``, it can never be assigned
to a ``double``?

Of course not.

You can explicitly perform these kinds of assignments by using a *typecast*.

.. index::
   single: typecast

The simplest way to convert a floating-point value to an integer is to
use a **typecast**. Typecasting is so called because it allows you to
take a value that belongs to one type and “cast” it into another type
(in the sense of molding or reforming, not throwing).

The syntax for typecasting is like the syntax for a function call. For
example:

::

    double pi = 3.14159;
    int x = int (pi);

The int function returns an integer, so x gets the value 3. Converting
to an integer always truncates, even if the fraction part is
0.99999999.

For every built-in type in C++, there is a corresponding function that casts
its argument to the appropriate type.

.. tabbed:: tab_check

   .. tab:: Q1

      .. mchoice:: double_to_int_1
         :answer_a: temp
         :answer_b: 8
         :answer_c: 7
         :answer_d: 8.0
         :answer_e: 7.0
         :correct: c
         :feedback_a: This is the name of a variable. Only the value of a variable will print with cout.
         :feedback_b: Remember that converting to an integer always truncates.
         :feedback_c: Correct!
         :feedback_d: This is not an integer data type, and it's not the right number.
         :feedback_e: This is not an integer data type.

         In the lab, we measured a temperature of 7.99999999 degrees C, using
         an extremely precise measuring device.  Now we are writing a program
         to perform some calculations with our data.  Consider the following C++
         code.

         ::

             int main () {
               double temp = 7.99999999;
               int approx_temp = int (temp);
               cout << approx_temp;
             }

         What is the value of ``approx_temp``?


   .. tab:: Q2

      .. mchoice:: double_to_int_2

          Your final grade consists of your average performance on exam 1 and exam 2.  
          Your professor is using C++ to grade the exams and allows you to choose which
          method you'd like your exam to be graded.

          ::

                double exam1 = 88.8;
                double exam2 = 72.7;
                double exam2 = 97.9;

          **Method 1:**

          ::

                double final = (int(exam1) + int(exam2) + int(exam3)) / 3;

          **Method 2:**

          ::

                int final = int((exam1 + exam2 + exam3) / 3);

          Which method would you choose and why?

          -   **Method 1:** ``final`` is a ``double``, meaning my final grade will
              have more digits past the decimal, and will be higher than the ``int``
              in Method 2.

              -   Although ``final`` is a ``double``, it doesn't have any digits past
                  the decimal due to the integer division.

          -   **Method 1:** the rounding happens at the beginning, so all three of my
              test scores will be rounded to the nearest ``int``, which in my case, will
              round all of them up.

              -   Converting to an ``int`` always rounds *down*, even if your ``double`` is very 
                  close to the next integer.

          -   **Method 2:** ``final`` is an ``int``, so it gets rounded up.

              -   Converting to an ``int`` always rounds *down*, even if your ``double`` is very 
                  close to the next integer.

          -   **Method 2:** the rounding happens at the very end, so my grade will be higher!

              +   Always save your rounding until the end!
