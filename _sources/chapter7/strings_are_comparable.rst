``string``\ s are comparable
----------------------------

All the comparison operators that work on ``int``\ s and ``double``\ s
also work on ``strings``. 

.. activecode:: strings_comparable_AC_1
   :language: cpp
   :caption: Strings are comparable
 
   Take a look at the active code below, which checks to see if ``word`` is 
   equal to ``"banana"``.
   ~~~~
   #include <iostream>
   #include <string>
 
   int main() {
       std::string word = "banana";
       if (word == "banana") {
           std::cout << "Yes, we have no bananas!\n";
       }
   }

The same rules and limitations that apply to the ``+`` operator
apply to the relational comparison operators.
In order to work correctly, at least one of the operands must
be a ``std::string``.
C strings by themselves are not comparable.
These comparisons work because one of the operands is a ``std::string``.

The other comparison operations are useful for putting words in
alphabetical order.

.. activecode:: strings_comparable_AC_2
   :language: cpp
   :caption: Strings are comparable
 
   The active code below uses comparison operators to determine the ordering
   of ``word`` relative to ``"banana"``.
   ~~~~
   #include <iostream>
   #include <string>
 
   int main() {
 
     std::string word = "Zebra";
     using std::cout;
 
     if (word < "banana") {
       cout << "Your word, " << word << ", comes before banana.\n";
     } else if (word > "banana") {
       cout << "Your word, " << word << ", comes after banana.\n";
     } else {
       cout << "Yes, we have no bananas!\n";
     }
   }

You should be aware, though, that the ``string`` class does not handle
upper and lower case letters the same way that people do. All the upper
case letters come before all the lower case letters. As a result,

::

   Your word, Zebra, comes before banana.

A common way to address this problem is to convert strings to a standard
format, like all lower-case, before performing the comparison. The next
sections explains how. I will not address the more difficult problem,
which is making the program realize that zebras are not fruit.


Sometimes we want to print the result of a comparison operation.
When we use ``cout`` to print the value, we don't get what we expect.

.. activecode:: strings_comparable_AC_3
   :language: cpp
   :caption: String comparisons print 0 and 1 by default
 
   Print a simple boolean value resulting from a string comparison.
   ~~~~
   #include <iostream>
   #include <string>
 
   int main() {
     std::string word = "Zebra";
     bool compare = word < "banana";
     std::cout << "Comparison: " << compare;
   }

The ``bool`` value is actually getting converted to an integer
when processed by the ``cout`` class.

In order to get the results we expect, we need to use the
*input / output manipulation* library: ``iomanip``.


.. activecode:: strings_comparable_AC_4
   :language: cpp
   :caption: iomanip can change what iostream displays
 
   The I/O manipluator ``boolalpha`` can display the boolean
   values as the words ``true`` or ``false``.
   ~~~~
   #include <iomanip>
   #include <iostream>
   #include <string>
 
   int main() {
     std::string word = "Zebra";
     bool compare = word < "banana";
     std::cout << std::boolalpha << "Comparison: " << compare;
   }



.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: strings_comparable_1
         :practice: T
         :answer_a: true
         :answer_b: false
         :correct: a
         :feedback_a: Both match up to the g but Dog is shorter than Doghouse so it comes first in the dictionary.
         :feedback_b: Strings are compared character by character.

         What would the result of the following comparison be?

         .. code-block:: cpp

            std::string a = "Dog";
            std::string b = "Doghouse";
            a < b;

   .. tab:: Q2

      .. mchoice:: strings_comparable_2
         :practice: T
         :answer_a: true
         :answer_b: false
         :answer_c: They are the same word
         :correct: b
         :feedback_a: d is greater than D
         :feedback_b: Yes, upper case is less than lower case according to the ordinal values of the characters.
         :feedback_c: C++ is case sensitive meaning that upper case and lower case characters are different.

         What would the result of the following comparison be?

         .. code-block:: cpp

            std::string a = "dog";
            std::string b = "Dog";
            a < b;


   .. tab:: Q3

      .. mchoice:: strings_comparable_3
         :practice: T
         :answer_a: true
         :answer_b: false
         :correct: b
         :feedback_a: d is greater than D.
         :feedback_b: The length does not matter.  Lower case d is greater than upper case D.

         What would the result of the following comparison be?

         .. code-block:: cpp

            std::string a = "dog";
            std::string b = "Doghouse";
            a < b;



   .. tab:: Q4

      .. mchoice:: strings_comparable_4
         :practice: T
         :answer_a: true
         :answer_b: false
         :correct: b
         :feedback_a: They are equal so one can't be greater than the other.
         :feedback_b: Correct! because they are equal. They are equal because all characters match. 

         What would the result of the following comparison be?

         .. code-block:: cpp

            std::string a = "bread";
            std::string b = "bread";
            a < b;




