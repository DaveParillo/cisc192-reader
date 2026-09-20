Order of Operations
-------------------

.. index::
   single: precedence
   single: order of operations

When more than one operator appears in an expression the order of
evaluation depends on the rules of **precedence**. A complete
explanation of precedence can get complicated, but just to get you
started:

-  Multiplication and division happen before addition and subtraction.
   So ``2 * 3 - 1`` yields 5, not 4, and ``2 / 3 - 1`` yields -1, not 1 
   (remember that in integer division ``2/3`` is 0).

-  If the operators have the same precedence they are evaluated from
   left to right. So in the expression ``minute * 100 / 60``, the multiplication
   happens first, yielding ``5900 / 60``, which in turn yields 98. If the
   operations had gone from right to left, the result would be 59 * 1
   which is 59, which is wrong.

-  Any time you want to override the rules of precedence (or you are not
   sure what they are) you can use parentheses. Expressions in parentheses 
   are evaluated first, so ``2 * (3 - 1) is 4``. You can also use parentheses 
   to make an expression easier to read, as in ``(minute * 100) / 60``, even 
   though it doesn’t change the result.

Observe the output of the code below to see how the placement of parentheses can change the result of a calculation.

.. tb-code:: cpp
   :name: order_of_operations_AC_1
   :caption: The Role of Parentheses
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>

   int main () {
       std::cout << (2 * 3) - 1 << '\n'
                 << 2 * (3 - 1) << '\n'
                 << 2 / 3 - 1   << '\n'
                 << 2 / (3 -1)  << '\n';
   }


.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-match::
         :name: order_of_operations_1

         Match the expression to its correct output. Don't forget to consider integer 
         division!


         (6*4)+1
            25
         6*(4+1)
            30
         (6/4)+1
            2
         6/(4+1)
            1

   .. tb-tab:: Q2

      .. tb-blank::
         :name: order_of_operations_2

         Any time you want to override the rules of precedence, you can use {{{{blank}}}}.

         .. tb-answer::
            :match: [Pp][Aa][Rr][Ee][Nn][Tt][Hh][Ee][Ss][Ee][Ss]
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q3

      .. note::
         The following module will walk you through an example of the rules of 
         precedence.  Answer the questions in order to check what you remember 
         about the order of operations!


      .. tb-reveal:: Question 3A
         :name: reveal0

         .. tb-click::
            :name: order_of_operations_3A

            Click on ALL PARTS of the expression that get evaluated first.  For example, if "1 + 1" gets evaluated first, click on "1", "+", and "1".

            .. code-block:: cpp

               1 + 2 * ( 10 - 2 ) / 4



            .. tb-miss:: text:1

               Try again!

            .. tb-miss:: text:+

               Try again!

            .. tb-miss:: text:2

               Try again!

            .. tb-miss:: text:*

               Try again!

            .. tb-hit:: text:10

               Correct.

            .. tb-hit:: text:-

               Correct.

            .. tb-hit:: text:2#2

               Correct.

            .. tb-miss:: text:/

               Try again!

            .. tb-miss:: text:4

               Try again!

      Once you've submitted your answer for Question 3A, click on Question 3B below.


      .. tb-reveal:: Question 3B
         :name: reveal1

         .. tb-click::
            :name: order_of_operations_3B

            Click on ALL PARTS of the expression that get evaluated NEXT.  For example, if "1 + 1" gets evaluated first, click on "1", "+", and "1".

            .. code-block:: cpp

               1 + 2 * 8 / 4



            .. tb-miss:: text:1

               Try again!

            .. tb-miss:: text:+

               Try again!

            .. tb-hit:: text:2

               Correct.

            .. tb-hit:: text:*

               Correct.

            .. tb-hit:: text:8

               Correct.

            .. tb-miss:: text:/

               Try again!

            .. tb-miss:: text:4

               Try again!

      Once you've submitted your answer for Question 3B, click on Question 3C below.


      .. tb-reveal:: Question 3C
         :name: reveal2

         .. tb-click::
            :name: order_of_operations_3C

            Click on ALL PARTS of the expression that get evaluated NEXT.  For example, if "1 + 1" gets evaluated first, click on "1", "+", and "1".

            .. code-block:: cpp

               1 + 16 / 4



            .. tb-miss:: text:1

               Try again!

            .. tb-miss:: text:+

               Try again!

            .. tb-hit:: text:16

               Correct.

            .. tb-hit:: text:/

               Correct.

            .. tb-hit:: text:4

               Correct.

      Once you've submitted your answer for Question 3C, click on Question 3D below.


      .. tb-reveal:: Question 3D
         :name: reveal3

         ::

             1 + 5

         is the only operation remaining.  I'm not going to ask you any questions
         about it.  However, it's important that you can wrap you head around the fact that
         the ``+`` operator appeared **first** in the calculation, but it was the **last**
         operator to be evaluated.  The order of operations can be kind of confusing
         at times, but I think you've got a good grasp of the concept!

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Operator precedence <operator_precedence>`
         
