Which is best?
--------------
.. index::
   single: functional programming languages

.. index::
   single: functional programming language

Anything that can be done with modifiers and fill-in functions can also
be done with pure functions. In fact, there are programming languages,
called **functional** programming languages, that only allow pure
functions. Some programmers believe that programs that use pure
functions are faster to develop and less error-prone than programs that
use modifiers. Nevertheless, there are times when modifiers are
convenient, and cases where functional programs are less efficient.

In general, I recommend that you write pure functions whenever it is
reasonable to do so, and resort to modifiers only if there is a
compelling advantage. This approach might be called a functional
programming style.

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: which_is_best_1
         :answer_a: Writing modifiers only if there is a compelling advantage. Otherwise, write pure functions.
         :answer_b: Writing fill-in functions only if there is a compelling advantage. Otherwise, write modifiers.
         :answer_c: Writing pure functions only if there is a compelling advantage. Otherwise, write modifiers.
         :correct: a
         :feedback_a: Correct!
         :feedback_b: Try again.
         :feedback_c: Try again.

         What is a functional programming style?

   .. tab:: Q2

      .. fillintheblank:: which_is_best_2

          Anything that can be done with modifiers and fill-in functions can also be done with ____.

          - :(?:p|P)ure (?:F|f)unctions: Correct!
            :.*: Try again!
