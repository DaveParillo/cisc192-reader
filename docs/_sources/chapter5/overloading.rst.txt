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

Many of the built-in C++ commands are overloaded, meaning that there are
different versions that accept different numbers or types of parameters.

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

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: overloading_1
         :answer_a: double price(int a, int b);
         :answer_b: double price(int a, string b, string c);
         :answer_c: double price(double x, int y, string z);
         :answer_d: all of the above
         :correct: b
         :feedback_a: This function has the same parameters as the first function below.
         :feedback_b: While this function has the same number of parameters as the second function, it takes different types of parameters.
         :feedback_c: This function has the same parameters as the second function below.
         :feedback_d: Take another look at the numbers and types of parameters.

         Which of the following function declarations would be legal if it was added to the program below?

         ::

             double price (int x, int y);
             double price (double a, int b, string c);


   .. tab:: Q2

      .. mchoice:: overloading_2
         :answer_a: recursion
         :answer_b: debugging
         :answer_c: overloading
         :answer_d: overriding
         :correct: c
         :feedback_a: Recursion is when a function calls itself.
         :feedback_b: Debugging is what we do after implementing a function.
         :feedback_c: Overloading is when we have two functions with the same name that take different parameters.
         :feedback_d: Overriding is when an inherited class uses a different method than the base class... more on this later!

         What are the following functions an example of?

         ::

             double price(int x, int y);
             double price(double a, int b, string c);


   .. tab:: Q3

      .. mchoice:: overloading_3
         :answer_a: Yes. Some of the parameters have the same names, so overloading is NOT legal.
         :answer_b: Yes. The parameters are the same types in the same order, so overloading is NOT legal.
         :answer_c: No. Some of the parameters have different names, so overloading is legal.
         :answer_d: No. The parameters are the same types in the same order, so overloading is legal.
         :correct: b
         :feedback_a: Variable names don't matter in overloading.
         :feedback_b: If the parameters are the same types in the same order, overloading is NOT legal.
         :feedback_c: Variable names don't matter in overloading.
         :feedback_d: If the parameters are the same types in the same order, overloading is NOT legal.

         Suppose you have written the following functions for baking cake.  
         Is there anything wrong with how ``bakeCake`` was overloaded?

         ::

             bool bakeCake (string cakeMix, int eggs, double milk, bool birthday);
             bool bakeCake (string cakeMix, int eggs, double water, bool holiday);

   .. tab:: Q4

      .. mchoice:: overloading_4
         :answer_a: Yes. Two functions with the same name have different return types which is not permitted.
         :answer_b: Yes. The parameters are the same types in the same order, so overloading is NOT legal.
         :answer_c: No. One of the parameters has a different name, so overloading is legal.
         :answer_d: No. One function returns an integer while the other returns a double, so overloading is legal.
         :correct: b
         :feedback_a: Return types are not considered in overloads. Any return type is permitted in all circumstances.
         :feedback_b: If the parameters are the same types in the same order, overloading is NOT legal.
         :feedback_c: Variable names don't matter in overloading.
         :feedback_d: Return type is not considered in resolving function overloads.

         Would adding both of the follwoing function declarations to a program lead to an error?

         ::

             int stockPrice (string currency, int previous_price, double interest_rate );
             double stockPrice (string currency, int older_price, double interest_rate );

