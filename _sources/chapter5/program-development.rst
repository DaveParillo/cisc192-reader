Program Development
-------------------
..	index::
	  pair: development; incremental development

At this point you should be able to look at complete C++ functions and
tell what they do. But it may not be clear yet how to go about writing
them. I am going to suggest one technique that I call **incremental
development**.

As an example, imagine you want to find the distance between two points,
given by the coordinates :math:`(x_1, y_1)` and :math:`(x_2, y_2)`. By
the usual definition,

.. math:: distance = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}

The first step is to consider what a distance function should look like
in C++. In other words, what are the inputs (parameters) and what is the
output (return value).

In this case, the two points are the parameters, and it is natural to
represent them using four doubles. The return value is the distance,
which will have type double.

Already we can write an outline of the function:

::

    double distance (double x1, double y1, double x2, double y2) {
      return 0.0;
    }

The return statement is a "stub" so that the function will compile
and return something, even though it is not the right answer. At this
stage the function doesn't do anything useful, but it is worthwhile to
try compiling it so we can identify any syntax errors before we make it
more complicated.

In order to test the new function, we have to call it with sample
values. Somewhere in main I would add:

::

    double dist = distance (1.0, 2.0, 4.0, 6.0);
    cout << dist << endl;

I chose these values so that the horizontal distance is 3 and the
vertical distance is 4; that way, the result will be 5 (the hypotenuse
of a 3-4-5 triangle). When you are testing a function, it is useful to
know the right answer.

Once we have checked the syntax of the function definition, we can start
adding lines of code one at a time. After each incremental change, we
recompile and run the program. That way, at any point we know exactly
where the error must be—in the last line we added.

The next step in the computation is to find the differences
:math:`x_2 - x_1` and :math:`y_2 - y_1`. I will store those values in
temporary variables named dx and dy.

::

    double distance (double x1, double y1, double x2, double y2) {
      double dx = x2 - x1;
      double dy = y2 - y1;
      cout << "dx is " << dx << endl;
      cout << "dy is " << dy << endl;
      return 0.0;
    }

I added output statements that will let me check the intermediate values
before proceeding. As I mentioned, I already know that they should be
3.0 and 4.0.

.. note::
   If you are ever unsure why a function isn't returning what you
   expect it to, using ``cout`` statements at different steps in
   your function will help you figure it out.

..	index::
   single: scaffolding

When the function is finished I will remove the output statements. Code
like that is called **scaffolding**, because it is helpful for building
the program, but it is not part of the final product. Sometimes it is a
good idea to keep the scaffolding around, but comment it out, just in
case you need it later.

The next step in the development is to square dx and dy. We could use
the pow function, but it is simpler and faster to just multiply each
term by itself.

::

    double distance (double x1, double y1, double x2, double y2) {
      double dx = x2 - x1;
      double dy = y2 - y1;
      double dsquared = dx*dx + dy*dy;
      cout << "dsquared is " << dsquared;
      return 0.0;
    }

Again, I would compile and run the program at this stage and check the
intermediate value (which should be 25.0).

Finally, we can use the sqrt function to compute and return the result.

::

    double distance (double x1, double y1, double x2, double y2) {
      double dx = x2 - x1;
      double dy = y2 - y1;
      double dsquared = dx*dx + dy*dy;
      return sqrt (dsquared);
    }

Then in main, we should output and check the value of the result.

.. activecode:: program_dvlmt_AC_1
   :language: cpp
   :caption: Program Development

   This program implements the distance function that we've been 
   talking about and outputs the result.
   ~~~~
   #include <cmath>
   #include <iostream>

   double distance (double x1, double y1, double x2, double y2) {
       double dx = x2 - x1;
       double dy = y2 - y1;
       double dsquared = dx*dx + dy*dy;
       double result = std::sqrt (dsquared);
       return std::sqrt (dsquared);
   }

   int main () {
       double dist = distance (1.0, 2.0, 4.0, 6.0);
       std::cout << dist << std::endl;
       return 0;
   }

As you gain more experience programming, you might find yourself writing
and debugging more than one line at a time. Nevertheless, this
incremental development process can save you a lot of debugging time.

The key aspects of the process are:

-  Start with a working program and make small, incremental changes. At
   any point, if there is an error, you will know exactly where it is.

-  Use temporary variables to hold intermediate values so you can output
   and check them.

-  Once the program is working, you might want to remove some of the
   scaffolding or consolidate multiple statements into compound
   expressions, but only if it does not make the program difficult to
   read.

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: program_dvlmt_1
         :answer_a: combining the parameters
         :answer_b: printing out the parameters
         :answer_c: returning something
         :answer_d: debugging
         :correct: c
         :feedback_a: Unless the function requires you to do so, then this is unnecessary.
         :feedback_b: If you don't know the values of the parameters, this could be useful, but there is a better answer.
         :feedback_c: This is called stubbing.  You don't have to return the correct answer, but you do need to return the correct data type.
         :feedback_d: You don't need to debug until after you've written the function.

         When writing the implementation for a function, a good place to
         start is __________.

   .. tab:: Q2

      .. mchoice:: program_dvlmt_2
         :answer_a: Use temporary variables to hold intermediate values so you can output and check them.
         :answer_b: Start with a working program and make small, incremental changes. That way you know exactly where the error is if you have one.
         :answer_c: Writing a program from start to finish, and then debugging at the end in order to understand all of the errors at once.
         :answer_d: Once the program is working, you might want to consolidate some statements into compound expressions, or remove them entirely.
         :correct: c
         :feedback_a: Temporary variables are very useful in understanding what is happening at each step.
         :feedback_b: This is the definition of incremental development.
         :feedback_c: Incremental development uses step by step debugging in order to avoid the difficulty this would present.
         :feedback_d: This is good practice, as long as it doesn't make the program difficult to read.

         Which of the following is **not** a key aspect of the incremental development process?


   .. tab:: Q3

      .. mchoice:: program_dvlmt_3
         :answer_a: scaffolding - allows the function to compile and return something
         :answer_b: stubbing - allows the function to compile and return something
         :answer_c: scaffolding - used to test values of temporary variables, later removed
         :answer_d: stubbing - used to test values of temporary variables, later removed
         :correct: c
         :feedback_a: This is not the correct definition of scaffolding.
         :feedback_b: This is the correct definition of stubbing but is not the correct answer.
         :feedback_c: Printing out the values allows you to observe whether the function is working or not.
         :feedback_d: This is not the correct definition of stubbing.

         The print statements in the distance function will be removed after testing. What is this called, and what is its purpose?

         ::

             #include <iostream>

             double distance (double x1, double y1, double x2, double y2) {
               double dx = x2 - x1;
               double dy = y2 - y1;
               std::cout << "dx is " << dx << std::endl;
               std::cout << "dy is " << dy << std::endl;
               return 0.0;
             }

