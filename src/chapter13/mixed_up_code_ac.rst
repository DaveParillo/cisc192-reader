.. _objects-vectors-activecode-exercises:

Activecode Exercises
--------------------

Answer the following **Activecode** questions to assess what you have learned in this chapter.

.. tb-group::
   :name: c192_mucp_13_1_ac

   .. tb-tab:: Question

       Write the enumerated type ``Days`` which maps days of the week to integers
       starting at 1. Use a switch statement to determine whether or not day
       is a weekend or not. Check for cases in numerical order.

      .. tb-code:: cpp
         :name: c192_mucp_13_1_ac_q
         :caption: Example c192_mucp_13_1_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to use a switch statement to classify a day of the week.

      .. tb-code:: cpp
         :name: c192_mucp_13_1_ac_a
         :caption: Example c192_mucp_13_1_ac_a

         #include <iostream>

         enum day { mon = 1, tue, wed, thu, fri, sat, sun };

         int main () {
             day day = sun;
             switch (day > 5) {
                 case 0:
                     std::cout << "It is not the weekend :(" << '\n';
                     break;
                 case 1:
                     std::cout << "It is the weekend :)" << '\n';
                     break;
                 default:
                     std::cout << "Invalid input." << '\n';
                     break;
             }
         }

.. tb-group::
   :name: c192_mucp_13_2_ac

   .. tb-tab:: Question

       Use a switch statement to check and print out whether a number is divisible by two.
       Prompt and get input from the user. If input isn't valid,
       print out the default statement "Invalid input." Check for cases in numerical order.

      .. tb-code:: cpp
         :name: c192_mucp_13_2_ac_q
         :caption: Example c192_mucp_13_2_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to use a switch statement to check and print out whether a number is divisible by
       two.

      .. tb-code:: cpp
         :name: c192_mucp_13_2_ac_a
         :caption: Example c192_mucp_13_2_ac_a

         #include <iostream>
         using std::cout;

         int main () {
             int input;
             cout << "Please enter an integer: ";
             std::cin >> input;
             switch (input % 2) {
                 case 0:
                     cout << input << " is even!" << '\n';
                     break;
                 case 1:
                     cout << input << " is odd!" << '\n';
                     break;
                 default:
                     cout << "Invalid input." << '\n';
                     break;
             }
         }

.. tb-group::
   :name: c192_mucp_13_3_ac

   .. tb-tab:: Question

       Use a switch statement to check and print out the maximum between two numbers.
       Prompt and get input from the user for two integers. If input isn't valid,
       print out the default statement "Invalid input." Check for cases in numerical order.

      .. tb-code:: cpp
         :name: c192_mucp_13_3_ac_q
         :caption: Example c192_mucp_13_3_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to use a switch statement to check and print out the maximum between two numbers.

      .. tb-code:: cpp
         :name: c192_mucp_13_3_ac_a
         :caption: Example c192_mucp_13_3_ac_a

         #include <iostream>
         using std::cout;

         int main () {
             int input1;
             int input2;
             cout << "Please enter first integer: ";
             std::cin >> input1;
             cout << "Please enter second integer: ";
             std::cin >> input2;
             switch (input1 > input2) {
                 case 0:
                     cout << "The maximum is " << input2 << '\n';
                     break;
                 case 1:
                     cout << "The maximum is " << input1 << '\n';
                 default:
                     cout << "Invalid input." << '\n';
                     break;
             }
         }

.. tb-group::
   :name: c192_mucp_13_4_ac

   .. tb-tab:: Question

       Write the pseudocode for the implementation of ``merge_sort``.

      .. tb-code:: cpp
         :name: c192_mucp_13_4_ac_q
         :caption: Example c192_mucp_13_4_ac_q

         // YOUR PSEUDOCODE HERE

   .. tb-tab:: Answer

       Below is one way to write the pseudocode of ``merge_sort``.

      .. tb-code:: cpp
         :name: c192_mucp_13_4_ac_a
         :caption: Example c192_mucp_13_4_ac_a

         // card_deck card_deck::merge_sort () const {
         //     find the midpoint of the deck
         //     divide the deck into two subdecks
         //     sort the subdecks using sort
         //     merge the two halves and return the result
         //     divide each subdeck into two more subdecks
         // }

.. tb-group::
   :name: c192_mucp_13_5_ac

   .. tb-tab:: Question

       Let's revisit the dictionary data structure defined in the previous section.
       Write the struct definitions for ``entry``, which has member variables word and page,
       and for ``dictionary``, which has a vector of Entries.

      .. tb-code:: cpp
         :name: c192_mucp_13_5_ac_q
         :caption: Example c192_mucp_13_5_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the struct definition for ``entry`` and for ``dictionary``.

      .. tb-code:: cpp
         :name: c192_mucp_13_5_ac_a
         :caption: Example c192_mucp_13_5_ac_a

         #include <string>
         #include <iostream>
         #include <vector>

         struct entry {
             std::string word;
             int page;
         };

         struct dictionary {
             std::vector<entry> entries;
         };

.. tb-group::
   :name: c192_mucp_13_6_ac

   .. tb-tab:: Question

       Assume our dictionary is currently unsorted. Let's write a dictionary member function ``find``
       that takes a string word as a parameter and returns the index of its corresponding
       entry. If the word isn't in the dictionary, return -1.

      .. tb-code:: cpp
         :name: c192_mucp_13_6_ac_q
         :caption: Example c192_mucp_13_6_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the dictionary member function.

      .. tb-code:: cpp
         :name: c192_mucp_13_6_ac_a
         :caption: Example c192_mucp_13_6_ac_a

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct entry {
             std::string word;
             int page;
         };

         struct dictionary {
             std::vector<entry> entries;
         public:
             std::ptrdiff_t find(std::string word);
         };

         std::ptrdiff_t dictionary::find (std::string word) {
             for (std::size_t i = 0; i < entries.size(); ++i) {
                 if (entries[i].word == word) {
                     return static_cast<std::ptrdiff_t>(i);
                 }
             }
             return -1;
         }

.. tb-group::
   :name: c192_mucp_13_7_ac

   .. tb-tab:: Question

       Of course, all dictionaries are in some sort of order. In order to do this, we
       must first write the dictionary member function ``find_first_word``, which takes a starting
       index as a parameter returns the index of the entry with the highest priority alphabetically
       (i.e. the entry with a word that would come first in the alphabet).

      .. tb-code:: cpp
         :name: c192_mucp_13_7_ac_q
         :caption: Example c192_mucp_13_7_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``find_first_word`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_13_7_ac_a
         :caption: Example c192_mucp_13_7_ac_a

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct entry {
             std::string word;
             int page;
         };

         struct dictionary {
             std::vector<entry> entries;
         public:
             std::size_t find_first_word(std::size_t start);
         };

         std::size_t dictionary::find_first_word (std::size_t start) {
             std::size_t min = start;
             for (std::size_t i = start; i < entries.size(); ++i) {
                 if (entries[i].word < entries[min].word) {
                     min = i;
                 }
             }
             return min;
         }

.. tb-group::
   :name: c192_mucp_13_8_ac

   .. tb-tab:: Question

       We also need a swap function. Write the dictionary member function
       ``swap`` which takes two indices as parameters and swaps the Entries
       at those indices.

      .. tb-code:: cpp
         :name: c192_mucp_13_8_ac_q
         :caption: Example c192_mucp_13_8_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``swap`` member function

      .. tb-code:: cpp
         :name: c192_mucp_13_8_ac_a
         :caption: Example c192_mucp_13_8_ac_a

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct entry {
             std::string word;
             int page;
         };

         struct dictionary {
             std::vector<entry> entries;
         public:
             void swap(std::size_t a, std::size_t b);
         };

         void dictionary::swap (std::size_t a, std::size_t b) {
             entry temp = entries[a];
             entries[a] = entries[b];
             entries[b] = temp;
         }

.. tb-group::
   :name: c192_mucp_13_9_ac

   .. tb-tab:: Question

       Now let's write the dictionary member function ``alphabetize``, which
       sorts the Entries in the dictionary in alphabetical order. Use
       the ``find_first_word`` and ``swap`` functions we defined earlier!

      .. tb-code:: cpp
         :name: c192_mucp_13_9_ac_q
         :caption: Example c192_mucp_13_9_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the dictionary member function ``alphabetize``.

      .. tb-code:: cpp
         :name: c192_mucp_13_9_ac_a
         :caption: Example c192_mucp_13_9_ac_a

         #include <algorithm>
         #include <cstddef>
         #include <string>
         #include <vector>
         struct entry { std::string word; std::size_t page; };
         struct dictionary {
             std::vector<entry> entries;
             void alphabetize();
             std::size_t find_first_word(std::size_t start) const {
                 std::size_t lowest = start;
                 for (std::size_t i = start; i < entries.size(); ++i) {
                     if (entries[i].word < entries[lowest].word) lowest = i;
                 }
                 return lowest;
             }
         };
         void dictionary::alphabetize() {
             for (std::size_t i = 0; i < entries.size(); ++i) {
                 const std::size_t lowest = find_first_word(i);
                 std::swap(entries[i], entries[lowest]);
             }
         }

.. tb-group::
   :name: c192_mucp_13_10_ac

   .. tb-tab:: Question

       Let's check to see if our sorting worked! Write the dictionary
       member function ``print_dictionary``, which prints out the word in each
       entry.

      .. tb-code:: cpp
         :name: c192_mucp_13_10_ac_q
         :caption: Example c192_mucp_13_10_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the dictionary member function ``print_dictionary``.

      .. tb-code:: cpp
         :name: c192_mucp_13_10_ac_a
         :caption: Example c192_mucp_13_10_ac_a

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct entry {
             std::string word;
             int page;
         };

         struct dictionary {
             std::vector<entry> entries;
         public:
             void print_dictionary();
         };

         void dictionary::print_dictionary () {
             for (std::size_t i = 0; i < entries.size(); ++i) {
                 std::cout << entries[i].word << '\n';
             }
         }

