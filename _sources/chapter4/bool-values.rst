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


.. tabbed:: self_check

   .. tab:: Q1

      .. fillintheblank:: bool_vals_1

          The boolean type has two values |blank| and |blank|.  The |blank|
          operator is used to check if two boolean values are equal.

          - :([Tt][Rr][Uu][Ee]|[Ff][Aa][Ll][Ss][Ee]): Correct!
            :.*: Try again!
          - :([Tt][Rr][Uu][Ee]|[Ff][Aa][Ll][Ss][Ee]): Correct!
            :.*: Try again!
          - :==: Correct!
            :.*: Try again!

   .. tab:: Q2

      .. parsonsprob:: bool_vals_2

         Put the following blocks in order of how large the type is.
         Put the largest type at the top.
         -----
         double
         int
         char
         bool



-----

.. admonition:: More to Explore

   - From cppreference.com

     - C++ :lang:`bool_literal`



