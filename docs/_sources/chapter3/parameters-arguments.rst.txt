Parameters and Arguments
------------------------

.. index::
   single: parameter

Some of the built-in functions we have used have **parameters**, which
are values that you provide to let the function do its job. For example,
if you want to find the sine of a number, you have to indicate what the
number is. Thus, ``sin`` takes a ``double`` value as a parameter.

Some functions take more than one parameter, like ``pow``, which takes two
``double`` s, the base and the exponent.

Notice that in each of these cases we have to specify not only how many
parameters there are, but also what type they are. So it shouldn't
surprise you that when you write a function definition, the parameter list
indicates the type of each parameter. For example:

::

    void print_twice (char phil) {
      cout << phil << phil << endl;
    }

This function takes a single parameter, named 'phil', that has type ``char``.
Whatever that parameter is (and at this point we have no idea what it
is), it gets printed twice, followed by a new line. I chose the name phil
to suggest that the name you give a parameter is up to you, but in
general you want to choose something more illustrative than phil.

In order to call this function, we have to provide a ``char``. For example,
we might have a ``main`` function like this:

::

    int main () {
      print_twice ('a');
      return 0;
    }

.. index::
   single: argument

.. index::
   single: pass

The ``char`` value you provide is called an **argument**, and we say that
the argument is **passed** to the function. In this case the value ’a’
is passed as an argument to print_twice where it will get printed twice.

Alternatively, if we had a ``char`` variable, we could use it as an argument
instead:

::

    int main () {
      char argument = 'b';
      print_twice (argument);
      return 0;
    }

Notice something very important here: the name of the variable we pass
as an argument (argument) has nothing to do with the name of the
parameter (phil). Let me say that again:

.. note::
   The name of the variable we pass as an argument has nothing to do
   with the name of the parameter.

They can be the same or they can be different, but it is important to
realize that they are not the same thing, except that they happen to
have the same value (in this case, the character ’b’).

.. caution::
   The value you provide as an argument must have the same type as the
   parameter of the function you call.

This rule is important, but it is sometimes confusing because C++ 
sometimes converts arguments from one type to another automatically. 
For now you should learn the general rule, and we will deal with 
exceptions later.

.. tabbed:: tab_check

   .. tab:: Q1

      .. activecode:: params_args_AC_1
         :language: cpp
         :caption: Parameter Practice

         The following code will show the output of the print_twice function.
         Try modifying the value of argument to change the output.
         ~~~~
         #include <iostream>

         void print_twice (char phil) {
             std::cout << phil << phil << std::endl;
         }

         int main () {
             char argument = 'b';
             print_twice (argument);
             return 0;
         }


   .. tab:: Q2

      .. fillintheblank:: params_args_1

         ::

             #include <iostream>

             void print_twice (char phil) {
               std::cout << phil << phil << std::endl;
             }

             int main () {
               string argument = "s";
               print_twice (argument);
               return 0;
             }

         What will be printed to the terminal?  If nothing will print, 
         or if the compiler will throw an error, type "error".
          
         - :error: The type provided does not match the expected parameter type!
           :ss: The type provided does not match the expected parameter type!
           :.*: Try again!


   .. tab:: Q3

      .. fillintheblank:: params_args_2

         ::

             #include <iostream>

             void print_twice (char phil) {
               std::cout << phil << phil << std::endl;
             }

             int main () {
               char argument = 'b';
               print_twice (argument);
               return 0;
             }

         What will be printed to the terminal?  If nothing will print, 
         or if the compiler will throw an error, type "error".
          
         - :bb: The print_twice fucntion will print the character argument proveided two times.
           :error: Something will be printed to the terminal!
           :.*: Try again!


   .. tab:: Q4

      .. dragndrop:: params_args_4
          :feedback: Try again!
          :match_1: int timesTwo(int x, int y);|||timesTwo(4, 7);
          :match_2: int timesTwo(string y, int x);|||timesTwo("hello", 10);
          :match_3: int timesTwo(double x, string y);|||timesTwo(4.5, "hello");
          :match_4: int timesTwo(string x, string y);|||timesTwo("hello", "hi");

          Match the function declaration to an example of its function call.
