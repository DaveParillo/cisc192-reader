Our own version of ``find``
---------------------------

If we are looking for a letter in a ``string``, we may not want to
start at the beginning of the string. One way to generalize the ``find``
function is to write a version that takes an additional parameter—the
index where we should start looking. Here is an implementation of this
function.

::

   int find (string s, char c, int i) {
     while (i<s.length()) {
       if (s[i] == c) return i;
       i = i + 1;
     }
     return -1;
   }

Instead of invoking this function on a ``string``, like the first
version of ``find``, we have to pass the ``string`` as the first
argument. The other arguments are the character we are looking for and
the index where we should start.

.. activecode:: own_version_find_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Our own find function

   In the active code below, we are finding the number of ``'e'`` characters in 
   the "Shepard" part of "German Shepard" using our function. 
   Then we use the built-in ``find`` function to demonstrate how they work differently.
   ~~~~
   #include <iostream>
   #include <string>
 
   int find (std::string s, char c, int i) {
       int length = s.length();
       while (i < length) {
           if (s[i] == c) {
               return i;
           }
           i = i + 1;
       }
       return -1;
   }
 
   int main() {
       std::string dog = "German Shepard";
       int start_shepard = 7;
       std::cout << find(dog, 'e', start_shepard) << '\n';
       std::cout << dog.find('e') << '\n';
   }
 
.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: own_version_find_1
         :practice: T
         :answer_a: 13, -1, 8
         :answer_b: 13, 0, 7
         :answer_c: 13, -1, 0
         :answer_d: 14, -1, 9
         :correct: a
         :feedback_a: Notice how the built-in find function works differently from ours.
         :feedback_b: Remember that when a character isn't found, the function returns -1.
         :feedback_c: Keep in mind that the find function is case sensitive, so "A" is different from "a".
         :feedback_d: Remember that indexing begins at 0 for C++.

         Given the definition of find provided in the previous active code,
         what is the correct output of the code below?

         .. code-block:: cpp

            int main() {
              string quote = "The way to get started is to quit talking and begin doing.";
              cout << find(quote, 't', 11) << ", " << find(quote, 't', 42) << ", " << quote.find('t');
            }

