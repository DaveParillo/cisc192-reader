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

   cout << blank.x << ", " << blank.y << endl;
   double distance = sqrt(blank.x * blank.x + blank.y * blank.y);

.. activecode:: accessing_instance_variables_AC_1
   :language: cpp

   In the active code below, we access the instance variables of ``point`` object 
   ``blank`` and output their values.
   Next, we display the distance from the origin.
   ~~~~
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
      std::cout << blank.x << ", " << blank.y << std::endl;
      double distance = std::sqrt(blank.x * blank.x + blank.y * blank.y);
      std::cout << distance << std::endl;
   }

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: accessing_instance_variables_1
         :practice: T
         :answer_a: ``string`` is the instance variable, ``cube`` is the object
         :answer_b: ``x`` is the instance variable, ``thing`` is the object
         :answer_c: ``thing`` is the instance variable, ``cube`` is the object
         :answer_d: ``cube`` is the instance variable, ``thing`` is the object
         :correct: d
         :feedback_a: ``string`` is a data type.
         :feedback_b: ``x`` is the local variable.
         :feedback_c: Consider the placement of ``thing`` -- it is before the ``.``
         :feedback_d: Yes, we access the instance variable ``cube`` of the object ``thing`` using the dot operator.

         In ``string x = thing.cube;``, what is the object and what is the instance variable we are reading the value of?


   .. tab:: Q2

      .. mchoice:: accessing_instance_variables_2
         :practice: T
         :answer_a: 2.0 7.0 53
         :answer_b: 2.07.053
         :answer_c: 7.0, 2.0 53
         :answer_d: 7.02.053
         :correct: b
         :feedback_a: Spaces need to be printed out like any other output.
         :feedback_b: There are no spaces in the correct output.
         :feedback_c: The order in which the variables are printed out do not need to match the order in which they are declared.
         :feedback_d: The order in which the variables are printed out do not need to match the order in which they are declared.

         What will print?

         .. code-block:: cpp

            struct blue {
              double x;
              double y;
            };

            int main() {
              blue blank;
              blank.x = 7.0;
              blank.y = 2.0;
              cout << blank.y << blank.x;
              double distance = blank.x * blank.x + blank.y * blank.y;
              cout << distance << endl;
            }

   .. tab:: Q3

      .. mchoice:: accessing_instance_variables_3
         :practice: T
         :answer_a: int y = circle.x();
         :answer_b: int circle = x.y;
         :answer_c: int y = circle.x;
         :answer_d: int x = circle.y;
         :correct: d
         :feedback_a: No parentheses are needed.
         :feedback_b: You should be assigning to the local variable x.
         :feedback_c: You should be assigning to the local variable x.
         :feedback_d: This is the correct way to assign the value of y to x.

         You want to go to the object named ``circle`` and get the value of ``y``, then assign it to the local variable ``x``. How would you do that?

