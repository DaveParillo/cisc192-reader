Composition
-----------

As you should expect by now, once you define a new function, you can use
it as part of an expression, and you can build new functions using
existing functions. For example, what if someone gave you two points,
the center of the circle and a point on the perimeter, and asked for the
area of the circle?

Let’s say the center point is stored in the variables ``xc`` and ``yc``, and the
perimeter point is in ``xp`` and ``yp``. The first step is to find the radius of
the circle, which is the distance between the two points. Fortunately,
we have a function, ``distance``, that does that.

::

    double radius = distance (xc, yc, xp, yp);

The second step is to find the area of a circle with that radius, and
return it.

::

    double result = area (radius);
    return result;

Wrapping that all up in a function, we get:

::

    double fred (double xc, double yc, double xp, double yp) {
      double radius = distance (xc, yc, xp, yp);
      double result = area (radius);
      return result;
    }

The name of this function is ``fred``, which may seem odd. I will explain
why in the next section.

The temporary variables radius and area are useful for development and
debugging, but once the program is working we can make it more concise
by composing the function calls:

::

    double fred (double xc, double yc, double xp, double yp) {
      return area (distance (xc, yc, xp, yp));
    }


.. activecode:: fun_comp_AC_1
   :language: cpp
   :caption: Function Composition

   This program shows you how the distance and area functions are
   composed in the fred function to calculate the area of a circle
   if we only know the coordinates of the center, and one other point
   of the circle.
   ~~~~
   #include <cmath>
   #include <iostream>

   double distance (double x1, double y1, double x2, double y2) {
       double dx = x2 - x1;
       double dy = y2 - y1;
       double dsquared = dx * dx + dy * dy;
       double result = sqrt (dsquared);
       return result;
   }

   double area (double radius) {
       double area = 3.14 * (radius * radius);
       return area;
   }

   double fred (double xc, double yc, double xp, double yp) {
       return area (distance (xc, yc, xp, yp));
   }

   int main () {
       double circle_area = fred (1.0, 2.0, 4.0, 6.0);
       cout << circle_area << endl;
       return 0;
   }


.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: fun_comp_1
         :answer_a: the types and quantities of variables that make up the function
         :answer_b: the process of combining one or more functions into more complicated ones
         :answer_c: the process of creating a function using incremental development
         :answer_d: all of the above
         :correct: b
         :feedback_a: This would tell us what variables the function is composed of, but this is not what function composition means.
         :feedback_b: This is what we did inside of the fred function.
         :feedback_c: Incremental development is useful in function composition, but does not define it.
         :feedback_d: There is only one correct answer here!

         What is function composition?

   .. tab:: Q2

      .. mchoice:: fun_comp_2
         :answer_a: print_hello_name
         :answer_b: fluffy_cat
         :answer_c: eat_pizza
         :answer_d: all of the above
         :answer_e: none of the above
         :correct: d
         :feedback_a: This function name isn't much of a change from our original, and would be a good choice, but what about the other options?
         :feedback_b: Although unconventional, there is nothing wrong about this name, but what about eat_pizza?
         :feedback_c: Although unconventional, there is nothing wrong about this name, but what about fluffy_cat?
         :feedback_d: All of these function names are technically legal, but in general, it's good practice to name your functions something that describes what they do.
         :feedback_e: There's nothing wrong with any of these function names, although some of them are weird.

         It turns out you already have a function called ``printHelloName``
         so you must rename this one.  Which of the following could be the 
         new name for your function?

         ::

             void printHelloName (string name) {
               cout << "Hello " << name << "!" <<  endl;
             }

Function composition is not limited to a fixed number of calls.
Multiple calls can be made to the same function as well as to a number of
different functions.

.. activecode:: multi_comp_1
   :language: cpp
   :caption: Function Composition

   This program shows how mutliple calls are made to one function and it
   also shows that calling two or more different functions is valid.
   ~~~~
   #include <iostream>

   int increase_population (int population) {
       return population*2;
   }

   void print_population (int population) {
       std::cout << "The current population is " 
                 << population << std::endl;
   }

   void grow_4(int start_size){
       int new_size = increase_population(start_size);
       // increase population again by doubling new_size
       new_size = increase_population(new_size);
       print_population(new_size);
   }

   int main () {
       int begin_population = 3;
       grow_4(begin_population);
   }


