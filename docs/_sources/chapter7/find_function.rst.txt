The ``find`` function
---------------------

The ``string`` class provides several other functions that you can
invoke on strings. 
The ``find`` function is like the opposite of the ``[]`` operator.
Instead of taking an index and extracting the character at that index, 
``find`` takes a character and finds the index where that character appears.


.. activecode:: find_function_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: The find function

   Take a look at the active code below, which uses the ``find`` function to find
   the character ``'a'`` in string ``fruit`` and string ``dessert``.
   ~~~~
   #include <iostream>
   #include <string>
 
   int main() {
       std::string fruit = "banana";
       int index = fruit.find('a');
       std::cout << index << '\n';
       std::string dessert = "pudding";
       int another_index = fruit.find('a');
       std::cout << another_index << '\n';
   }

This example finds the index of the letter ``'a'`` in the string. In
this case, the letter appears three times, so it is not obvious what
``find`` should do. 
According to the documentation, 
it returns the index of the *first* appearance, 
so the result is 1. If the given letter does not appear in the string, 
``find`` returns the special value ``std::string::npos``,
which is a number larger than any valid position in a string.

In addition, there is a version of ``find`` that takes another
``string`` as an argument and that finds the index where the substring
appears in the string. 

.. activecode:: find_function_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: The find function

   The active code below finds the starting index of ``"nan"`` in ``fruit``.
   ~~~~
   #include <iostream>
   #include <string>
 
   int main() {
       std::string fruit = "banana";
       int index = fruit.find("nan");
       std::cout << index;
   }

This example returns the value 2.

You should remember from Section `[overloading] <#overloading>`__ that
there can be more than one function with the same name, as long as they
take a different number of parameters or different types. In this case,
C++ knows which version of ``find`` to invoke by looking at the type of
the argument we provide.


.. tabbed:: self_check

   .. tab:: Q1

      .. clickablearea:: find_function_1
          :question: Click on the name of each variable that had been initialized with the value of 0.
          :iscode:
          :feedback: Remember that the index of a string begins at 0, not 1.

          :click-incorrect:def main() {::endclick:
              :click-incorrect:string fruit = "apple";:endclick:
              int:click-incorrect: index_a :endclick:= fruit.find('e');
              int:click-correct: index_b :endclick:= fruit.find("app");
              int:click-correct: index_c :endclick:= fruit.find('a');
              int:click-incorrect: index_d :endclick:= fruit.find('l');
          }

   .. tab:: Q2

      .. parsonsprob:: find_function_2
         :numbered: left
         :adaptive:

         Construct a block of code that correctly finds and prints where the first "B" is in the string. Declare ``city`` before ``index``.
         -----
         int main() {

            string city = "New Baltimore";

            string city = "New Baltimore" #distractor

            int index;

            index = city.find('B');

            index = city.find(B); #distractor

            index = city.find('b'); #distractor

            cout << index << endl;

         }

   .. tab:: Q3

      .. mchoice:: find_function_3
         :practice: T 
         :answer_a: Index to find sea is 29
         :answer_b: Index to find sea is 5
         :answer_c: Index to find sea is std::string::npos
         :correct: b
         :feedback_a: <code>find</code> returns the index of the FIRST occurence of "sea". 
         :feedback_b: Correct! <code>index</code> only has to look for a sequence arranged as "sea" in the stirng. 
         :feedback_c: sea is present in the <code>sentence</code>.

         What is printed when the code is run?

         .. code-block:: cpp

            string sentence = "Most seas are rough but this sea is so calm!";
            string target = "sea";
            int index = sentence.find(target);
            cout << "Index to find sea is " << index << endl;

