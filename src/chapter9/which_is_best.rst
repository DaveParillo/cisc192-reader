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

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: which_is_best_1

         What is a functional programming style?

         - [x] Writing modifiers only if there is a compelling advantage. Otherwise, write pure functions.

           Correct!
         - [ ] Writing fill-in functions only if there is a compelling advantage. Otherwise, write modifiers.

           Try again.
         - [ ] Writing pure functions only if there is a compelling advantage. Otherwise, write modifiers.

           Try again.

   .. tb-tab:: Q2

      .. tb-blank::
         :name: which_is_best_2

         Anything that can be done with modifiers and fill-in functions can also be done with ____.

         {{blank}}

         .. tb-answer::
            :regex:
            :match: pure functions
            :feedback: Correct!
            :incorrect: Try again!

