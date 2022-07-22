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


.. activecode:: composition_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Multiplication Output

   This program performs multiplication and prints the result simultaneously.
   ~~~~
   #include <iostream>

   int main () {
       std::cout << 17 * 3;
   }


Actually, I shouldn't say "at the same time", since in reality the
multiplication has to happen before the output, but the point is that
any expression, involving numbers, characters, and variables, can be
used inside an output statement. We've already seen one example:


.. activecode:: composition_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Variable Output

   This program performs a calculation involving variables and
   prints the result at the same time.
   ~~~~
   #include <iostream>

   int main () {
       int hour = 7;
       int minute = 1;
       std::cout << hour * 60 + minute << '\n';
   }


You can also put arbitrary expressions on the right-hand side of an
assignment statement:


.. activecode:: composition_AC_3
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Performing Calculations Before Assignment

   This program performs a calculation involving variables and simultaneously
   assigns the result as the variable initial value.
   ~~~~
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

.. tabbed:: tab_check

   .. tab:: Q1

      .. mchoice:: compos_1
         :practice: T
         :answer_a: Change line 5 to pets = dogs + cats;
         :answer_b: Change line 5 to int pets = dogs + cats;
         :answer_c: Change line 5 to pets == dogs + cats;
         :answer_d: Change line 5 to int pets == dogs + cats;
         :answer_e: No change, the code runs fine as is.
         :correct: a
         :feedback_a: Assignment statements operate such that the evaluated expression on the right is assigned to the variable on the left.
         :feedback_b: pets has already been declared as an int.
         :feedback_c: The == operator checks if the left side EQUALS the right side.  It is not the correct operator here.
         :feedback_d: pets has already been declared as an int.  Also, the == operator is not the proper choice here.
         :feedback_e: Assignment statements assign the value on the right to the variable on the left.

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


   .. tab:: Q2

      .. fillintheblank:: compos_2

         The left-hand side of an assignment statement has to be a |blank| name, not an expression.

         - :[Vv][Aa][Rr][Ii][Aa][Bb][Ll][Ee]: Correct!
           :.*: Try again!


   .. tab:: Q3

      .. fillintheblank:: compos_3

         In programming, another word for **combine** is |blank|.

         - :[Cc][Oo][Mm][Pp][Oo][Ss][Ee]: Correct!
           :.*: Try again!


   .. tab:: Q4

      .. activecode:: compos_4
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:

         Finish the code below so that the velocity is calculated and 
         returned on the same line.  
         
         Hint: the current velocity results from 
         1) the initial velocity and 2) the acceleration over a window of time.
         ~~~~
         int velocity(int initial_velocity, int acceleration, int time) {
             // Modify the return statement to pass the tests
             return ;
         }
         ====

         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>

         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, const T& actual, 
                     const T& expected, const Compare& op = Compare())
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


   .. tab:: Q5

      .. activecode:: compos_5
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:

         Finish the code below so that the volume of a cylinder with radius ``r`` and height ``h`` is calculated and returned on the same line. 
         ~~~~
         double volume(int r, int h) {
             // Modify the return statement to pass the tests
             return ;
         }

         ====

         #include <cmath>
         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>

         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, const T& actual, 
                     const T& expected, const Compare& op = Compare())
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



-----

.. admonition:: More to Explore

   - From cppreference.com

     - C++ :lang:`expressions` and :lang:`function declarations <function>`
