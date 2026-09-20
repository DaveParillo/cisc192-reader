.. _fruitful-functions-logical-operators:

Logical operators
-----------------
.. index::
   single: logical operators 

There are three :lang:`logical operators <operator_logical>` in C++:
AND, OR, and NOT, which are normally denoted by the symbols
``&&``, ``||`` and ``!``.
The semantics (meaning) of these operators is similar to their meaning in English. 
For example ``x > 0 && x < 10`` is true only if ``x`` 
is greater than zero AND less than 10.

``even || n%3 == 0`` is true if *either* of the conditions is true,
that is, if the bool variable even is true OR the number is divisible by 3.

Finally, the NOT operator has the effect of negating or inverting a bool
expression, so ``!even`` is true if even is false; that is, if the
number is odd.

Logical operators often provide a way to simplify nested conditional
statements.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: logical_op_1

         Multiple Response: How could you re-write the following code using a single conditional?

         ::

            if (x > 0) {
              if (x < 10) {
                cout << "x is a positive single digit" << '\n';
              }
            }

         - [x] if (x > 0 && x < 10) {...

           This is exactly what the nested conditionals are saying.
         - [ ] if (x > 0 || x < 10) {...

           || represents "or", but we need both sides of the conditional to be true.
         - [ ] if (x > 0 ! x < 10) {...

           The ! operator cannot be used to compare two sides of a conditional.
         - [ ] if ( !(x < 0) && !(x > 10) ) {...

           If x = 0 or if x = 10, this expression will return true when it shouldn't.
         - [x] if ( !(x <= 0) && !(x >= 10) ) {...

           If it IS NOT what we don't want, then it IS what we want!

   .. tb-tab:: Q2

      .. tb-match::
         :name: logical_op_2

         Match the conditional statement to the correct boolean and the meaning of the operator in use, given n = 7.

         (n * 2 > 10 && n >= 7)
            true, "and"
         (n * 2 > 10 && n < 7)
            false, "and"
         (n%2 == 1 || n == 8)
            true, "or"
         (n%2 == 0 || n == 8)
            false, "or"
         !(n == 7)
            false, "not"
         !(n >= 10)
            true, "not"

   .. tb-tab:: Q3

      .. tb-blank::
         :name: logical_op_3

         Add a single logical operator to make the expression check if x is greater than or equal to 50
          {{blank}} ( x < 50 )

         .. tb-answer::
            :match: !
            :feedback: If the expression checks for the opposite of what you want then just ``!`` the result
            :incorrect: Try again!

-----

.. admonition:: More to Explore

   - :lang:`logical operators <operator_logical>` from cppreference

