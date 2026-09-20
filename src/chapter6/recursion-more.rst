More recursion
--------------
.. index::
   pair: programming language; complete programming language

So far we have only learned a small subset of C++, but you might be
interested to know that this subset is now a **complete** programming
language, by which I mean that anything that can be computed can be
expressed in this language. Any program ever written could be rewritten
using only the language features we have used so far (actually, we would
need a few commands to control devices like the keyboard, mouse, disks,
etc., but that’s all).

Proving that claim is a non-trivial exercise first accomplished by Alan
Turing, one of the first computer scientists (well, some would argue
that he was a mathematician, but a lot of the early computer scientists
started as mathematicians). Accordingly, it is known as the Turing
thesis. If you take a course on the Theory of Computation, you will have
a chance to see the proof.

To give you an idea of what you can do with the tools we have learned so
far, we’ll evaluate a few recursively-defined mathematical functions. A
recursive definition is similar to a circular definition, in the sense
that the definition contains a reference to the thing being defined. A
truly circular definition is typically not very useful:

frabjuous:
    an adjective used to describe something that is frabjuous.

.. index::
   single: factorial 

If you saw that definition in the dictionary, you might be annoyed. On
the other hand, if you looked up the definition of the mathematical
function **factorial**, you might get something like:

.. math::

   \begin{aligned}
   &&  0! = 1 \\
   &&  n! = n \cdot (n-1)!\end{aligned}

.. note::
   Factorial is usually denoted with the symbol :math:`!`, which is not to
   be confused with the C++ logical operator ! which means NOT.

This definition says that the factorial of 0 is 1, and the factorial of any
other value, :math:`n`, is :math:`n` multiplied by the factorial of
:math:`n-1`. So :math:`3!` is 3 times :math:`2!`, which is 2 times
:math:`1!`, which is 1 times 0!. Putting it all together, we get
:math:`3!` equal to 3 times 2 times 1 times 1, which is 6.

If you can write a recursive definition of something, you can usually
write a C++ program to evaluate it. The first step is to decide what the
parameters are for this function, and what the return type is. With a
little thought, you should conclude that factorial takes an integer as a
parameter and returns an integer:

::

    int factorial (int n) {
    }

If the argument happens to be zero, all we have to do is return 1:

::

    int factorial (int n) {
      if (n == 0) {
        return 1;
      }
    }

Otherwise, and this is the interesting part, we have to make a recursive
call to find the factorial of :math:`n-1`, and then multiply it by
:math:`n`.

This program uses recursion to calculate the factorial of
the passed argument.

.. tb-code:: cpp
   :name: more_recursion_AC_1
   :caption: Factorial Recursion
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>

   int factorial (int n) {
       if (n == 0) {
           return 1;
       } 
       int recurse = factorial (n-1);
       int result = n * recurse;
       return result;
   }

   int main () {
       std::cout << factorial(3) << '\n';
   }


If we look at the flow of execution for this program, it is similar to
``repeat_lines`` from the previous chapter.
If we call factorial with the value 3:

Since 3 is not zero, we continue branch and calculate the
factorial of :math:`n-1`...

    Since 2 is not zero, we continue branch and calculate the
    factorial of :math:`n-1`...

        Since 1 is not zero, we continue branch and calculate the
        factorial of :math:`n-1`...

            Since 0 *is* zero, we take the first branch and return the
            value 1 immediately without making any more recursive calls.

        The return value (1) gets multiplied by n, which is 1, and the
        result is returned.

    The return value (1) gets multiplied by n, which is 2, and the
    result is returned.

The return value (2) gets multiplied by n, which is 3, and the result,
6, is returned to main, or whoever called factorial (3).

The stack diagram in :numref:`fig_factorial_stack` shows this sequence of function
calls:

The return values are shown being passed back as the stack unwinds.

.. digraph:: factorial
   :name: fig_factorial_stack
   :caption: Stack diagram for factorial
   :alt: stack diagram showing recursive factorial calls and results
   :align: center

   fontname = "Bitstream Vera Sans"
   ranksep=0.1
   nodesep=0.1

   node [
      fontname = "Bitstream Vera Sans"
      fontsize = 11
      shape=record
      fillcolor=lightblue
   ]

   n0 [label="{ factorial| {n: 0 |base case | }}"]
   n1 [label="{ factorial| {n: 1 |recurse: 1 |result: 1}}"]
   n2 [label="{ factorial| {n: 2 |recurse: 1 |result: 2}}"]
   n3 [label="{ factorial| {n: 3 |recurse: 2 |result: 6}}"]
   
   n1:w -> n0:w [xlabel="return 1 ", dir="back"]
   n2:w -> n1:w [xlabel="return 1 ", dir="back"]
   n3:w -> n2:w [xlabel="return 2 ", dir="back"]
   main:w -> n3:w [xlabel="return 6 ", dir="back"]
   main:e -> n3:e [xlabel="calls factorial"]
   n3:e -> n2:e -> n1:e -> n0:e [xlabel=" calls"]


Notice that in the last instance of factorial, the local variables
recurse and result do not exist because when n=0 the branch that creates
them does not execute.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1


      .. tb-choice::
         :name: more_recursion_1

         In the example above, how many times was the ``factorial`` function
         called?


         - [ ] 1

           As the programmer, we explicitly call this function one time... but remember, recursive functions call themselves!
         - [ ] 2

           Not quite! Maybe you were thinking of the two possible branches of the function call.
         - [ ] 3

           You're close! But what happens when n = 0?
         - [x] 4

           The function is called four times total.  Three of those times, the function recurses.  The last time, the function reaches its base case and returns 1.

   .. tb-tab:: Q2

      .. tb-blank::
         :name: more_recursion_2

         **Complete the circular definition:** unreal - a word used to describe
         something that is {{blank}}.

         .. tb-answer::
            :match: unreal
            :feedback: Correct! Circular defintions are a great example of recursion.
            :hint: x; Try again!

   .. tb-tab:: Q3

      .. tb-blank::
         :name: more_recursion_3

         The factorial of 12 is {{blank}}.

         .. tb-answer::
            :match: 479001600
            :feedback: Correct!
            :hint: x; Try plugging this into the active code!

   .. tb-tab:: Q4

      .. tb-choice::
         :name: mce_6_2

         What is the final value of ``i`` when the code finished running?

         .. code-block:: cpp

          int main() {
            int x = 0;
            int i = 1;
            while (i < 10) {
              x = i;
              i++;
            }
            cout << x;
          }

         - [ ] 0

           - ``i`` is initialized with a value of 1 and is incremented, so it will never have a value of 0.

         - [ ] 1

           - ``i`` is initialized with a value of 1 but it is incremented during the while loop.

         - [ ] 9

           - This is the final value of ``x`` when the code is finished running.

         - [x] 10

           + In order for the while loop to terminate, the condition ``i < 10`` must be false, and this is achieved when ``i`` is incremented to 10.

