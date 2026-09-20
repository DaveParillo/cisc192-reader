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

Take a look at the active code below.
Notice from the output of the code below how the 
function ``add_two`` changes the instance variables, but not on ``blank`` itself.

.. tb-code:: cpp
   :name: call_by_value_AC_1
   :caption: Example call_by_value_AC_1
   :compileargs: ['-Wall', '-std=c++20']

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


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: call_by_value_1

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

         - [ ] ``2 4``

           - Take a look at exactly what is being outputted.

         - [x] ``2 4 2``

           + Correct!

         - [ ] ``4 4 2``

           - Take a look at exactly what is being outputted.

         - [ ] ``2 4 4``

           - Remember the rules of pass by value.


   .. tb-tab:: Q2

      .. tb-choice::
         :name: call_by_value_2

         What will print?

         .. code-block:: cpp

            struct point {
              int x, y;
            };

            void times_two (point p) {
              p.x = p.x * 2;
              p.y = p.y * 2;
              cout << '(' << p.x << ", " << p.y << ')';
            }

            int main() {
              point blank = { 3, 4 };
              times_two (blank);
              cout << ", " << blank.x << '\n';
            }

         - [x] ``(6, 8), 3``

           + Correct!

         - [ ] ``(6, 8), 6``

           - Remember the rules of pass by value.

         - [ ] ``(68),3``

           - Take a look at exactly what is being outputted.

         - [ ] ``68, 6``

           - Take a look at exactly what is being outputted.

