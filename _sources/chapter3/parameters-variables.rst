Parameters and Variables are Local
----------------------------------

Parameters and variables only exist inside their own functions. Within
the confines of ``main``, there is no such thing as phil. If you try to use
it, the compiler will complain. Similarly, inside ``print_twice`` there is no
such thing as argument.
The value of argument in main is copied into the new variable phil
when print_twice is called.

.. activecode:: locals_AC_1
   :language: cpp
   :caption: Understanding Parameters

   The following code will show the output of the print_twice function.
   Notice that it is the argument 'b' that is outputted, not the
   variable 'phil'.
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
   :align: center
   :alt: Stack diagram for print_twice

   fontname = "Bitstream Vera Sans"
   label="Stack diagram for print_twice"
   labelloc=bottom
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


.. index::
   pair: function; instance

Whenever a function is called, it creates a new **instance** of that
function and places it on top of the function call stack.
Each instance of a function contains the parameters and local
variables for that function. In the diagram an instance of a function is
represented by a box with the name of the function in the first section and
the variables and parameters inside.
A instance of a function on the stack are stored in
**activation records**.

In the example, ``main`` has one local variable, argument, and no
parameters. ``print_twice`` has no local variables and one parameter, named
phil.

.. tabbed:: tab_check

   .. tab:: Q1

      .. mchoice:: locals_1
         :answer_a: 1 local variable, 1 parameter
         :answer_b: 0 local variables, 1 parameter
         :answer_c: 2 local variables, 0 parameters
         :answer_d: 2 local variables, 1 parameter
         :correct: c
         :feedback_a: A parameter would be located within the parentheses next to the function's name.
         :feedback_b: A parameter would be located within the parentheses next to the function's name.
         :feedback_c: Correct!
         :feedback_d: A parameter would be located within the parentheses next to the function's name.

         How many local variables and parameters does ``main`` have?

         ::

             void prit_hello_name (string name) {
               cout << "Hello " << name << "!";
             }

             int main () {
               string name1 = "Phil";
               prit_hello_name(name1);
               string name2 = "Joe";
               prit_hello_name(name2);
               return 0;
             }


   .. tab:: Q2

      .. mchoice:: locals_2
         :answer_a: 1 local variable, 1 parameter
         :answer_b: 0 local variables, 1 parameter
         :answer_c: 2 local variables, 0 parameters
         :answer_d: 2 local variables, 1 parameter
         :correct: b
         :feedback_a: A local variable exists when a variable is declared within a function.
         :feedback_b: Correct!
         :feedback_c: A local variable exists when a variable is declared within a function.
         :feedback_d: A local variable exists when a variable is declared within a function.

         How many local variables and parameters does ``prit_hello_name`` have?

         ::

             void prit_hello_name (string name) {
               cout << "Hello " << name << "!";
             }

             int main () {
               string name1 = "Phil";
               prit_hello_name(name1);
               string name2 = "Joe";
               prit_hello_name(name2);
               return 0;
             }


   .. tab:: Q3

      .. fillintheblank:: locals_3

         Whenever we make a function call, we create a(n) |blank| of that fucntion,
         which contiains the parameters and local variables for that function.
          
         - :[Ii][Nn][Ss][Tt][Aa][Nn][Cc][Ee]: You could create many instances of one function, each with their own parameters and local variables if you wanted!
           :.*: Try again!

   .. tab:: Q4

      .. mchoice:: locals_4
         :answer_a: 1 call
         :answer_b: 4 calls
         :answer_c: 2 calls
         :answer_d: 3 calls
         :correct: b
         :feedback_a: hi( ) is called from multiple functions.
         :feedback_b: Correct!
         :feedback_c: hi( ) is called from multiple functions.
         :feedback_d: Two calls from one function are indeed two seperate calls.

         How many calls to ``hi`` are made during the exectuion of the entire program?

         ::

             void hi() {
               cout << "hiii !"<<endl;
             }
            
             void print_greeting(){
               hi();
               cout<<"how are you doing today. "<<endl;
               hi();
             }

             int main () {
               hi();
               print_greeting();
               hi();
               return 0;
             }

