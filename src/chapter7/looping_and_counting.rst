Looping and counting
--------------------

The active code below counts the number of times the letter ``'a'``
appears in a string ``fruit``.

.. tb-code:: cpp
   :name: looping_and_counting_AC_1
   :caption: Looping and counting
   :compileargs: ['-Wall', '-std=c++11']

   #include <cstddef>
   #include <iostream>
   #include <string>

   using std::size_t;

   int main() {
       std::string fruit = "banana";
       std::size_t count = 0;

       std::size_t index = 0;
       while (index < fruit.size()) {
           if (fruit[index] == 'a') {
               count = count + 1;
           }
           index = index + 1;
       }
       std::cout << count;
   }

.. index:: 
   single: counter
   single: increment
   single: decrement

This program demonstrates a common idiom, called a **counter**. The
variable ``count`` is initialized to zero and then incremented each time
we find an ``’a’``. (To **increment** is to increase by one; it is the
opposite of **decrement**, and unrelated to **excrement**, which is a
noun.) When we exit the loop, ``count`` contains the result: the total
number of a’s.


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: looping_counting_1

         What does the following code print?

         .. code-block:: cpp
            :linenos:

            int x = -5;
            while (x < 0) {
              x = x + 1;
              cout << x << ' ';
            }


         - [ ] 5 4 3 2 1

           Notice that x is negative.
         - [ ] -5 -4 -3 -2 -1

           Notice that the value of x is incremented before it is printed.
         - [x] -4 -3 -2 -1 0

           The value of x is incremented before it is printed so the first value printed is -4.

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: looping_counting_2

         As an exercise, encapsulate this code in a function named
         ``count_letter``, and generalize it so that it accepts the string and
         the letter as arguments. In the function, declare count and index in that order.
         Within the main function, declare city and letter in that order.

         .. code-block:: cpp

            {{group}}
            std::size_t count_letter(string s, char letter) {
            {{endgroup}}
            {{group}}
               std::size_t count = 0;
            {{endgroup}}
            {{group}}
               std::size_t index = 0;
            {{endgroup}}
            {{group}}
               while (index < s.size()) {
            {{endgroup}}
            {{group}}
                 if (s[index] == letter) {
            {{endgroup}}
            {{group}}
                   count = count + 1;
                 }
            {{endgroup}}
            {{group}}
                 index = index + 1;
               }
            {{endgroup}}
            {{group}}
               return count;
            }
            {{endgroup}}
            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               string city = "New Baltimore";
            {{endgroup}}
            {{group}}
               char letter = 'e';
            {{endgroup}}
            {{group}}
               cout << count_letter(city, letter);
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: looping_counting_3

         The following is the correct code for printing the even numbers from 0 to 10, but it also includes some extra code that you won't need. Drag the needed blocks from the left and put them in the correct order on the right.

         .. code-block:: cpp

            {{distractor}}
            {{group}}
            x = x + 1; #distractor
            {{endgroup}}
            {{group}}
            x = 0;
            {{endgroup}}
            {{group}}
            while (x <= 10) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            while (x < 10) { #distractor
            {{endgroup}}
            {{group}}
               cout << x << '\n';
            {{endgroup}}
            {{group}}
               x = x + 2;
            }
            {{endgroup}}

   .. tb-tab:: Q4

      .. tb-choice::
         :name: looping_counting_4

         What is the value of ``counter`` right before main returns 0?

         .. code-block:: cpp
            :linenos:

            string word_1 = "understand";
            string word_2 = "underwaa";

            size_t end_1 = word_1.length();
            size_t end_2 = word_2.length();

            if ( end_2 < end_1 ){
               end_1 = end_2;
            }

            size_t index = 0;
            size_t counter = 0;

            while ( index < end_1 ) {
              if ( word_1[index] == word_2[index] ){
                 counter = counter + 1;
              }
              else {
                 counter = counter - 1;
              }
              index = index + 1;
            }

            return 0;

         - [ ] The code dosen't reach ``return 0`` because we index out of bounds in ``word_2``.

           - We set ``end_1`` to be the smaller of the two lengths so we don't index out of bounds.

         - [ ] 2

           - Not all the letters after index 4 differ in the two words.

         - [ ] 3

           - We decrement the value of counter when we don't have matching letters.

         - [x] 4

           + Correct! we have 6 matching letters and 2 differing letters upto the length of ``word_2``.

