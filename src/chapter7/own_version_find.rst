Our own version of ``find``
---------------------------

If we are looking for a letter in a ``string``, we may not want to
start at the beginning of the string. One way to generalize the ``find``
function is to write a version that takes an additional parameter—the
index where we should start looking. Here is an implementation of this
function.

::

   std::size_t find (string s, char c, std::size_t i) {
     while (i < s.size()) {
       if (s[i] == c) return i;
       i = i + 1;
     }
     return std::string::npos;
   }

Instead of invoking this function on a ``string``, like the first
version of ``find``, we have to pass the ``string`` as the first
argument. The other arguments are the character we are looking for and
the index where we should start. Both functions return
``std::string::npos`` if there is no match. Our function also returns
``std::string::npos`` if the starting index is at or beyond the size.

In the active code below, we are finding the index of the first ``'e'`` character in
the "Shepard" part of "German Shepard" using our function. 
Then we use the built-in ``find`` function to demonstrate how the starting index changes the result.

.. tb-code:: cpp
   :name: own_version_find_AC_1
   :caption: Our own find function
   :compileargs: ['-Wall', '-std=c++11']

   #include <cstddef>
   #include <iostream>
   #include <string>

   using std::size_t;

   std::size_t find (std::string s, char c, std::size_t i) {
       while (i < s.size()) {
           if (s[i] == c) {
               return i;
           }
           i = i + 1;
       }
       return std::string::npos;
   }

   int main() {
       std::string dog = "German Shepard";
       std::size_t start_shepard = 7;
       std::cout << find(dog, 'e', start_shepard) << '\n';
       std::cout << dog.find('e') << '\n';
   }

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: own_version_find_1

         en the definition of find provided in the previous active code,
         t is the correct output of the code below?

         code-block:: cpp

         int main() {
           string quote = "The way to get started is to quit talking and begin doing.";
           cout << find(quote, 't', 11) << ", ";
           std::size_t index = find(quote, 't', 42);
           if (index == string::npos) {
               cout << "not found";
           } else {
               cout << index;
           }
           cout << ", " << quote.find('t');
         }

         - [x] 13, not found, 8

           The searches begin at 11, 42, and 0 respectively; no t occurs at or after 42.
         - [ ] 13, not found, 7

           The final search starts at the beginning. Count indices from zero.
         - [ ] 13, not found, 0

           Keep in mind that the find function is case sensitive, so "A" is different from "a".
         - [ ] 14, not found, 9

           Remember that indexing begins at 0 for C++.

