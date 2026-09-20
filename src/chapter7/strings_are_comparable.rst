``string``\ s are comparable
----------------------------

All the comparison operators that work on ``int``\ s and ``double``\ s
also work on ``strings``. 

Take a look at the active code below, which checks to see if ``word`` is 
equal to ``"banana"``.

.. tb-code:: cpp
   :name: strings_comparable_AC_1
   :caption: Strings are comparable
   :compileargs: ['-Wall', '-std=c++11']

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

The active code below uses comparison operators to determine the ordering
of ``word`` relative to ``"banana"``.

.. tb-code:: cpp
   :name: strings_comparable_AC_2
   :caption: Strings are comparable
   :compileargs: ['-Wall', '-std=c++11']

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

Print a simple boolean value resulting from a string comparison.

.. tb-code:: cpp
   :name: strings_comparable_AC_3
   :caption: String comparisons print 0 and 1 by default
   :compileargs: ['-Wall', '-std=c++11']

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


The I/O manipluator ``boolalpha`` can display the boolean
values as the words ``true`` or ``false``.

.. tb-code:: cpp
   :name: strings_comparable_AC_4
   :caption: iomanip can change what iostream displays
   :compileargs: ['-Wall', '-std=c++11']

   #include <iomanip>
   #include <iostream>
   #include <string>

   int main() {
     std::string word = "Zebra";
     bool compare = word < "banana";
     std::cout << std::boolalpha << "Comparison: " << compare;
   }



.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: strings_comparable_1

         What would the result of the following comparison be?
         Where ``1`` means true and ``0`` means false.

         .. code-block:: cpp

            "Dog" < "Doghouse";

         - [x] 1

           Both match up to the g but Dog is shorter than Doghouse so it comes first in the dictionary.
         - [ ] 0

           Strings are compared character by character.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: strings_comparable_2

         What would the result of the following comparison be?
         Where ``1`` means true and ``0`` means false.

         .. code-block:: cpp

            "dog" < "Dog";

         - [ ] 1

           d is greater than D
         - [x] 0

           Yes, upper case is less than lower case according to the ordinal values of the characters.
         - [ ] They are the same word

           C++ is case sensitive meaning that upper case and lower case characters are different.

   .. tb-tab:: Q3

      .. tb-choice::
         :name: strings_comparable_3

         What would the result of the following comparison be?
         Where ``1`` means true and ``0`` means false. 

         .. code-block:: cpp

            "dog" < "Doghouse";

         - [ ] 1

           d is greater than D.
         - [x] 0

           The length does not matter.  Lower case d is greater than upper case D.

   .. tb-tab:: Q4

      .. tb-choice::
         :name: strings_comparable_4

         What would the result of the following comparison be?
         Where ``1`` means true and ``0`` means false.

         .. code-block:: cpp

            "bread" < "bread";

         - [ ] 1

           They are equal so one can't be greater than the other.
         - [x] 0

           Correct! because they are equal. They are equal because all characters match.

