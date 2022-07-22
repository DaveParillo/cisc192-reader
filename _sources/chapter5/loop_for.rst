The ``for`` statement
---------------------

The loops we have written so far have a number of elements in common.
All of them start by initializing a variable; they have a test, or
condition, that depends on that variable; and inside the loop they do
something to that variable, like increment it.

.. index::
   single: for loop

This type of loop is so common that there is an alternate loop
statement, called ``for``, that expresses it more concisely. The general
syntax looks like this:

::

     for (INITIALIZER; CONDITION; INCREMENTOR) {
       BODY
     }

This statement is exactly equivalent to

::

     INITIALIZER;
     while (CONDITION) {
       BODY
       INCREMENTOR
     }

except that it is more concise and, since it puts all the loop-related
statements in one place, it is easier to read. For example:

::

     // print words 1 character at a time, with a space
     string words = "The rain in Spain falls mainly on the plain.";
     for (size_t i = 0; i < words.size(); ++i) {
       cout << words[i] << ' ';
     }

is equivalent to

::

     size_t i = 0;
     while (i < words.size()) {
       cout << count[i] << ' ';
       ++i;
     }

The main advantage of the for loop is that the loop variable ``i`` is only
accessible inside the for loop.

Often the loops we write start at the beginning and increment
one element at a time until the end is reached.
For loops are more general purpose than that.

- The initializer does not have to be zero
- The loop can terminate using any boolean expression that makes sense
- The 'incrementor' does not need to increase by one each step.
  Decrementing and dividing by 2 are very common alternatives.


.. tabbed:: for_loop_tabbed

   .. tab:: while loop

      .. activecode:: for_loops_AC_1
         :language: cpp
         :nocodelens:

         Run the active code below, which uses a ``while`` loop.

         We have been using these for a while --
         no suprises here.
         ~~~~
         #include <iostream>
         #include <string>

         int main() {
             // print words in reverse
             std::string words = "The rain in Spain falls mainly on the plain.";

             size_t i = words.size();
             while (i > 0) {
               std::cout << words[i-1];
               --i;
             }
             return 0;
         }

   .. tab:: for loop

      .. activecode:: for_loops_AC_2
         :language: cpp
         :nocodelens:

         Run the active code below, which uses a ``for`` loop.
         ~~~~
         #include <iostream>
         #include <string>

         int main() {
             // print words in reverse
             std::string words = "The rain in Spain falls mainly on the plain.";
             for (size_t i = words.size(); i > 0; --i) {
               std::cout << words[i-1];
             }
             return 0;
         }

When are loops are of the simple sort:
- The data source is an array or container
- and we want to start at the beginning and step forward until the end

Then C++ offers an even simpler syntax starting in C++11:

::

     for (VARIABLE : CONTAINER) {
       BODY
     }

.. tabbed:: range_for_loop_tabbed

   .. tab:: range for loop

      .. activecode:: for_loops_AC_3
         :language: cpp

         In C++, this is called a :lang:`range-for` loop.
         In other languages, this is sometimes called a *for each* loop.
         The idea is that the for loop knows how to get each element out of
         the provided container one at a time and assign it to a variable.
         ~~~~
         #include <iostream>
         #include <string>

         int main() {
         std::string words = "The rain in Spain falls mainly on the plain.";
             for (char letter : words) {
                 std::cout << letter << ' ';
             }
         }

.. admonition::  Try This!

   In the code lens, change the range-for syntax to a traditional loop
   and see what changes.

   Can you remember what happens if you change
   ``char letter` to ``int letter``? Try it out.

The range-for loop introduced in C++11 was a great addition to the language.
It improves readability and simplifies code.
It is less error prone and does not require a separate index variable.

The :lang:`range-for` loop, while convenient, has limitations.

Any situation in which you do not need or want to visit every element
requires a traditional loop:

.. code-block:: cpp

   for (int i=max; i>0; i/=2) {
     // do something with i . . .
   }

Similarly, if you need to iterate through multiple containers in a single loop,
possibly at different rates, then you need a traditional for loop:

.. code-block:: cpp

   for (int i=max, j=0; i>0; i/=2, j++) {
     // do something with i and j . . .
   }

These special cases excepted, range-for loops are preferred in cases
where they make sense.

.. tabbed:: self_check

   .. tab:: Q1

      .. fillintheblank:: for_loops_1

          How many times would the following loop execute?  ``for (int i = 1; i < 4; i++)``

          - :3: Correct!
            :4: Incorrect! The loop does not execute when i = 4.
            :.*: Incorrect!

   .. tab:: Q2

      .. mchoice:: for_loops_2
         :answer_a: in the BODIES of both loops
         :answer_b: in the BODY of a for loop, and in the statement of a while loop
         :answer_c: in the statement of a for loop, and in the BODY of a while loop
         :answer_d: in the statements of both loops
         :correct: c
         :feedback_a: Incorrect!
         :feedback_b: Incorrect!
         :feedback_c: Correct!
         :feedback_d: Incorrect!

         Where are the incrementors in ``for`` loops and ``while``?

   .. tab:: Q3

      .. parsonsprob:: question10_4_3
         :numbered: left
         :adaptive:

         Construct the <code>half_life()</code> function that prints the first num half lives
         of the initial amount.
         -----
         void half_life(int initial_amount, int num) {
         =====
         int half_life(int initial_amount, int num) {                         #paired
         =====
            int new_amount = initial_amount;
         =====
            for (int i = 0; i &#60; num; ++i) {
         =====
            for (int i = 0; i &#60;= num; ++i) {                         #paired
         =====
               new_amount = new_amount / 2;
         =====
               new_amount / 2;                         #paired
         =====
               cout << new_amount << endl;
         =====
            return new_amount;                         #distractor
         =====
            }
         }

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`for` loop and :lang:`range-for` loops
     - :lang:`while` loop
