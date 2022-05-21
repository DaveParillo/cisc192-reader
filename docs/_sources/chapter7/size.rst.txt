String size
-----------

To find the size (or length) of a string (number of characters), we can use the
``size`` function. The syntax for calling this function is a little
different from what we've seen before.

.. activecode:: length_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Finding the size of a string

   The active code below outputs the size of string ``fruit``.
   ~~~~
   #include <iostream>
   #include <string>

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
``()``. The return value is an integer, in this case 6. 

To find the last letter of a string, you might be tempted to try
something like

::

     int size = fruit.size();
     char last = fruit[size];       // WRONG!!

That won’t work. The reason is that there is no 6th letter in
``"banana"``. Since we started counting at 0, the 6 letters are numbered
from 0 to 5. To get the last character, you have to subtract 1 from
``size``.

.. warning::
   A common source of error involving strings and other arrays is indexing
   out of bounds. This is usually the result of forgetting to subtract 1 from
   ``size``.

.. activecode:: length_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Finding the size of a string and outputting it

   The active code below outputs the last character in string ``fruit``
   using the ``size`` function.
   ~~~~
   #include <iostream>
   #include <string>
 
   int main() {
       std::string fruit = "Watermelon";
       int size = fruit.size();
       char last = fruit[size-1];
       std::cout << last;
   }

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: length_1
         :practice: T
         :answer_a: 11
         :answer_b: 12
         :correct: b
         :feedback_a: The space counts as a character.
         :feedback_b: Yes, there are 12 characters in the string.


         What is printed by the following statements?

         .. code-block:: cpp

            string s = "coding rocks";
            cout << s.size();

   .. tab:: Q2

      .. mchoice:: length_2
         :practice: T
         :answer_a: o
         :answer_b: r
         :answer_c: s
         :answer_d: Error, s.size() is 12 and there is no index 12.
         :correct: b
         :feedback_a: Take a look at the index calculation again, s.size()-5.
         :feedback_b: Yes, s.size() is 12 and 12-5 is 7.  Use 7 as index and remember to start counting with 0.
         :feedback_c: s is at index 11.
         :feedback_d: You subtract 5 before using the index operator so it will work.


         What is printed by the following statements?

         .. code-block:: cpp

            string s = "coding rocks";
            cout << (s[s.size()-5]);

   .. tab:: Q3


      .. parsonsprob:: length_3
         :numbered: left
         :adaptive:

         Construct a block of code that correctly implements the accumulator pattern, with ``course`` being the first variable initialized.
         -----
         int main() {

            string course = "Programming";

            int num_chars;

            string num_chars; #distractor

            num_chars = course.size();

            num_chars = length(course); #distractor

            cout << num_chars << endl;

         }


