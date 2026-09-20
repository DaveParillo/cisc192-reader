String size
-----------

To find the size (or length) of a string (number of characters), we can use the
``size`` function. The syntax for calling this function is a little
different from what we've seen before.

The active code below outputs the size of string ``fruit``.

.. tb-code:: cpp
   :name: length_AC_1
   :caption: Finding the size of a string
   :compileargs: ['-Wall', '-std=c++11']

   #include <cstddef>
   #include <iostream>
   #include <string>

   using std::size_t;

   int main() {
       std::string fruit = "Watermelon";
       std::cout << fruit.size();
   }

.. note::
   
   The string class does include a function ``length``
   which does the same thing as ``size``, but in general,
   we will use ``size`` mostly to be consistent with
   other container classes in the C++ Standard Library.

.. index::
   single: invoking

To describe this function call, we would say that we are **invoking**
the size function on the string named ``fruit``. This vocabulary may
seem strange, but we will see many more examples where we invoke a
function on an object. The syntax for function invocation is called “dot
notation,” because the dot (period) separates the name of the object,
``fruit``, from the name of the function, ``size``.

``size`` takes no arguments, as indicated by the empty parentheses
``()``. The return value is an unsigned size type, which we store in ``std::size_t``
when a variable is needed. For ``"Watermelon"``, the size is 10.
Include ``<cstddef>`` and use ``std::size_t`` in a complete program.

To find the last letter of a string, you might be tempted to try
something like

::

     char last = fruit[fruit.size()]; // The null terminator, not the last letter

Reading ``fruit[fruit.size()]`` gives the terminating null character. The
characters of ``"Watermelon"`` have indices 0 through 9. For a nonempty
string, the last character has index ``fruit.size() - 1``.

.. warning::
   Check that a string is not empty before subtracting 1 from its size.
   Sizes are unsigned, so subtracting 1 from zero wraps to a large value;
   it does not produce a valid character index.

The active code below outputs the last character in string ``fruit``
using the ``size`` function.

.. tb-code:: cpp
   :name: length_AC_2
   :caption: Finding the size of a string and outputting it
   :compileargs: ['-Wall', '-std=c++11']

   #include <cstddef>
   #include <iostream>
   #include <string>

   using std::size_t;

   int main() {
       std::string fruit = "Watermelon";
       if (!fruit.empty()) {
           char last = fruit[fruit.size() - 1];
           std::cout << last;
       }
   }

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: length_1

         What is printed by the following statements?

         .. code-block:: cpp

            string s = "coding rocks";
            cout << s.length() << '\n';


         - [ ] 11

           The space counts as a character.
         - [x] 12

           Yes, there are 12 characters in the string.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: length_2

         What is printed by the following statements?

         .. code-block:: cpp

            string s = "coding rocks";
            cout << (s[s.length()-5]) << '\n';


         - [ ] o

           Take a look at the index calculation again, s.length()-5.
         - [x] r

           Yes, s.length() is 12 and 12-5 is 7.  Use 7 as index and remember to start counting with 0.
         - [ ] s

           s is at index 11.
         - [ ] Error, s.length() is 12 and there is no index 12.

           You subtract 5 before using the index operator so it will work.

   .. tb-tab:: Q3


      .. tb-parsons::
         :name: length_3

         Construct a block of code that prints the number of characters in a string, with ``course`` being the first variable initialized.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               string course = "Programming";
            {{endgroup}}
            {{group}}
               std::size_t num_chars;
            {{endgroup}}
            {{distractor}}
            {{group}}
               string num_chars; #distractor
            {{endgroup}}
            {{group}}
               num_chars = course.size();
            {{endgroup}}
            {{distractor}}
            {{group}}
               num_chars = length(course); #distractor
            {{endgroup}}
            {{group}}
               cout << num_chars << '\n';
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

