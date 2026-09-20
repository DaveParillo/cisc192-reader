Compound values
---------------
.. index::
   pair: types; compound types

Most of the data types we have been working with represent a single
value—an integer, a floating-point number, a boolean value.
``string``\ s are different in the sense that they are made up of
smaller pieces, the characters. Thus, ``string``\ s are an example of a
**compound** type.

Depending on what we are doing, we may want to treat a compound type as
a single thing (or object), or we may want to access its parts (or
instance variables). This ambiguity is useful.

.. index::
   single: structures
   single: classes

It is also useful to be able to create your own compound values. C++
provides two mechanisms for doing that: **structures** and **classes**.
We will start out with structures and get to classes in
Chapter `[class] <#class>`__ (there is not much difference between
them).

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-blank::
         :name: compound_values_1

         Strings are made up of smaller pieces (the characters). This makes strings an example of a _____ type.

         {{blank}}

         .. tb-answer::
            :regex:
            :match: compound
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q2

      .. tb-blank::
         :name: compound_values_2

         One of the mechanisms for creating your own compound values is structures. What is the other?

         {{blank}}

         .. tb-answer::
            :regex:
            :match: classes
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q3

      .. tb-choice::
         :name: compound_values_3

         Which is different from the others because it is does not represent a single value?

         - [ ] integer

           Try again!
         - [x] string

           Correct!
         - [ ] floating-point number

           Try again!
         - [ ] boolean value

           Try again!

