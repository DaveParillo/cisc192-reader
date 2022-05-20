Composition
-----------

.. index::
   single: composition

Just as with mathematical functions, C++ functions can be **composed**,
meaning that you use one expression as part of another. For example, you
can use expressions as an argument to a function:

::

    double x = cos (angle + pi / 2);

This statement takes the value of pi, divides it by two and adds the
result to the value of angle. The sum is then passed as an argument to
the ``cos`` function.

You can also take the result of one function and pass it as an argument
to another:


.. activecode:: function_comp_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Composition of Math Functions

   This program finds the log base e of 10 and raises e to that power.  The
   result of this computation is assigned to x.
   ~~~~
   #include <cmath>
   #include <iostream>

   int main () {
       double x = exp (log (10.0));
       std::cout << x;
   }


.. tabbed:: tab_check

   .. tab:: Q1

      .. mchoice:: function_comp_1

          Which of these statements has proper syntax?

          -   ``double x = log6 (12);``

              -   ``log6`` is not a built in cmath function, but you could write an implementation for it if you wanted!

          -   ``double val = abs (tan (1.57));``

              +   This correctly uses cmath functions!

          -   ``double num = exp (cosine (0.86667));``

              -   ``cosine`` is not a built in cmath function, but ``cos`` is!

          -   ``double y = exp (cos (1.047)) + exp (tan (2.094))``

              -   This would be correct if it ended in a semi-colon.

   .. tab:: Q2

      .. mchoice:: function_comp_2

          Which of these statements returns the y-component of the unit
          vector at 330 degrees?

          -   ``y = cos(330);``

              -   You must always convert to radians before using sinusoidal functions.

          -   ``y = cos(330 * 2 * pi / 360);``

              -   ``cos`` will return the x-component.

          -   ``y = sin(330);``

              -   You must always convert to radians before using sinusoidal functions.

          -   ``y = sin(330 * 2 * pi / 360);``

              +   ``sin`` returns the y-component, ``cos`` returns the x-component.

          -   ``y = tan(330 * 2 * pi / 360);``

              -   ``tan`` is not the proper function to use here.
