.. _variables-types-compound-expressions:

Compound Expressions
--------------------

.. index::
   single: composition
   single: compose

So far we have looked at the elements of a programming
language—variables, expressions, and statements—in isolation, without
talking about how to combine them.

One of the most useful features of programming languages is their
ability to take small building blocks and **compose** them. For example,
we know how to multiply integers and we know how to output values; it
turns out we can do both at the same time:


This program performs multiplication and prints the result simultaneously.

.. tb-code:: cpp
   :name: composition_AC_1
   :caption: Multiplication Output

   #include <iostream>

   int main () {
       std::cout << 17 * 3;
   }


Actually, I shouldn't say "at the same time", since in reality the
multiplication has to happen before the output, but the point is that
any expression, involving numbers, characters, and variables, can be
used inside an output statement. We've already seen one example:


This program performs a calculation involving variables and
prints the result at the same time.

.. tb-code:: cpp
   :name: composition_AC_2
   :caption: Variable Output

   #include <iostream>

   int main () {
       int hour = 7;
       int minute = 1;
       std::cout << hour * 60 + minute << '\n';
   }


You can also put arbitrary expressions on the right-hand side of an
assignment statement:


This program performs a calculation involving variables and simultaneously
assigns the result as the variable initial value.

.. tb-code:: cpp
   :name: composition_AC_3
   :caption: Performing Calculations Before Assignment

   #include <iostream>

   int main () {
       int minute = 3;
       int percentage = (minute * 100) / 60;
       std::cout << percentage;
   }


This ability may not seem so impressive now, but we will see other
examples where composition makes it possible to express complex
computations neatly and concisely.

.. caution::
   There are limits on where you can use certain expressions; most
   notably, the left-hand side of an assignment statement has to be a
   *variable* name, not an expression. 

That’s because the left side indicates the storage location where the 
result will go. Expressions do not represent storage locations, only 
values. So the following is illegal: ``minute + 1 = hour;``.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: compos_1

         What must be changed in order for this code block to work?

         .. code-block:: 
             :linenos:

             int main () {
               int dogs = 3;
               int cats = 6;
               int pets;
               dogs + cats = pets;
               cout << "I have " << pets << " pets!";
               return 0;
             }


         - [x] Change line 5 to pets = dogs + cats;

           Assignment statements operate such that the evaluated expression on the right is assigned to the variable on the left.
         - [ ] Change line 5 to int pets = dogs + cats;

           pets has already been declared as an int.
         - [ ] Change line 5 to pets == dogs + cats;

           The == operator checks if the left side EQUALS the right side.  It is not the correct operator here.
         - [ ] Change line 5 to int pets == dogs + cats;

           pets has already been declared as an int.  Also, the == operator is not the proper choice here.
         - [ ] No change, the code runs fine as is.

           Assignment statements assign the value on the right to the variable on the left.

   .. tb-tab:: Q2

      .. tb-blank::
         :name: compos_2

         The left-hand side of an assignment statement has to be a {{blank}} name, not an expression.

         .. tb-answer::
            :match: variable
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q3

      .. tb-blank::
         :name: compos_3

         In programming, another word for **combine** is {{blank}}.

         .. tb-answer::
            :match: compose
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q4

      Finish the code below so that the velocity is calculated and 
      returned on the same line.  

      Hint: the current velocity results from 
      1) the initial velocity and 2) the acceleration over a window of time.

      .. tb-code:: cpp
         :name: compos_4-support
         :hidden:


         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>

         template <class t, class compare = std::equal_to<t>>
         void check (const std::string& name, const t& actual, 
                     const t& expected, const compare& op = compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
           if(op(actual, expected)) {
             std::cout << " OK      \n";
             return;
           }
           std::cout << " Try again!\n";
           std::cout << "\treceived [" << actual
                     << "], but expected [" << expected << "]\n";
           exit(1);
         }
         int main() {
             check("velocity(5,3,4)", velocity(5,3,4),  17);
             check("velocity(3,5,8)", velocity(3,5,8),  43);
             check("velocity(8,13,21)", velocity(8,13,21),  281);
         }



      .. tb-code:: cpp
         :name: compos_4
         :caption: Example compos_4
         :run-after: compos_4-support

         int velocity(int initial_velocity, int acceleration, int time) {
             // Modify the return statement to pass the tests
             return ;
         }

   .. tb-tab:: Q5

      Finish the code below so that the volume of a cylinder with radius ``r`` and height ``h`` is calculated and returned on the same line. 

      .. tb-code:: cpp
         :name: compos_5-support
         :hidden:


         #include <cmath>
         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>

         template <class t, class compare = std::equal_to<t>>
         void check (const std::string& name, const t& actual, 
                     const t& expected, const compare& op = compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
           if(op(actual, expected)) {
             std::cout << " OK      \n";
             return;
           }
           std::cout << " Try again!\n";
           std::cout << "\treceived [" << actual
                     << "], but expected [" << expected << "]\n";
           exit(1);
         }
         bool close_to(double x, double y)
         {
             return std::abs(x-y) < 0.001;
         }
         int main() {
             check("volume(3,4)", volume(3, 4),  113.097, close_to);
             check("volume(2,6)", volume(2, 6),  75.3982, close_to);
             check("volume(5,4)", volume(5, 4),  314.159, close_to);
         }




      .. tb-code:: cpp
         :name: compos_5
         :caption: Example compos_5
         :run-after: compos_5-support

         double volume(int r, int h) {
             // Modify the return statement to pass the tests
             return ;
         }

-----

.. admonition:: More to Explore

   - From cppreference.com

     - C++ :lang:`expressions` and :lang:`function declarations <function>`

