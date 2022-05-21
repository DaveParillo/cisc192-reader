Pass by value
-------------
.. index::
   single: pass by value

When you pass a structure as an argument, remember that the argument and
the parameter are not the same variable. Instead, there are two
variables (one in the caller and one in the callee) that have the same
value, at least initially. For example, when we call ``print_point``,
the stack diagram looks like this:

.. digraph:: state
   :align: center
   :alt: function call stack diagram

   graph [compound = true];
   fontname = "Bitstream Vera Sans"
   label="Function call stack diagram";
   labelloc=bottom;
   node [
      shape=record
      fontname = "Bitstream Vera Sans"
      fontsize = 11
      style=filled
      fillcolor=lightblue
   ]

   subgraph cluster_main {
      label="main"
      labelloc=top;
      subgraph cluster_0 {
         label="blank"
         main [label="x: 3 | y: 4"]
      }
   }

   subgraph cluster_func {
      label="print_point"
      labelloc=top;
      subgraph cluster_1 {
         label="p"
         print [label="x: 3 | y: 4"]
      }
   }

   main -> print [style=invis]; 

If ``print_point`` happened to change one of the instance variables of
``p``, it would have no effect on ``blank``. Of course, there is no
reason for ``print_point`` to modify its parameter, so this isolation
between the two functions is appropriate.

This kind of parameter-passing is called "pass by value" because it is
the value of the structure (or other type) that gets passed to the
function.

Remember pass by value will always make a copy, leaving the original unchanged.

.. activecode:: call_by_value_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:

   Take a look at the active code below.
   Notice from the output of the code below how the 
   function ``add_two`` changes the instance variables, but not on ``blank`` itself.
   ~~~~
   #include <iostream>
 
   struct point {
       double x;
       double y;
   };

    void add_two (point p) {
       std::cout << '(' << p.x + 2 << ", " << p.y + 2 << ")\n";
   }
 
   int main() {
       point blank = { 3.0, 4.0 };
       add_two (blank);
       std::cout << '(' << blank.x << ", " << blank.y << ")\n";
   }
 

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: call_by_value_1
         :practice: T
         :answer_a: 2 4
         :answer_b: 2 4 2
         :answer_c: 4 4 2
         :answer_d: 2 4 4
         :correct: b
         :feedback_a: Take a look at exactly what is being output.
         :feedback_b: Correct!
         :feedback_c: Take a look at exactly what is being output.
         :feedback_d: Remember the rules of pass by value.

         What will print?

         .. code-block:: cpp

            int add_two(int x) {
              cout << x << ' ';
              x = x + 2;
              cout << x << ' ';
              return x;
            }

            int main() {
              int num = 2;
              add_two(num);
              cout << num << '\n';
            }

   .. tab:: Q2

      .. mchoice:: call_by_value_2
         :practice: T
         :answer_a: 6.0, 8.0, 3.0, 4.0
         :answer_b: 6.0, 8.0, 6.0, 8.0
         :answer_c: 6.08.03.04.0
         :answer_d: 6.08.06.08.0
         :correct: a
         :feedback_a: Correct!
         :feedback_b: Remember the rules of pass by value.
         :feedback_c: Take a look at exactly what is being outputted.
         :feedback_d: Take a look at exactly what is being outputted.

         What will print?

         .. code-block:: cpp

            struct point {
              double x;
              double y;
            };

            void times_two (point p) {
              cout << '(' << p.x * 2 << ", " << p.y * 2 << ')';
            }

            int main() {
              point blank = { 3.0, 4.0 };
              times_two (blank);
              cout << ", " << blank << endl;
            }


