Functions with Multiple Parameters
----------------------------------

The syntax for declaring and invoking functions with multiple parameters
is a common source of errors. First, remember that you have to declare
the type of every parameter. For example

::

    void print_time (int hour, int minute) {
      std::cout << hour << ':' << minute;
    }

It might be tempting to write ``(int hour, minute)``, but that format is
only legal for variable declarations, not for parameters.

Another common source of confusion is that you do not have to declare
the types of arguments when calling a function.
The following is wrong!

::

    int hour = 11;
    int minute = 59;
    print_time (int hour, int minute);   // WRONG!

In this case, the compiler can tell the type of hour and minute by
looking at their declarations. 

.. caution::
   It is unnecessary and illegal to include the type when you pass 
   variables as arguments! The type is only needed for declaration.
   
The correct syntax is ``print_time (hour, minute)``.


.. activecode:: multiple_params_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Understanding Multiple Parameters

   This program shows how the dollar_amount and cent_amount arguments
   are passed into the print_price function.
   ~~~~
   #include <iostream>

   void print_price (int dollars, int cents) {
       std::cout << "Price is " 
                 << dollars << " dollars and " 
                 << cents << " cents.\n";
   }

   int main () {
       int dollar_amount = 2;
       int cent_amount = 92;
       print_price (dollar_amount, cent_amount);
       return 0;
   }


.. tabbed:: tab_check

   .. tab:: Q1

      .. mchoice::  multiple_params_1

          Which of the following is a correct function header (first line of 
          a function definition)?

          -   ``totalcost (double cost, tax, discount)``

              -   ``totalcost`` needs a return type, and each parameter needs a data type.

          -   ``totalCost (double cost, double tax) {``

              -   ``totalcost`` needs a return type.

          -   ``void totalCost (double cost, double tax, double discount) {``

              +   Correct!

          -   ``void totalCost (double cost, double tax)``

              -   This function header is missing a ``{``, which is needed to begin defining the function.


   .. tab:: Q2

      .. mchoice::  multiple_params_2

          Which of the following is a legal function call of the function below?

          ::

              void multiply_two (int num, string name) {
                int total = num * 2;
                cout << "Hi " << name << ", your total is " << total << "!" << endl;
              }

              int main() {
                int x = 2;
                string phil = "Phil";
              }

          -   ``multiply_two (int x, string phil);``

              -   Data types are not needed when calling a function.

          -   ``multiply_two (x, phil);``

              +   Correct!

          -   ``void multiply_two (int num, string name) {``

              -   This is the function definition.

          -   ``void multiply_two (int x, string phil);``

              -   Data types are not needed when calling a function.
