Traversal
---------
.. index::
   single: traversal

A common thing to do with a string is start at the beginning, select
each character in turn, do something to it, and continue until the end.
This pattern of processing is called a **traversal**. A natural way to
encode a traversal is with a ``while`` statement.

The active code below outputs each letter of string ``fruit``
using a while loop.

.. tb-code:: cpp
   :name: traversal_AC_1
   :caption: Accessing a string character
   :compileargs: ['-Wall', '-std=c++11']

   #include <cstddef>
   #include <iostream>
   #include <string>

   using std::size_t;

   int main() {
       std::size_t index = 0;
       std::string fruit = "apple";
       while (index < fruit.size()) {
           char letter = fruit[index];
           std::cout << letter << '\n';
           index = index + 1;
       }
   }

This loop traverses the string and outputs each letter on a line by
itself. Notice that the condition is ``index < fruit.size()``, which
means that when ``index`` is equal to the length of the string, the
condition is false and the body of the loop is not executed. The last
character we access is the one with the index ``fruit.size()-1``.

.. index::
   single: index

The name of the loop variable is ``index``. An **index** is a variable
or value used to specify one member of an ordered set, in this case the
set of characters in the string. The index indicates (hence the name)
which one you want. The set has to be ordered so that each letter has an
index and each index refers to a single character.

As an exercise, write a function that takes a ``string`` as an argument
and that outputs the letters backwards, all on one line.

Try writing the ``reverse_word`` function in the commented section
of the active code below. If done correctly, the program outputs "olleh".
If you get stuck, you can reveal the extra problem at the end for help. 

.. tb-code:: cpp
   :name: traversal_AC_2
   :caption: Example traversal_AC_2
   :compileargs: ['-Wall', '-std=c++11']

   #include <cstddef>
   #include <iostream>
   #include <string>
   using std::size_t;

   void reverse_word (std::string word) {
       // ``reverse_word`` should take the letters of ``word``
       // and output them in reverse.
   }

   int main() {
       reverse_word("hello");
   }

.. tb-reveal:: Reveal Problem
   :name: id_7_5_1

   .. tb-parsons::
      :name: traversal_1

      Let's write the code for the ``reverse_word`` function. ``reverse_word``
      should take a string as a parameter and output the letters backwards.

      .. code-block:: cpp

         {{group}}
         void reverse_word (string input) {
         {{endgroup}}
         {{group}}
           std::size_t x = input.size();
         {{endgroup}}
         {{distractor}}
         {{group}}
           std::size_t x = input.size() - 1;
         {{endgroup}}
         {{group}}
           while (x > 0) {
         {{endgroup}}
         {{distractor}}
         {{group}}
           while (x >= 0) {
         {{endgroup}}
         {{group}}
             x = x - 1;
             std::cout << input[x];
           }
         }
         {{endgroup}}
         {{distractor}}
         {{group}}
             x = x + 1;
             std::cout << input[x];
           }
         } #distractor
         {{endgroup}}

Start at the size and subtract one **before** accessing a character. This
also handles an empty string: the loop never starts. An unsigned index
cannot become negative, so ``x >= 0`` cannot terminate this loop.


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: traversal_2

         How many times is the letter o printed by the following statements?

         .. code-block:: cpp

            string s = "coding rocks";
            size_t i = 1;
            while (i < s.length()) {
              cout << s[i] << endl;
              i = i + 2;
            }

         - [ ] 0

           i goes through the odd numbers starting at 1.
         - [x] 1

           Yes, i goes through the odd numbers starting at 1.  o is at position 1 and 8.
         - [ ] 2

           There are 2 o characters but idx does not take on the correct index values for both.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: traversal_3

         What is printed when the code is run?

         .. code-block:: cpp

            string truth = "engr101";
            size_t index = 0;
            int counter = 0;
            while (index < truth.length()) {
              cout << truth[index] << " ";
              index = index + counter;
              counter = counter + 1;
            }

         - [x] e e n r 1

           Correct! the values of index are 0 0 1 3 6. After this while loop ends.
         - [ ] e e e e e

           We are updating the value of of <code>index</code>. Not doing so would make it an infinte loop!
         - [ ] e e n r

           Recalculate the values of <code>index</code> at each stage and consider which ones are &lt 7.
