.. _functions-parameters-and-variables-are-local:

Parameters and Variables are Local
----------------------------------

Parameters and variables only exist inside their own functions. Within
the confines of ``main``, there is no such thing as phil. If you try to use
it, the compiler will complain. Similarly, inside ``print_twice`` there is no
such thing as argument.
The value of argument in main is copied into the new variable phil
when print_twice is called.

The following code will show the output of the print_twice function.
Notice that it is the argument 'b' that is outputted, not the
variable 'phil'.

.. tb-code:: cpp
   :name: locals_AC_1
   :caption: Understanding Parameters

   #include <iostream>

   void print_twice (char phil) {
       std::cout << phil << phil << '\n';
   }

   int main () {
       char argument = 'b';
       print_twice (argument);
       return 0;
   }

.. admonition:: Try This!

   Make the following changes to the previous program:
   
   - Change the value of 'phil' before printing.
   - Print the value of 'argument' after ``print_twice`` is called.

   Are the results what you expect?


.. index::
   single: local
   single: local variable

.. index::
   single: stack diagram

Variables like this are said to be **local**. In order to keep track of
parameters and local variables, it is useful to draw a **stack
diagram**. Like state diagrams, stack diagrams show the value of each
variable, but the variables are contained in larger boxes that indicate
which function they belong to.

For example, the stack diagram for ``print_twice`` looks like this:

.. digraph:: state
   :name: fig_print_twice_stack
   :caption: Stack diagram for print_twice
   :alt: stack diagram showing the print_twice call and its parameter
   :align: center

   fontname = "Bitstream Vera Sans"
   ranksep=0.1

   node [
      fontname = "Bitstream Vera Sans"
      fontsize = 11
      shape=record
      fillcolor=lightblue
   ]
   main [label="{main|{argument: 'b'}}"]
   func [label="{print_twice|{ phil: 'b'}}"]
   main -> func [style=invis]

Keeping similar names separated from eachother in C++ is called
:lang:`scope` -- and is one of the most important and powerful concepts
in C++ (or any programming language).

.. index::
   pair: function; instance

Whenever a function is called, it creates a new **instance** of that
function (a new scope) and places it on top of the function call stack.
Each instance of a function contains the parameters and local
variables for that function. In :numref:`fig_print_twice_stack`, an instance of a function is
represented by a box with the name of the function in the first section and
the variables and parameters inside.
A instance of a function on the stack are stored in
**activation records**.

In the example, ``main`` has one local variable, argument, and no
parameters. ``print_twice`` has no local variables and one parameter, named
phil.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: locals_1

         How many local variables and parameters does ``main`` have?

         ::

             void print_hello_name (string name) {
               cout << "Hello " << name << '!';
             }

             int main () {
               string name1 = "Phil";
               print_hello_name(name1);
               string name2 = "Joe";
               print_hello_name(name2);
               return 0;
             }


         - [ ] 1 local variable, 1 parameter

           A parameter would be located within the parentheses next to the function's name.
         - [ ] 0 local variables, 1 parameter

           A parameter would be located within the parentheses next to the function's name.
         - [x] 2 local variables, 0 parameters

           Correct!
         - [ ] 2 local variables, 1 parameter

           A parameter would be located within the parentheses next to the function's name.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: locals_2

         How many local variables and parameters does ``print_hello_name`` have?

         ::

             void print_hello_name (string name) {
               cout << "Hello " << name << '!';
             }

             int main () {
               string name1 = "Phil";
               print_hello_name(name1);
               string name2 = "Joe";
               print_hello_name(name2);
               return 0;
             }


         - [ ] 1 local variable, 1 parameter

           A local variable exists when a variable is declared within a function.
         - [x] 0 local variables, 1 parameter

           Correct!
         - [ ] 2 local variables, 0 parameters

           A local variable exists when a variable is declared within a function.
         - [ ] 2 local variables, 1 parameter

           A local variable exists when a variable is declared within a function.

   .. tb-tab:: Q3

      .. tb-blank::
         :name: locals_3

         Whenever we make a function call, we create a(n) {{blank}} of that fucntion,
         which contiains the parameters and local variables for that function.

         .. tb-answer::
            :match: instance
            :feedback: You could create many instances of one function, each with their own parameters and local variables if you wanted!
            :incorrect: Try again!

   .. tb-tab:: Q4

      .. tb-choice::
         :name: locals_4

         How many calls to ``hi`` are made during the exectuion of the entire program?

         ::

             void hi() {
               cout << "hiii !"<<'\n';
             }

             void print_greeting(){
               hi();
               cout<<"how are you doing today. "<<'\n';
               hi();
             }

             int main () {
               hi();
               print_greeting();
               hi();
               return 0;
             }

         - [ ] 1 call

           hi( ) is called from multiple functions.
         - [x] 4 calls

           Correct!
         - [ ] 2 calls

           hi( ) is called from multiple functions.
         - [ ] 3 calls

           Two calls from one function are indeed two seperate calls.

-----

.. admonition:: More to Explore

   - :lang:`Scope <scope>` from cppreference.com
   - :wiki:`Call statck <Call_stack>` from Wikipedia

