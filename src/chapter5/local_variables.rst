Local variables
---------------
.. index::
   pair: variables; local variables

About this time, you might be wondering how we can use the same variable
``i`` in both ``print_multiples`` and ``multiples_table``. Didn't I say
that you can only declare a variable once? And doesn't it cause problems
when one of the functions changes the value of the variable?

The answer to both questions is "no," because the ``i`` in
``print_multiples`` and the ``i`` in ``multiples_table`` are *not the same
variable*. They have the same name, but they do not refer to the same
storage location, and changing the value of one of them has no effect on
the other.

.. note::
   Remember that variables that are declared inside a function definition
   are local. You cannot access a local variable from outside its "home"
   function, and you are free to have multiple variables with the same
   name, as long as they are not in the same function **scope**.

The stack diagram for this program shows clearly that the two variables
named ``i`` are not in the same storage location. They can have
different values, and changing one does not affect the other.

.. digraph:: stack
   :align: center
   :alt: Stack diagram for multiples table

   fontname = "Bitstream Vera Sans"
   label="Stack diagram for multiples table";
   labelloc=bottom;
   ranksep=0.1

   node [
      fontname = "Bitstream Vera Sans"
      fontsize = 11
      shape=record
      fillcolor=lightblue
   ]

   b [label="{print_multiples()|{{n: 1}|{i: 3}}}"]
   a [label="{multiples_table()|{i: 1}}"]
   main [label="{main}"]
   main:e -> a:e -> b:e [label="   calls"]


Notice that the value of the parameter ``n`` in ``print_multiples`` has
to be the same as the value of ``i`` in ``multiples_table``. On the other
hand, the value of ``i`` in ``print_multiples`` goes from 1 up to ``n``.
In the diagram, it happens to be 3. The next time through the loop it
will be 4.

It may be a good idea to use different variable names in different
functions, to avoid confusion, but there are good reasons to reuse
names. For example, it is common to use the names ``i``, ``j`` and ``k``
as loop variables. If you avoid using them in one function just because
you used them somewhere else, you will probably make the program harder
to read.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: local_variables_1

         Are there any issues with the code below?

         .. code-block:: cpp

          #include <iostream>
          using namespace std;

          int main() {
            cout << "Let's print the multiples of 2." << endl;
            int i = 1;
            while (i < 10) {
              int j = i * 2;
              cout << i << ": " << j << endl;
              i++;
            }
            i = 10;
            j = 20;
            cout << i << ": " << j << "!";
          }

         - [x] Yes, we cannot output the value of j outside of the loop.

           The scope of i is restricted to the loop, so we cannot change the value of i outside of the loop.
         - [ ] Yes, we cannot output anything before the loop.

           This is allowed.
         - [x] Yes, we cannot reassign j to 20 outside of the loop.

           The scope of i is restricted to the loop, so we cannot output the value of i outside of the loop.
         - [ ] Yes, we cannot let i start at 1 in the loop.

           We are allowed to initialize i to any value.
         - [ ] No, there are no issues with the code below.

           There are issues with the code. Can you find them?

   .. tb-tab:: Q2

      .. tb-choice::
         :name: local_variables_2

         Take a look at the code below. Is the ``i`` in ``printMultiples`` the same variable as the ``i`` in ``printMultTable``?

         .. code-block:: cpp

          #include <iostream>
          using namespace std;

          void printMultiples (int n) {
            int i = 1;
            while (i <= 6) {
              cout << n * i << '\t';
              i = i + 1;
            }
            cout << endl;
          }

          void printMultTable() {
            int i = 1;
            while (i <= 6) {
              printMultiples (i);
              i = i + 1;
            }
          }

          int main() {
            printMultTable();
          }

         - [ ] Yes

           They are two different variables in two different scopes, but they do have the same name.
         - [x] No

           Correct! They are not the same variable.

   .. tb-tab:: Q3

      .. tb-choice::
         :name: local_variables_3

         Take a look at the code below. Is the variable ``j`` accessable  in the function ``printMultiples``?

         .. code-block:: cpp

             #include <iostream>
             using namespace std;

             void printMultiples (int n) {
               int i = 1;
               while (i <= 6) {
                 cout << n * i << '\t';
                 i = i + 1;
               }
               cout << endl;
             }

             void printMultTable() {
               int j = 1;
               while (j <= 6) {
                 printMultiples (j);
                 j = j + 1;
               }
             }

             int main() {
               printMultTable();
             }


         - [ ] Yes

           - The scope of ``j`` does not include ``printMultiples`` function.

         - [x] No

           + Correct! ``j`` is not accessable as the value is merely passes from one function to another. We cannot have a statement such as j++; in ``printMultiples`` as it is out of the scope of ``printMultTable``



