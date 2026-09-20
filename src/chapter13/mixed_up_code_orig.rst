.. _objects-vectors-mixed-up-code-practice:

Mixed Up Code Practice
----------------------

.. tb-parsons::
   :name: c192_mucp_13_1
   :no-indent:

   Below is the enumerated type Days which maps days of the week to integers
   starting at 1. Use a switch statement to determine whether or not day
   is a weekend or not. Check for cases in numerical order.

   .. code-block:: c++

      {{group}}
      enum day { mon = 1, tue, wed, thu, fri, sat, sun };
      {{endgroup}}
      {{group}}
      int main () {
      {{endgroup}}
      {{group}}
         day day = sun;
      {{endgroup}}
      {{group}}
         switch (day > 5) {
      {{endgroup}}
      {{group}}
            case 0:
      {{endgroup}}
      {{group}}
               std::cout << "It is not the weekend :(" << '\n';
      {{endgroup}}
      {{group}}
               break;
      {{endgroup}}
      {{group}}
            case 1:
      {{endgroup}}
      {{group}}
               std::cout << "It is the weekend :)" << '\n';
      {{endgroup}}
      {{group}}
               break;
      {{endgroup}}
      {{group}}
            default:
      {{endgroup}}
      {{group}}
               std::cout << "Invalid input." << '\n';
      {{endgroup}}
      {{group}}
               break;
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_13_2
   :no-indent:

   Use a switch statement to check and print out whether a number is divisible by two.
   Prompt and get input from the user. If input isn't valid,
   print out the default statement "Invalid input." Check for cases in numerical order.

   .. code-block:: c++

      {{group}}
      int main () {
      {{endgroup}}
      {{group}}
         int input;
      {{endgroup}}
      {{group}}
         std::cout << "Please enter an integer: ";
      {{endgroup}}
      {{group}}
         std::cin >> input;
      {{endgroup}}
      {{group}}
         switch (input % 2) {
      {{endgroup}}
      {{group}}
            case 0:
      {{endgroup}}
      {{group}}
               std::cout << input << " is even!" << '\n';
      {{endgroup}}
      {{group}}
               break;
      {{endgroup}}
      {{group}}
            case 1:
      {{endgroup}}
      {{group}}
               std::cout << input << " is odd!" << '\n';
      {{endgroup}}
      {{group}}
               break;
      {{endgroup}}
      {{group}}
            default:
      {{endgroup}}
      {{group}}
               std::cout << "Invalid input." << '\n';
      {{endgroup}}
      {{group}}
               break;
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_13_3
   :no-indent:

   Use a switch statement to check and print out the maximum between two numbers.
   Prompt and get input from the user for two integers. If input isn't valid,
   print out the default statement "Invalid input." Check for cases in numerical order.

   .. code-block:: c++

      {{group}}
      int main () {
      {{endgroup}}
      {{group}}
         int input1;
      {{endgroup}}
      {{group}}
         int input2;
      {{endgroup}}
      {{group}}
         std::cout << "Please enter first integer: ";
      {{endgroup}}
      {{group}}
         std::cin >> input1;
      {{endgroup}}
      {{group}}
         std::cout << "Please enter second integer: ";
      {{endgroup}}
      {{group}}
         std::cin >> input2;
      {{endgroup}}
      {{group}}
         switch (input1 > input2) {
      {{endgroup}}
      {{group}}
            case 0:
      {{endgroup}}
      {{group}}
               std::cout << "The maximum is " << input2 << '\n';
      {{endgroup}}
      {{group}}
               break;
      {{endgroup}}
      {{group}}
            case 1:
      {{endgroup}}
      {{group}}
               std::cout << "The maximum is " << input1 << '\n';
      {{endgroup}}
      {{group}}
            default:
      {{endgroup}}
      {{group}}
               std::cout << "Invalid input." << '\n';
      {{endgroup}}
      {{group}}
               break;
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_13_4

   Below is the pseudocode for the implementation of merge_sort.
   Put the blocks in the correct order!

   .. code-block:: c++

      {{group}}
      card_deck card_deck::merge_sort () const {
      {{endgroup}}
      {{distractor}}
      {{group}}
      card_deck::merge_sort () const {  #distractor
      {{endgroup}}
      {{group}}
         find the midpoint of the deck
      {{endgroup}}
      {{group}}
         divide the deck into two subdecks
      {{endgroup}}
      {{group}}
         sort the subdecks using sort
      {{endgroup}}
      {{group}}
         merge the two halves and return the result
      {{endgroup}}
      {{distractor}}
      {{group}}
         use a for loop to traverse half the deck  #distractor
      {{endgroup}}
      {{group}}
         divide each subdeck into two more subdecks
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_13_5

   Let's revisit the dictionary data structure defined in the previous section.
   Write the struct definitions for entry, which has member variables word and page,
   and for dictionary, which has a vector of Entries. Put the necessary
   blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      struct entry {
      {{endgroup}}
      {{group}}
         std::string word;
      {{endgroup}}
      {{group}}
         int page;
      {{endgroup}}
      {{distractor}}
      {{group}}
         entry word;  #distractor
      {{endgroup}}
      {{group}}
      };
      {{endgroup}}
      {{group}}
      struct dictionary {
      {{endgroup}}
      {{group}}
         std::vector<entry> entries;
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::vector<Word> entries;  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         entry entries;  #distractor
      {{endgroup}}
      {{group}}
      };
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_13_6

   Assume our dictionary is currently unsorted. Let's write a dictionary member function find
   that takes a string word as a parameter and returns the index of its corresponding
   entry. If the word isn't in the dictionary, return -1.
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      std::ptrdiff_t dictionary::find (std::string word) {
      {{endgroup}}
      {{distractor}}
      {{group}}
      std::ptrdiff_t dictionary::find (entry word) {
      {{endgroup}}
      {{group}}
         for (std::size_t i = 0; i < entries.size(); ++i) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         for (std::size_t i = 1; i < entries.size(); ++i) {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         for (std::size_t i = 1; i < dictionary.entries.size(); ++i) {  #distractor
      {{endgroup}}
      {{group}}
            if (entries[i].word == word) {
      {{endgroup}}
      {{distractor}}
      {{group}}
            if (i.word == word) {  #distractor
      {{endgroup}}
      {{group}}
               return static_cast<std::ptrdiff_t>(i);
      {{endgroup}}
      {{group}}
            }
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         return -1;
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_13_7

   Of course, all dictionaries are in some sort of order. In order to do this, we
   must first write the dictionary member function find_first_word, which takes a starting
   index as a parameter returns the index of the entry with the highest priority alphabetically
   (i.e. the entry with a word that would come first in the alphabet).
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      std::size_t dictionary::find_first_word (std::size_t start) {
      {{endgroup}}
      {{distractor}}
      {{group}}
      std::size_t dictionary::find_first_word (std::string word) {
      {{endgroup}}
      {{group}}
         std::size_t min = start;
      {{endgroup}}
      {{group}}
         for (std::size_t i = start; i < entries.size(); ++i) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         for (std::size_t i = 0; i < entries.size(); ++i) {  #distractor
      {{endgroup}}
      {{group}}
            if (entries[i].word < entries[min].word) {
      {{endgroup}}
      {{distractor}}
      {{group}}
            if (entries[i].word > entries[min].word) {  #distractor
      {{endgroup}}
      {{group}}
               min = i;
      {{endgroup}}
      {{group}}
            }
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         return min;
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_13_8

   We also need a swap function. Write the dictionary member function
   swap which takes two indices as parameters and swaps the Entries
   at those indices.
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      void dictionary::swap (std::size_t a, std::size_t b) {
      {{endgroup}}
      {{distractor}}
      {{group}}
      void dictionary::swap () {
      {{endgroup}}
      {{group}}
         entry temp = entries[a];
      {{endgroup}}
      {{group}}
         entries[a] = entries[b];
      {{endgroup}}
      {{group}}
         entries[b] = temp;
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_13_9

   Now let's write the dictionary member function alphabetize, which
   sorts the Entries in the dictionary in alphabetical order. Use
   the find_first_word and swap functions we defined earlier!
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      void dictionary::alphabetize () {
      {{endgroup}}
      {{distractor}}
      {{group}}
      int dictionary::alphabetize () {
      {{endgroup}}
      {{group}}
         for (std::size_t i = 0; i < entries.size(); ++i) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         for (std::size_t i = 0; i < entries.size() - 1; ++i) {  #distractor
      {{endgroup}}
      {{group}}
            std::size_t min = find_first_word (i);
      {{endgroup}}
      {{distractor}}
      {{group}}
            std::size_t min = find_first_word (0);  #distractor
      {{endgroup}}
      {{group}}
            std::swap (entries[i], entries[min]);
      {{endgroup}}
      {{distractor}}
      {{group}}
            std::swap (0, min);  #distractor
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_13_10

   Let's check to see if our sorting worked! Write the dictionary
   member function print_dictionary, which prints out the word in each
   entry.
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      void dictionary::print_dictionary () {
      {{endgroup}}
      {{group}}
         for (std::size_t i = 0; i < entries.size(); ++i) {
      {{endgroup}}
      {{group}}
            std::cout << entries[i].word << '\n';
      {{endgroup}}
      {{distractor}}
      {{group}}
            std::cout << entries[i].entry << '\n';  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
            std::cout << entry.word << '\n';  #distractor
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

