.. _variables-types-operators-for-characters:

Operators for Characters
------------------------

Interestingly, the same mathematical operations that work on integers
also work on characters. For example, observe the following output.

This program performs character addition.  It works because the
character ``a`` is actually stored as the number ``97``!
The value '97' is the way 'a' is represented in the ASCII
character set.
ASCII is common, but there are many others.

``cout`` 'knows' that when the type is ``char``, it should
print the character representation and not the actual
numeric value.

.. tb-code:: cpp
   :name: char_operations_AC_1
   :caption: Adding to Characters

   #include <iostream>

   int main () {
       char letter = 'a' + 1;
       std::cout << letter;
   }

Although it is syntactically legal to multiply characters, it is almost never
useful to do it.

Earlier I said that you can only assign integer values to integer
variables and character values to character variables, but that is not
completely true. In some cases, C++ converts automatically between
types. For example, the following is legal.

This program performs automatic type converstion.  It converts 'a' 
to its ASCII value.

.. tb-code:: cpp
   :name: char_operations_AC_2
   :caption: Automatic Type Conversion

   #include <iostream>
   int main () {
       int number = 'a';
       std::cout << number;
   }

It is generally a good idea to treat
characters as characters, and integers as integers, and only convert
from one to the other if there is a good reason.

.. index::
   single: ASCII

.. note::
   Characters in C++ hold :lang:`ASCII <ascii>` values,
   which range from 0 to 127.
   Uppercase 'A' has an ASCII value of 65, lowercase 'a' has a value of 97,
   and a space has a value of 32.
   C++ converts characters to their ASCII values to 
   perform automatic type conversion and character arithmetic.


Automatic type conversion is an example of a common problem in designing
a programming language, which is that there is a conflict between
**formalism**, which is the requirement that formal languages should
have simple rules with few exceptions, and **convenience**, which is the
requirement that programming languages be easy to use in practice.

More often than not, convenience wins, which is usually good for expert
programmers, who are spared from rigorous but unwieldy formalism, but
bad for beginning programmers, who are often baffled by the complexity
of the rules and the number of exceptions. In this book I have tried to
simplify things by emphasizing the rules and omitting many of the
exceptions.


.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-blank::
         :name: char_operations_1

         What is the value of letter if ``letter = 'c' + 3``?

         {{blank}}

         .. tb-answer::
            :match: f
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: char_operations_2

         Construct a main function that uses character operations to generate the output 'r'.

         .. code-block:: cpp

            {{group}}
            int main () {
            {{endgroup}}
            {{group}}
             char r;
            {{endgroup}}
            {{distractor}}
            {{group}}
             int r; #distractor
            {{endgroup}}
            {{group}}
             r = 'p' + 2;
            {{endgroup}}
            {{distractor}}
            {{group}}
             r = p + 2; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             r = 'p' + 3; #distractor
            {{endgroup}}
            {{group}}
             cout << r;
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << 'r'; #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

-----

.. admonition:: More to Explore

   - From cppreference.com

     - C++ :lang:`identifiers` and :lang:`type`
     - :lang:`ASCII <ascii>` character chart


