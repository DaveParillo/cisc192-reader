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

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: local_variables_1
         :multiple_answers:
         :answer_a: Yes, we cannot output the value of i outside of the for loop.
         :answer_b: Yes, we cannot output anything before the for loop.
         :answer_c: Yes, we cannot reassign i to 10 outside of the for loop.
         :answer_d: Yes, we cannot let i start at 1 in the for loop.
         :answer_e: No, there are no issues with the code below.
         :correct: a, c
         :feedback_a: The scope of i is restricted to the for loop, so we cannot change the value of i outside of the for loop.
         :feedback_b: This is allowed.
         :feedback_c: The scope of i is restricted to the for loop, so we cannot output the value of i outside of the for loop.
         :feedback_d: We are allowed to initialize i to any value.
         :feedback_e: There are issues with the code. Can you find them?

         Are there any issues with the code below?

         .. code-block:: cpp

            #include <iostream>

            int main() {
              using std::cout;
              cout << "Let's print some numbers.\n";
              for (int i = 1; i < 10; ++i) {
                cout << i << "! ";
              }
              i = 10;
              cout << i << "!";
            }

   .. tab:: Q2

      .. mchoice:: local_variables_2
         :answer_a: True
         :answer_b: False
         :correct: b
         :feedback_a: They are two different variables in two different scopes but they do have the same name.
         :feedback_b: Yes, they are not the same variable.


         Take a look at the code below. The ``i`` in ``print_multiples`` is the same variable as the ``i`` in ``multiples_table``.

         .. code-block:: cpp

            #include <iostream>
            using std::cout;

            void print_multiples (int n) {
              int i = 1;
              while (i <= 6) {
                cout << n*i << '\t';
                i = i + 1;
              }
              cout << '\n';
            }

            void multiples_table() {
              int i = 1;
              while (i <= 6) {
                print_multiples (i);
                i = i + 1;
              }
            }

            int main() {
              multiples_table();
            }

   .. tab:: Q3

      .. mchoice:: local_variables_3
         :answer_a: True
         :answer_b: False
         :correct: b
         :feedback_a: The scope of ``j`` does not include ``print_multiples`` function.
         :feedback_b: Yes, ``j`` is not accessable as the value is merely passes from one function to another. We cannot have a statement such as j++; in ``print_multiples`` as it is out of the scope of ``multiples_table``


         Take a look at the code below. The variable ``j`` is accessable in the function ``print_multiples``

         .. code-block:: cpp

            #include <iostream>

            void print_multiples (int n) {
              int i = 1;
              while (i <= 6) {
                std::cout << n*i << '\t';
                i = i + 1;
              }
              std::cout << '\n';
            }

            void multiples_table() {
              int j = 1;
              while (j <= 6) {
                print_multiples (j);
                j = j + 1;
              }
            }

            int main() {
              multiples_table();
            }

