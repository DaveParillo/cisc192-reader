Floating-point
--------------

In the last chapter we had some problems dealing with numbers that were
not integers. We worked around the problem by measuring percentages
instead of fractions, but a more general solution is to use
**floating-point** numbers, which can represent fractions as well as
integers. In C++, there are two floating-point types, called ``float`` and
``double``. In this book we will use doubles exclusively.

You can create floating-point variables and assign values to them using
the same syntax we used for the other types. For example:

::

    double pi;
    pi = 3.14159;

It is also legal to declare a variable and assign a value to it at the
same time:

::

    int x = 1;
    string empty = "";
    double pi = 3.14159;

.. index::
   single: initialize
   single: initialization
   single: initialization statement

In fact, this syntax is quite common. A combined declaration and
assignment is sometimes called an **initialization**.

.. caution::
   It is important that you **initialize** any and all variables that you
   declare.  Failure to do so will generate an error (if you're lucky), or
   C++ will initialize the variable to leftover memory, which could lead to
   undefined behavior.

Although floating-point numbers are useful, they are often a source of
confusion because there seems to be an overlap between integers and
floating-point numbers. For example, if you have the value 1, is that an
integer, a floating-point number, or both?

Strictly speaking, C++ distinguishes the integer value 1 from the
floating-point value 1.0, even though they seem to be the same number.
They belong to different types, and strictly speaking, you are not
allowed to make assignments between types. For example, the following is
illegal

::

    int x = 1.1;

because the variable on the left is an ``int`` and the value on the right is
a ``double``. But it is easy to forget this rule, especially because there
are places where C++ automatically converts from one type to another.
For example,

::

    double y = 1;

should technically not be legal, but C++ allows it by converting the ``int``
to a ``double`` automatically. This leniency is convenient, but it can cause
problems; for example:

::

    double y = 1 / 3;

You might expect the variable y to be given the value 0.333333, which is
a legal floating-point value, but in fact it will get the value 0.0. The
reason is that the expression on the right appears to be the ratio of
two integers, so C++ does *integer* division, which yields the integer
value 0. Converted to floating-point, the result is 0.0.

.. caution::
   It's crucial that you understand that when given two integers, C++ 
   performs integer division!  This is a common logic error that can be 
   hard to catch, since your program will compile without problems.

One way to solve this problem (once you figure out what it is) is to
make the right-hand side a floating-point expression:

::

    double y = 1.0 / 3.0;

This sets y to 0.333333, as expected.

All the operations we have seen—addition, subtraction, multiplication,
and division—work on floating-point values, although you might be
interested to know that the underlying mechanism is completely
different. In fact, most processors have special hardware just for
performing floating-point operations.

.. tabbed:: tab_check

   .. tab:: Q1

      .. fillintheblank:: floating_point_1

         A(n) |blank| statment consists of a declaration statement and an 
         assignment statement, which are combined.
          
         - :[Ii][Nn][Ii][Tt][Ii][Aa][Ll][Ii][Zz][Aa][Tt][Ii][Oo][Nn]: Correct!
           :.*: Try again!


   .. tab:: Q2

      .. fillintheblank:: floating_point_2

         It's your birthday and your cake can serve 12.  You want to slice it
         evenly so that you and each of your 4 friends receive an equal amount.  
         One of your friends is on a diet and, and wants to know the serving size 
         of her slice.  You write the following code in C++ to answer her question.

         ::

             int servings = 12;
             int people = 5;

             double servingSize = servings / people;

         Based on the value of ``servingSize``, you tell your friend that each
         slice is |blank| servings.  This is |blank| (more, less, the same) than/as
         the actual serving size of her slice.
          
         - :2: Correct! C++ performs integer division.
           :.*: servingSize and people are integer variables!
         - :[Ll][Ee][Ss][Ss]: Correct! You just unintentionally messed up your friend's diet.
           :[Mm][Oo][Rr][Ee]: Remember, integer division rounds down to the nearest integer.
           :.*: Remember, C++ performs integer division.


   .. tab:: Q3

      .. mchoice:: floating_point_3
         :answer_a: e
         :answer_b: 3
         :answer_c: 2
         :answer_d: 3.0
         :answer_e: 2.71828
         :correct: c
         :feedback_a: This is the name of a variable. Only the value of a variable will print with cout.
         :feedback_b: Converting to an int always rounds down.
         :feedback_c: When we converted e to an int, e was rounded down to 2. When we converted e_nt to e_double, the decimal places from e were lost, and the value of e_double is 2.
         :feedback_d: Converting to an int always rounds down.
         :feedback_e: When we converted e to an int, e was rounded down to 2. When we converted e_nt to e_double, the decimal places from e were lost.

         In the lab, we measured a temperature of 7.99999999 degrees C, using
         an extremely precise measuring device.  Now we are writing a program
         to perform some calculations with our data.  Consider the following C++
         code.

         ::

             double e = 2.71828;
             int e_int = e;
             double e_double = eInt;
             cout << e_double;

         What is the value of ``e_double`` that is printed to the terminal?

   .. tab:: Q4

      Identifying whether an operation carries out integer division or floating point division
      can get tricky when we have a mix of integers and doubles in our expression.
      The thing to remeber is if either the divisor or the dividend is a double
      then the program will carry out floating point division.

      .. activecode:: floating_point_a1
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:

         Run the code below to see what type of division occurs each time.
         ~~~~
         #include <iostream>
         using namespace std;

         int main () {
             double value = 5.0/2; //(a)
             cout<<"current value (a) is "<<value<<endl;

             value = 5/2.0; //(b)
             cout<<"current value (b) is "<<value<<endl;

             value = 5/2; //(c)
             cout<<"current value (c) is "<<value<<endl;

             value = 5.0/2.0; //(d)
             cout<<"current value (d) is "<<value<<endl;
             return 0;
         }
