.. _strings-things-string-variables:

``string`` variables
--------------------
.. index::
   pair: variables; string variables
   pair: string; string variables

You can create a variable with type ``string`` in the usual ways.

In the code below, the first line creates a ``string``
without giving it a value.
The second line assigns it the string value ``"Hello,"``. 
The third line is a combined declaration and assignment,
also called an initialization.

:: 

    std::string first;
    first = "Hello, ";
    std::string second = "world.";

Normally when string values like ``"Hello, "`` or ``"world."`` appear,
they are treated as C strings. In this case, when we assign them to an
``string`` variable, they are converted automatically to ``string``
values.

We can output strings in the usual way:

::

     cout << first << second << '\n';

In order to compile this code, you will have to include the header file
containing the ``string`` definitions to all your source files
that refer to the ``string`` type.

Run the active code below!

.. tb-code:: cpp
   :name: string_variables_AC_2
   :caption: Outputting a string variable

   #include <iostream>
   #include <string>

   int main() {
       std::string first;
       first = "Hello, ";
       std::string second = "world.";
       std::cout << first << second << '\n';
   }

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: string_variables_1

         Construct a block of code that correctly prints out a string variable.

         .. code-block:: cpp

            {{group}}
            std::string x;
            {{endgroup}}
            {{group}}
            x = "It is cold outside!";
            {{endgroup}}
            {{distractor}}
            {{group}}
            x = "It is cold outside"
            {{endgroup}}
            {{group}}
            std::cout << x << '\n';
            {{endgroup}}

   .. tb-tab:: Q2

      .. tb-choice::
         :name: string_variables_2

         How would you initialize a string?


         - [x] string x = "Hello";

           This is the correct way to initialize a string.
         - [ ] x = "Hello";

           This is an assignment.
         - [ ] string x;

           This is a declaration.

   .. tb-tab:: Q3

      .. tb-click::
         :name: string_variables_3

         Click on each spot where a string assignment occurs.

         .. code-block:: cpp

            int main() {
                string fruit;
                fruit = "apple";
                fruit = "pear";
                string flavor = "sweet";
                flavor = "vanilla";
            }


         .. tb-miss:: text:int main() {

            Remember, assignment and initialization are different.

         .. tb-miss:: text:string fruit;

            Remember, assignment and initialization are different.

         .. tb-hit:: text:fruit = "apple";

            Correct.

         .. tb-hit:: text:fruit = "pear";

            Correct.

         .. tb-miss:: text:string flavor = "sweet";

            Remember, assignment and initialization are different.

         .. tb-hit:: text:flavor = "vanilla";

            Correct.

