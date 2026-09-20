Stack Diagrams for Recursive Functions
--------------------------------------

.. index::
   single: stack diagram

In the previous chapter we used a **stack diagram** to represent the state
of a program during a function call. The same kind of diagram can make
it easier to interpret a recursive function.

Remember that every time a function gets called it creates a new
instance that contains the function’s local variables and parameters.

The stack diagram in :numref:`fig_countdown_stack` shows ``countdown`` called
with ``n = 3``:

.. digraph:: stack
   :name: fig_countdown_stack
   :caption: Stack diagram for countdown
   :alt: stack diagram showing countdown stack frames
   :align: center

   fontname = "Bitstream Vera Sans"
   ranksep=0.1

   node [
      fontname = "Bitstream Vera Sans"
      fontsize = 11
      shape=record
      fillcolor=lightblue
   ]
   d [label="{countdown()|{ n: 0 }}"]
   c [label="{countdown()|{n: 1}}"]
   b [label="{countdown()|{n: 2}}"]
   a [label="{countdown()|{n: 3}}"]
   main [label="{main|{countdown()}}"]
   main:e -> a:e -> b:e -> c:e -> d:e [label="   calls"]


There is one instance of ``main`` and **four** instances of ``countdown``, each with
a different value for the parameter ``n``. The top of the stack,
``countdown`` with ``n = 0`` is the base case. It does not make a recursive call,
so there are no more instances of ``countdown``.

.. note::

   Does the stack grow upward or downward?

   Actually, it's implementation defined.
   But on any given platform, stack growth is consistent.
   It can't grow 'up' one day and 'down' the next.

   We normally think of a stack like a physical stack of plates
   with the most recent item on the top.
   When the stack grows 'down' then the most recent item appears visually
   on the bottom.
   Slightly confusing, but they are drawn this way in the book to be
   consistent with the stack visualizations in codelens.

The instance of ``main`` is calls countdown, but does not have any parameters
or local variables. 

.. admonition:: Try This!

  Draw a stack diagram for ``print_lines``, 
  invoked with the parameter n = 4.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: stack_1

         Refer to the ``n_lines`` function below.  It is the same as the ``n_lines``
         function defined on the previous page.  How many instances of ``n_lines``
         would there be in the stack diagram if we begin with n = 4?

         ::

             void n_lines(int n) {
               if (n > 0) {
                 cout << '\n';
                 n_lines(n + 1);
               }
             }

         - [ ] 3

           If n_lines could reach its base case, it cannot be done in 3 function calls.
         - [ ] 4

           If n_lines could reach its base case, it cannot be done in 4 function calls.
         - [ ] 5

           If n_lines could reach its base case, it could be done in 5 function calls, but does it ever reach the base case?
         - [x] infinite

           The n_lines function never reaches its base case, so the stack diagram would be infinitely long.

