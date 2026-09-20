Accessing instance variables
----------------------------

You can read the values of an instance variable using the same syntax we
used to write them:

::

       int x = blank.x;

The expression ``blank.x`` means “go to the object named ``blank`` and
get the value of ``x``.” In this case we assign that value to a local
variable named ``x``. Notice that there is no conflict between the local
variable named ``x`` and the instance variable named ``x``. The purpose of the
member access operator is to identify *which* variable you are referring to
unambiguously.

You can use the member access operator as part of any C++ expression, 
so the following are legal.

::

   cout << blank.x << ", " << blank.y << '\n';
   double distance = sqrt(blank.x * blank.x + blank.y * blank.y);

In the active code below, we access the instance variables of ``point`` object 
``blank`` and output their values.
Next, we display the distance from the origin.

.. tb-code:: cpp
   :name: accessing_instance_variables_AC_1
   :caption: Example accessing_instance_variables_AC_1
   :compileargs: ['-Wall', '-std=c++20']

   #include <cmath>
   #include <iostream>

   struct point {
       double x;
       double y;
   };

   int main() {
      point blank;
      blank.x = 3.0;
      blank.y = 4.0;
      std::cout << blank.x << ", " << blank.y << '\n';
      double distance = std::sqrt(blank.x * blank.x + blank.y * blank.y);
      std::cout << distance << '\n';
   }

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: accessing_instance_variables_1

         In ``string x = thing.cube;``, what is the object and what is the instance variable we are reading the value of?

         - [ ] ``string`` is the instance variable, ``cube`` is the object

           - ``string`` is a data type.

         - [ ] ``x`` is the instance variable, ``thing`` is the object

           - ``x`` is the local variable.

         - [ ] ``thing`` is the instance variable, ``cube`` is the object

           - Consider the placement of ``thing`` -- it is before the ``.``


         - [x] ``cube`` is the instance variable, ``thing`` is the object

           + Yes, we access the instance variable ``cube`` of the object ``thing`` using the dot operator.

         - [ ] ``cube`` is the instance variable, ``string`` is the object

           - ``string`` is a data type.


   .. tb-tab:: Q2

      .. tb-choice::
         :name: accessing_instance_variables_2

         What will print?

         .. code-block:: cpp

            struct blue {
              double x, y;
            };

            int main() {
              blue blank;
              blank.x = 7.0;
              blank.y = 2.0;
              cout << blank.y << blank.x;
              double distance = blank.x * blank.x + blank.y * blank.y;
              cout << distance << '\n';
            }


         - [ ] ``2.0 7.0 53``

           - Spaces need to be printed out like any other output.

         - [x] ``2753``

           + There are no spaces in the correct output.

         - [ ] ``7253``

           - The order in which the variables are printed out do not need to match the order in which they are declared.

         - [ ] ``7.02.053``

           - The order in which the variables are printed out do not need to match the order in which they are declared.


   .. tb-tab:: Q3

      .. tb-choice::
         :name: accessing_instance_variables_3

         You want to go to the object named ``circle`` and get the integer value of ``y``, then assign it to the local variable ``x``. How would you do that?

         - [ ] ``int y = circle.x();``

           -  No parentheses are needed.

         - [ ] ``int circle = x.y;``

           - You should be assigning to the local variable ``x``.

         - [ ] ``int y = circle.x;``

           - You should be assigning to the local variable ``x``.

         - [x] ``int x = circle.y;``

           + This is the correct way to assign the value of ``y`` to ``x``.

