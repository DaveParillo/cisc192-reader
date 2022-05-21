Extracting characters from a string
-----------------------------------
.. index::
   pair: string; string extraction

Strings are called "strings" because they are made up of a sequence, or
string, of characters.
Imagine a string of beads, where each character is a bead in the string.


.. graphviz::

   graph char_array {
     fontname = "Bitstream Vera Sans"
     label="Beads on a 'string'"
     node [
        fontname = "Bitstream Vera Sans"
        fontsize = 14
        shape = "circle"
        style=filled
        fillcolor=lightblue
     ]
     
     a -- b -- c -- d -- e -- f -- h -- i -- j -- k [ constraint=false]
   }

The first operation we are going to perform on a
string is to extract one of the characters. C++ uses square brackets
(``[`` and ``]``) for this operation.

.. activecode:: extracting_characters_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Accessing a string character

   Take a look at the active code below. We extract the character
   at index 1 from string ``fruit`` using ``[`` and ``]``.
   ~~~~
   #include <iostream>
   #include <string>

   int main() {
       std::string fruit = "orange";
       char letter = fruit[1];
       std::cout << letter;
   }

The expression ``fruit[1]`` indicates that I want character number 1
from the string named ``fruit``. The result is stored in a ``char``
named ``letter``.
When I output the value of ``letter``, I get a surprise:

::

   r

``r`` is not the first letter of ``"orange"``.
Unless you are a computer scientist.
Programmers (and most programming languages) always start
counting from zero.
The 0th letter (“zeroeth”) of ``"orange"`` is ``o``.
The 1th letter (“oneth”) is ``r`` and the 2th (“twoeth”) letter is
``a``.

.. note::
   In C++, indexing begins at 0!

If you want the zereoth letter of a string, 
then you have to put zero in the square brackets.

.. activecode:: extracting_characters_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Accessing a string character

   The active code below accesses the first character in string ``fruit``.
   ~~~~
   #include <iostream>
   #include <string>

   int main() {
       string fruit = "orange";
       char letter = fruit[0];
       cout << letter << endl;
   }

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: extracting_characters_1
         :practice: T
         :answer_a: 1
         :answer_b: 0
         :answer_c: 2
         :correct: b
         :feedback_a: Don't forget that computer scientists do not start counting at 1!
         :feedback_b: Yes, this would access the letter 'b'.
         :feedback_c: This would access the letter 'k'.


         What would replace the "?" in order to access the letter 'b' in the string below?

         .. code-block:: cpp
            :linenos:

            #include <string>

            int main () {
              std::string bake = "bake a cake!";
              char letter = bake[?];
            }

   .. tab:: Q2

      .. mchoice:: extracting_characters_2
         :practice: T
         :answer_a: lunch
         :answer_b: jello
         :answer_c: lello
         :answer_d: heljo
         :correct: c
         :feedback_a: When we <code>cout</code> a <code>string</code> we print its content not its name.
         :feedback_b: Carefully check which string(s) we are indexing into.
         :feedback_c: Correct! We copy the 'l' from position 3 of "hello" to position 0. 
         :feedback_d: Consider which string(s) we are indexing into. 


         What is printed when the code below is run?

         .. code-block:: cpp
            :linenos:

            #include <iostream>
            #include <string>

            int main () {
              std::string lunch = "hello";
              std::string person = "deejay";
              lunch[0] = lunch[3];
              std::cout << lunch;
            }

   .. tab:: Q3

      .. clickablearea:: extracting_characters_3
          :question: Click on each spot where a character in a string is accessed.
          :iscode:
          :feedback: Remember, square brackets [] are used to access a character in a string.

          :click-incorrect:int main() {:endclick:
              :click-incorrect:string fruit = "apple";:endclick:
              char letter = :click-correct:fruit[2];:endclick:
              :click-incorrect:cout << fruit << endl;:endclick:
              cout <<  :click-correct:fruit[4]:endclick:  << endl;
          }


   .. tab:: Q4

      .. parsonsprob:: extracting_characters_4
         :numbered: left
         :adaptive:

         Construct a block of code that correctly prints the letter "a".
         -----
         string x;

         x = "It is warm outside!";

         x = "It is warm outside" #paired

         cout << x[7] << endl;

         cout << x[8] << endl; #distractor

