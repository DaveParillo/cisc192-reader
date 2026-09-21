.. _objects-vectors-mixed-up-code-exercises:

Mixed-Up Code Exercises
-----------------------

Arrange the following **Mixed-Up Code** exercises to
assess what you have learned in this chapter.

.. _objects-vectors-parsons-exercises:

Parsons exercises
~~~~~~~~~~~~~~~~~

.. tb-parsons::
   :name: c192_cp_13_ac_2_pp

    How long is a year on other planets? Let's write a program that prints out the number of days
    in a year on each planet using a switch statement. These values are, in planetary order,
    88 days, 225 days, 365 days, 687 days, 4333 days, 10759 days, 30687 days, and 60190 days.
    Print out this information in the following format: planet ``planet`` has ``num_days`` number of days in
    a year! Use the lines to construct the code, then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
       enum planet { mercury = 1, venus, earth, mars, jupiter, saturn, uranus, neptune };
      {{endgroup}}
      {{group}}
       int main() {
      {{endgroup}}
      {{group}}
           planet p = venus;
      {{endgroup}}
      {{group}}
           switch (p) {
      {{endgroup}}
      {{group}}
               case 1:
                   std::cout << "planet Mercury has 88 number of days in a year!" << '\n';
                   break;
      {{endgroup}}
      {{group}}
               case 2:
                   std::cout << "planet Venus has 225 number of days in a year!" << '\n';
                   break;
      {{endgroup}}
      {{group}}
               case 3:
                   std::cout << "planet Earth has 365 number of days in a year!" << '\n';
                   break;
      {{endgroup}}
      {{group}}
               case 4:
                   std::cout << "planet Mars has 687 number of days in a year!" << '\n';
                   break;
      {{endgroup}}
      {{group}}
               case 5:
                   std::cout << "planet Jupiter has 4333 number of days in a year!" << '\n';
                   break;
      {{endgroup}}
      {{group}}
               case 6:
                   std::cout << "planet Saturn has 10759 number of days in a year!" << '\n';
                   break;
      {{endgroup}}
      {{group}}
               case 7:
                   std::cout << "planet Uranus has 30687 number of days in a year!" << '\n';
                   break;
      {{endgroup}}
      {{group}}
               case 8:
                   std::cout << "planet Neptune has 60190 number of days in a year!" << '\n';
                   break;
      {{endgroup}}
      {{group}}
           }
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_13_ac_4_pp

    Now let's generate a ``bingo_board``! We want to fill the 25 ``space``\s on the ``bingo_board`` with
    random values from 1 to 75 without repititon. To do this, we'll make a ``vector``
    of numbers from 1 to 75 and shuffle it using the same method as shown in this chapter. Then
    we will select the first 25 values for the 25 spaces on the ``bingo_board``. We will
    do this entire process in multiple steps. First, write the function ``random_int``, which
    generates a random value between low and high, inclusive. Be sure to include the relevant libraries!
    Use the lines to construct the code, then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
       std::size_t random_int(std::size_t low, std::size_t high) {
      {{endgroup}}
      {{group}}
           static std::mt19937 engine(std::random_device{}());
      {{endgroup}}
      {{group}}
           return std::uniform_int_distribution<std::size_t>{low, high}(engine);
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_13_ac_6_pp

    Now that we have the functions ``random_int`` and ``swap_values``, we can write the function
    ``generate_rand_vec``. ``generate_rand_vec`` creates a ``vector`` with values from 1 to 75,
    shuffles it using ``random_int`` and ``swap_values``, and returns the shuffled ``vector``.
    Use the lines to construct the code, then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
       std::vector<int> generate_rand_vec() {
      {{endgroup}}
      {{group}}
          std::vector<int> vec(75);
      {{endgroup}}
      {{group}}
          iota(vec.begin(), vec.end(), 1);
      {{endgroup}}
      {{group}}
          for (std::size_t i = 0; i < vec.size(); ++i) {
      {{endgroup}}
      {{group}}
              std::size_t x = random_int(i, vec.size() - 1);
      {{endgroup}}
      {{group}}
              swap_values(vec, i, x);
      {{endgroup}}
      {{group}}
          }
      {{endgroup}}
      {{group}}
          return vec;
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_13_ac_8_pp

    Let's print out our ``bingo_board``! Write the ``bingo_board`` member function
    ``print_board``. Insert tabs between each value in each row to make the board
    print out neater. Use the lines to construct the code, then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
       void bingo_board::print_board () {
      {{endgroup}}
      {{group}}
           for (std::size_t j = 0; j < board.size(); j++) {
      {{endgroup}}
      {{group}}
               for (std::size_t i = 0; i < board[j].size(); i++) {
      {{endgroup}}
      {{group}}
                   std::cout << board[j][i].value << '\t';
      {{endgroup}}
      {{group}}
               }
      {{endgroup}}
      {{group}}
               std::cout << '\n';
      {{endgroup}}
      {{group}}
           }
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_13_ac_10_pp

    You may have noticed that in some cases, our version of ``bubble_sort`` does
    an unnecessary amount of work. For example, if our ``vector`` was {1, 2, 3, 5, 4},
    ``bubble_sort`` would swap 4 and 5, but then keep going even though our ``vector``
    is already in order! We can save some work by including a ``bool`` called ``is_changed``.
    If we swap values during a pass, we set ``is_changed`` to true. If nothing has been swapped,
    then ``is_changed`` stays false, and we know to break out of the loop since our ``vector``
    is already sorted. Write the function ``fast_bubble_sort``, which is ``bubble_sort`` with this
    modification. Use the lines to construct the code, then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
       void fast_bubble_sort(std::vector<int> &vec) {
      {{endgroup}}
      {{group}}
           bool is_changed = false;
      {{endgroup}}
      {{group}}
           for (std::size_t i = 0; i + 1 < vec.size(); ++i) {
      {{endgroup}}
      {{group}}
               for (std::size_t j = 0; j + 1 < vec.size() - i; ++j) {
      {{endgroup}}
      {{group}}
                   if (vec[j] > vec[j + 1]) {
      {{endgroup}}
      {{group}}
                       swap_values(vec, j, j + 1);
      {{endgroup}}
      {{group}}
                       is_changed = true;
      {{endgroup}}
      {{group}}
                   }
      {{endgroup}}
      {{group}}
                   if (is_changed == false) {
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
      {{group}}
           }
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
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
