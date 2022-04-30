Operations on structures
------------------------

Most of the operators we have been using on other types, like
mathematical operators ( ``+``, ``%``, etc.) and comparison operators
(``==``, ``>``, etc.), do not work on structures by default. It is
possible to define the meaning of these operators for the new type, but
we won’t do that in this book.

On the other hand, the assignment operator *does* work for structures.
It can be used in two ways: to initialize the instance variables of a
structure or to copy the instance variables from one structure to
another. An initialization looks like this:

::

     point blank = { 3.0, 4.0 };

The values in curly braces get assigned to the instance variables of
the structure one by one, in order. So in this case, ``x`` gets the
first value and ``y`` gets the second.

.. note::

   Prior to C++11, this syntax can be used only in an initialization, not in
   an assignment statement. So the following is illegal in C++03,
   and is probablly a compile error when using default compiler settings.

   ::

        point blank;
        blank = { 3.0, 4.0 };       // C++11 or later only

   A simple work around exists. If you add a C style typecast:

   ::

        point blank;
        blank = (point){ 3.0, 4.0 };

   That works.

It is legal to assign one structure to another. For example:

::

     point p1 = { 3.0, 4.0 };
     point p2 = p1;
     cout << p2.x << ", " <<  p2.y << endl;

The output of this program is ``3, 4``.

.. tabbed:: self_check

   .. tab:: Q1

      .. clickablearea:: operations_structures_1
          :question: Click on all incorrect statements. Assume C++11 is not available.
          :iscode:
          :feedback: Remember, this syntax can be used only in an initialization, not in an assignment statement.

          :click-incorrect:int main() {:endclick:
              :click-incorrect:point blank = { 3.0, 4.0 };:endclick:
              :click-incorrect:point hello;:endclick:
              :click-correct:hello = { 3.0, 4.0 };:endclick:
              :click-incorrect:point foo;:endclick:
              :click-incorrect:foo = (point){3.0, 4.0};:endclick:
              :click-correct:foo = {3.0, 4.0};:endclick:
          }

   .. tab:: Q2

      .. parsonsprob:: operations_structures_2
         :numbered: left
         :adaptive:

         Construct a block of code that correctly initializes the instance variables of a structure.
         -----
         struct point {
         =====
            double x, y;
         };
         =====
         int main() {
         =====
            point blank;
         =====
            int blank; #distractor
         =====
            blank = (point){ 12.0, 3.2 };
         =====
            blank = (point){ 12.0, 3.2 } #distractor
         =====
            blank = { 12.0, 3.2 }; #distractor
         }

   .. tab:: Q3

      .. mchoice:: operations_structures_3
         :multiple_answers:
         :answer_a: %
         :answer_b: =
         :answer_c: >
         :answer_d: ==
         :answer_e: +
         :correct: a, c, d, e
         :feedback_a: The modulo operator does not work on structures.
         :feedback_b: The assignment operator does work on structures.
         :feedback_c: The greater than operator does not work on structures.
         :feedback_d: The equality operator does not work on structures.
         :feedback_e: The addition operator does not work on structures.

         Which operators do NOT work on structures. Select all that apply.

