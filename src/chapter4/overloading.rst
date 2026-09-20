.. _fruitful-functions-overloading:

Overloading
-----------

In the previous section you might have noticed that ``fred`` and ``area``
perform similar functions—finding the area of a circle—but take
different parameters. For ``area``, we have to provide the radius; for ``fred``,
we provide two points.

If two functions do the same thing, it is natural to give them the same
name. In other words, it would make more sense if ``fred`` were called ``area``.

..	index::
    single: overloading

Having more than one function with the same name, which is called
**overloading**, is legal in C++ *as long as each version takes
different parameters*. So we can go ahead and rename ``fred``:

::

    double area (double xc, double yc, double xp, double yp) {
      return area (distance (xc, yc, xp, yp));
    }

This looks like a recursive function, but it is not. Actually, this
version of ``area`` is calling the other version. When you call an
overloaded function, C++ knows which version you want by looking at the
arguments that you provide. If you write:

::

    double x = area (3.0);

C++ goes looking for a function named ``area`` that takes a double as an
argument, and so it uses the first version. If you write

::

    double x = area (1.0, 2.0, 4.0, 6.0);

C++ uses the second version of ``area``.

Many of C++ standard library functions are overloaded, meaning that there are
different versions that accept different numbers or types of parameters.

Function overloads are a huge advantage over C
where (nearly) every function is global
and every function name must be unique.
For example:

- C defines 7 different functions just for absolute value 

  - ``abs``, ``llabs``, ``fabs``, ``fabsf``, etc.
    see :cmath:`abs`

- and 13 different functions for different types of 
  see :numeric:`division operations <math/div>`.

This just adds to the amount of stuff programmers have to commit to memory.
In C++, you only have to remember a single function to compute
the absolute value: ``abs``.

In order to count as a valid overload, 
either the number of parameters must be different, 
or the parameter types must be different, or a combination of both. 
For example:

.. tb-group::
   :name: example-tab

   .. tb-tab:: addition

      .. tb-code:: cpp
         :name: overloading-AC1
         :caption: Example overloading-AC1

         #include <iostream>
         using std::cout;

         // add two ints
         int add (int a, int b) {
           return a+b;
         }
         // add two doubles
         double add (double a, double b) {
           return a+b;
         }

         int main () {
           int x=5, y=2;
           double p=3.14, e=2.718;
           cout << add (x,y) << '\n';
           cout << add (p,e) << '\n';

           // error: call to overloaded function add (double, int) ambiguous
           // cout << add (31.4, 10) << '\n';

           // explicit conversion is OK
           cout << add (31.4, double(10)) << '\n';
         }

   .. tb-tab:: volume

      .. tb-code:: cpp
         :name: volume-overloading-AC2
         :caption: Example volume-overloading-AC2

         #include <iostream>
         #include <cmath>

         namespace mesa {
            constexpr double pi = 3.141592653;
         }

         // volume of a cube
         double volume (const double a) {
           return a * a * a;
         }

         // volume of a cylinder
         double volume (const double r, const double h) {
           return mesa::pi * r * r * h;
         }

         // volume of a cuboid
         double volume (const double a, const double b, const double c) {
           return a * b * c;
         }

         int main() {
           std::cout << "volume of a 2 x 2 x 2 cube: " 
                     << volume(2) << '\n'

                     << "volume of a cylinder, radius 2, height 3: " 
                     << volume(2, 3) << '\n'

                     << "volume of a 2 x 3 x 4 cuboid: " 
                     << volume(2, 3, 4) << '\n';
           return 0;
         }


.. note:: 

   The return type is **not** part of the overload.

   Two functions in the same namespace that differ only in return type will not compile.



**Overloading anti-patterns**

How many parameters are too many?

This is an often asked question, with no clear cut answer.
It is primarily a question of *clarity* and *design*.


For example, given:

.. code-block:: cpp

   int operate (float a, int b, long c, double d);

In this case, the parameters and function name provide no guidance on
how to call this function.
So four is probably too many parameters, 
simply because future usage errors are likely.

Keep in mind that more parameters equal more complexity.
Limit the number of parameters you need in a given method. 
Also, be wary of overloads with the same number of parameters and different types.
For example:

.. code-block:: cpp

   int operate (double a, int b);
   int operate (int a, double b);

Depending on what ``operate`` does with it's parameters, 
reversing the order of the parameters could have drastic consequences.
We just don't know without looking at the source code.
In this case even two parameters is too many.
It is almost certain someone will invoke the wrong version occasionally.

.. warning::
   Although overloading is a useful feature, it should be used with
   caution. You might get yourself nicely confused if you are trying to
   debug one version of a function while accidentally calling a different
   one.

Actually, that reminds me of one of the cardinal rules of debugging:
**make sure that the version of the program you are looking at is the
version of the program that is running!** Some time you may find
yourself making one change after another in your program, and seeing the
same thing every time you run it. This is a warning sign that for one
reason or another you are not running the version of the program you
think you are. To check, stick in an output statement (it doesn't matter
what it says) and make sure the behavior of the program changes
accordingly.



.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: overloading_1

         Which of the following function declarations would be legal if it was added to the program below?

         ::

             double price (int x, int y);
             double price (double a, int b, string c);


         - [ ] double price(int a, int b);

           This function has the same parameters as the first function below.
         - [x] double price(int a, string b, string c);

           While this function has the same number of parameters as the second function, it takes different types of parameters.
         - [ ] double price(double x, int y, string z);

           This function has the same parameters as the second function below.
         - [ ] all of the above

           Take another look at the numbers and types of parameters.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: overloading_2

         What are the following functions an example of?

         ::

             double price(int x, int y);
             double price(double a, int b, string c);


         - [ ] recursion

           Recursion is when a function calls itself.
         - [ ] debugging

           Debugging is what we do after implementing a function.
         - [x] overloading

           Overloading is when we have two functions with the same name that take different parameters.
         - [ ] overriding

           Overriding is when an inherited class uses a different method than the base class... more on this later!

   .. tb-tab:: Q3

      .. tb-choice::
         :name: overloading_3

         Suppose you have written the following functions for baking cake.  
         Is there anything wrong with how ``bake_cake`` was overloaded?

         ::

             bool bake_cake (string cake_mix, int eggs, double milk, bool birthday);
             bool bake_cake (string cake_mix, int eggs, double water, bool holiday);

         - [ ] Yes. Some of the parameters have the same names, so overloading is NOT legal.

           Variable names don't matter in overloading.
         - [x] Yes. The parameters are the same types in the same order, so overloading is NOT legal.

           If the parameters are the same types in the same order, overloading is NOT legal.
         - [ ] No. Some of the parameters have different names, so overloading is legal.

           Variable names don't matter in overloading.
         - [ ] No. The parameters are the same types in the same order, so overloading is legal.

           If the parameters are the same types in the same order, overloading is NOT legal.

   .. tb-tab:: Q4

      .. tb-choice::
         :name: overloading_4

         Would adding both of the following function declarations to a program lead to an error?

         ::

             int stock_price (string currency, int previous_price, double interest_rate );
             double stock_price (string currency, int older_price, double interest_rate );

         - [ ] Yes. Two functions with the same name have different return types which is not permitted.

           Return types are not considered in overloads. Any return type is permitted in all circumstances.
         - [x] Yes. The parameters are the same types in the same order, so overloading is NOT legal.

           If the parameters are the same types in the same order, overloading is NOT legal.
         - [ ] No. One of the parameters has a different name, so overloading is legal.

           Variable names don't matter in overloading.
         - [ ] No. One function returns an integer while the other returns a double, so overloading is legal.

           Return type is not considered in resolving function overloads.

-----

.. admonition:: More to Explore

   - From cppreference.com
     
     - :numeric:`division operations <math/div>` and :cmath:`abs`
     - :lang:`Overload resolution <overload_resolution>`
     
