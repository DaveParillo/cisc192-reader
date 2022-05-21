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

     cout << first << second << endl;

In order to compile this code, you will have to include the header file
containing the ``string`` definitions to all your source files
that refer to the ``string`` type.

.. activecode:: string_variables_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Outputting a string variable

   Run the active code below!
   ~~~~
   #include <iostream>
   #include <string>

   int main() {
       std::string first;
       first = "Hello, ";
       std::string second = "world.";
       std::cout << first << second << '\n';
   }

.. tabbed:: self_check

   .. tab:: Q1

      .. parsonsprob:: string_variables_1
         :numbered: left
         :adaptive:

         Construct a block of code that correctly prints out a string variable.
         -----
         std::string x;

         x = "It is cold outside!";

         x = "It is cold outside" #paired

         std::cout << x << std::endl;

   .. tab:: Q2

      .. mchoice:: string_variables_2
         :practice: T
         :answer_a: string x = "Hello";
         :answer_b: x = "Hello";
         :answer_c: string x;
         :correct: a
         :feedback_a: This is the correct way to initialize a string.
         :feedback_b: This is an assignment.
         :feedback_c: This is a declaration.


         Which statement correctly initializes a string?


   .. tab:: Q3

      .. clickablearea:: string_variables_3
          :question: Click on each spot where a string assignment occurs.
          :iscode:
          :feedback: Remember, assignment and initialization are different.

          :click-incorrect:int main() {:endclick:
              :click-incorrect:string fruit;:endclick:
              :click-correct:fruit = "apple";:endclick:
              :click-correct:fruit = "pear";:endclick:
              :click-incorrect:string flavor = "sweet";:endclick:
              :click-correct:flavor = "vanilla";:endclick:
          }

