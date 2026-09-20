.. _fruitful-functions-boolean-values:

Boolean Values
--------------
..	index::
	  pair: types; bool types

The types we have seen so far are pretty big. There are a lot of
integers in the world, and even more floating-point numbers. By
comparison, the set of characters is pretty small. Well, there is
another type in C++ that is even smaller. It is called **boolean**, and
the only values in it are true and false.

Without thinking about it, we have been using boolean values for the
last couple of chapters. The condition inside an if statement or a while
statement is a boolean expression. Also, the result of a comparison
operator is a boolean value. For example:

::

    if (x == 5) {
      // do something
    }

The operator ``==`` compares two integers and produces a boolean value.

The values true and false are keywords in C++, and can be used anywhere
a boolean expression is called for. For example,

::

    bool is_prime = false;


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-blank::
         :name: bool_vals_1

         The boolean type has two values {{blank:blank1}} and {{blank:blank2}}.  The {{blank:blank3}}
         operator is used to check if two boolean values are equal.

         .. tb-answer:: blank1
            :regex:
            :match: true|false
            :feedback: Correct!
            :incorrect: Try again!

         .. tb-answer:: blank2
            :regex:
            :match: true|false
            :incorrect: Try again!

         .. tb-answer:: blank3
            :match: ==
            :incorrect: Try again!

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: bool_vals_2

         Put the following blocks in order of how large the type is.
         Put the largest type at the top.

         .. code-block:: cpp

            {{group}}
            double
            {{endgroup}}
            {{group}}
            int
            {{endgroup}}
            {{group}}
            char
            {{endgroup}}
            {{group}}
            bool
            {{endgroup}}

-----

.. admonition:: More to Explore

   - From cppreference.com

     - C++ :lang:`bool_literal`



