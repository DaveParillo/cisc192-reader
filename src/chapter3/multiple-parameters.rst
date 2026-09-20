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

.. caution::
   It is unnecessary and illegal to include the type when you pass 
   variables as arguments! The type is only needed for declaration.
   
In this case, the compiler is getting mixed information and won't know
what to do. What is meant by ``print_time(int hour, int minute);``

- Is this a function call with the types included?
  The compiler does not need types included, it knows the
  types by looking at their declarations. 
- Is this a malformed declaration -- missing the return type?

Because the compiler can't tell what is intended, it stops
and reports an error instead.

The correct syntax is ``print_time (hour, minute);``.


This program shows how the dollar_amount and cent_amount arguments
are passed into the print_price function.

.. tb-code:: cpp
   :name: multiple_params_AC_1
   :caption: Understanding Multiple Parameters
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>

   void print_price (int dollars, int cents) {
       std::cout << "The price is $" 
                 << dollars << '.'
                 << cents << "\n.";
   }

   int main () {
       int dollar_amount = 2;
       int cent_amount = 92;
       print_price (dollar_amount, cent_amount);
       return 0;
   }


.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: multiple_params_1

         h of the following is a correct function declaration?

         ``total_cost (double cost, tax, discount);``

         - [ ] ``total_cost`` needs a return type, and each parameter needs a data type.

         ``total_cost (double cost, double tax) {``

         - [x] ``total_cost`` needs a return type.

         ``void total_cost (double cost, double tax, double discount);``

         +   Correct!

         ``void total_cost (double cost, tax);``

         - [ ] This declaration needs types for each parameter.


   .. tb-tab:: Q2

      .. tb-choice::
         :name: multiple_params_2

         h of the following is a legal function call of the function below?



         void multiply_two (int num, string name) {
           int total = num * 2;
           cout << "Hi " << name << ", your total is " << total << "!" << endl;
         }

         int main() {
           int x = 2;
           string phil = "Phil";
         }

         ``multiply_two (int x, string phil);``

         - [x] Data types are not needed when calling a function.

         ``multiply_two (x, phil);``

         +   Correct!

         ``void multiply_two (int num, string name) {``

         - [ ] This is the function definition.

         ``void multiply_two (int x, string phil);``

         - [ ] Data types are not needed when calling a function.

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Function definitions <definition>` and
       :lang:`declarations`
     - :lang:`Functions <functions>`

