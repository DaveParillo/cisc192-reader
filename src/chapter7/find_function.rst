The ``find`` function
---------------------

The ``string`` class provides several other functions that you can
invoke on strings. 
The ``find`` function is like the opposite of the ``[]`` operator.
Instead of taking an index and extracting the character at that index, 
``find`` takes a character and finds the index where that character appears.


Take a look at the active code below, which uses the ``find`` function to find
the character ``'a'`` in string ``fruit`` and string ``dessert``.

.. tb-code:: cpp
   :name: find_function_AC_1
   :caption: The find function
   :compileargs: ['-Wall', '-std=c++11']

   #include <cstddef>
   #include <iostream>
   #include <string>

   using std::size_t;

   int main() {
       std::string fruit = "banana";
       std::size_t index = fruit.find('a');
       std::cout << index << '\n';
       std::string dessert = "pudding";
       std::size_t another_index = dessert.find('a');
       if (another_index == std::string::npos) {
           std::cout << "not found\n";
       } else {
           std::cout << another_index << '\n';
       }
   }

This example finds the index of the letter ``'a'`` in the string. In
this case, the letter appears three times, so it is not obvious what
``find`` should do. 
According to the documentation, 
it returns the index of the *first* appearance, 
so the result is 1. If the given letter does not appear in the string, 
``find`` returns the special value ``std::string::npos``,
which is a number larger than any valid position in a string. Store the
result in ``std::size_t`` and compare it with ``std::string::npos`` before
using it as an index. The second search prints ``not found``.

In addition, there is a version of ``find`` that takes another
``string`` as an argument and that finds the index where the substring
appears in the string. 

The active code below finds the starting index of ``"nan"`` in ``fruit``.

.. tb-code:: cpp
   :name: find_function_AC_2
   :caption: The find function
   :compileargs: ['-Wall', '-std=c++11']

   #include <cstddef>
   #include <iostream>
   #include <string>

   using std::size_t;

   int main() {
       std::string fruit = "banana";
       std::size_t index = fruit.find("nan");
       std::cout << index;
   }

This example returns the value 2.

You should remember from Section `[overloading] <#overloading>`__ that
there can be more than one function with the same name, as long as they
take a different number of parameters or different types. In this case,
C++ knows which version of ``find`` to invoke by looking at the type of
the argument we provide.


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-click::
         :name: find_function_1

         Click on the name of each variable that had been initialized with the value of 0.

         .. code-block:: cpp

            int main() {
                string fruit = "apple";
                std::size_t index_a = fruit.find('e');
                std::size_t index_b = fruit.find("app");
                std::size_t index_c = fruit.find('a');
                std::size_t index_d = fruit.find('l');
            }


         .. tb-miss:: text:int main() {

            Remember that the index of a string begins at 0, not 1.

         .. tb-miss:: text:string fruit = "apple";

            Remember that the index of a string begins at 0, not 1.

         .. tb-miss:: text:index_a

            Remember that the index of a string begins at 0, not 1.

         .. tb-hit:: text:index_b

            Correct.

         .. tb-hit:: text:index_c

            Correct.

         .. tb-miss:: text:index_d

            Remember that the index of a string begins at 0, not 1.

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: find_function_2

         Construct a block of code that correctly finds and prints where the first "B" is in the string. Declare ``city`` before ``index``.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               string city = "New Baltimore";
            {{endgroup}}
            {{distractor}}
            {{group}}
               string city = "New Baltimore" #distractor
            {{endgroup}}
            {{group}}
               std::size_t index;
            {{endgroup}}
            {{group}}
               index = city.find('B');
            {{endgroup}}
            {{distractor}}
            {{group}}
               index = city.find(B); #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               index = city.find('b'); #distractor
            {{endgroup}}
            {{group}}
               cout << index << endl;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-choice::
         :name: find_function_3

         What is printed when the code is run?

         .. code-block:: cpp

            string sentence = "Most seas are rough but this sea is so calm!";
            string target = "sea";
            size_t index = sentence.find(target);
            cout << "Index to find sea is " << index << endl;

         - Index to find sea is 29

           - ``find`` returns the index of the *first* occurence of "sea".

         - Index to find sea is 5

           + Correct! ``index`` only has to look for a sequence arranged as "sea" in the string.

         - Index to find sea is ``string::npos``

           - "sea" is present in the ``sentence`` string.

         - [ ] Index to find sea is 29

           <code>find</code> returns the index of the FIRST occurence of "sea".
         - [x] Index to find sea is 5

           Correct! <code>index</code> only has to look for a sequence arranged as "sea" in the string.
         - [ ] Index to find sea is -1

           sea is present in the <code>sentence</code>.

