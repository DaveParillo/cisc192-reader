Passing other types by reference
--------------------------------

It's not just structures that can be passed by reference. All the other
types we've seen can, too. For example, to swap two integers, we could
write something like:

::

   void swap (int& x, int& y) {
     int temp = x;
     x = y;
     y = temp;
   }

We would call this function in the usual way:

::

     int i = 7;
     int j = 9;
     swap (i, j);
     cout << i << j << '\n';

The output of this program is ``97``. Draw a stack diagram for this
program to convince yourself this is true. If the parameters ``x`` and
``y`` were declared as regular parameters (without the ``&``\ s),
``swap`` would not work. It would modify ``x`` and ``y`` and have no
effect on ``i`` and ``j``.

The active code below uses the ``swap`` function. Run the active code
for the output!

.. tb-code:: cpp
   :name: pass_others_reference_AC_1
   :caption: Example pass_others_reference_AC_1
   :compileargs: ['-Wall', '-std=c++20']

   #include <iostream>

   void swap (int& x, int& y) {
       int temp = x;
       x = y;
       y = temp;
   }

   int main() {
       int i = 7;
       int j = 9;
       swap (i, j);
       std::cout << i << ' ' << j;
   }

When people start passing things like integers by reference, they often
try to use an expression as a reference argument. For example:

::

   int i = 7;
   int j = 9;
   swap (i, j+1);         // WRONG!!

This is not legal because the expression ``j+1`` is not a variable—it
does not occupy a location that the reference can refer to. It is a
little tricky to figure out exactly what kinds of expressions can be
passed by reference. For now a good rule of thumb is that reference
arguments have to be variables.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: pass_others_reference_1

         Which of the parameters in the following code block are pass-by-reference?

         .. code-block:: cpp

            void swap (int& x, int& y) {
              int temp = x;
              x = y;
              y = temp;
            }

            void add (int& z, int q) {
              z = z + y;
            }

            int multiply (int a, int b) {
              int total = a * b;
              return total;
            }

         - [x] ``x``, ``y``, ``z``

           + Correct!

         - [ ] ``x``, ``y``, ``z``, ``q``

           - Pay attention to the placement of the ``&``

         - [ ] ``a``, ``b``

           - Pay attention to the placement of the ``&``


   .. tb-tab:: Q2

      .. tb-parsons::
         :name: pass_others_reference_2

         Create a function called ``add`` that takes two parameters, an integer x and an integer y. The function should add y to x, then print x. The variable x should be modified, while the variable y should not.

         .. code-block:: cpp

            {{group}}
            void add(int& x, int y) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void add(int x&, int y) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            void add(int x, int y) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            void add(int& x, int& y) { #distractor
            {{endgroup}}
            {{group}}
               x = x + y;
            {{endgroup}}
            {{distractor}}
            {{group}}
               y = x + y; #distractor
            {{endgroup}}
            {{group}}
               cout << x;
            }
            {{endgroup}}
            {{distractor}}
            {{group}}
               return x; #distractor
            }
            {{endgroup}}

