.. _objects-vectors-coding-practice:

Coding Practice
---------------

.. tb-group::
   :name: c192_cp_13_1

   .. tb-tab:: Question

      Create the enumerated type planet, which maps the planets in our solar system to integers
      starting at 1. Make sure to list the planets out in order! (Sadly, Pluto is not a planet :( )

      .. tb-code:: cpp
         :name: c192_cp_13_ac_1q
         :caption: Example c192_cp_13_ac_1q

         #include <iostream>

         // Write your code for the enumerated type planet.

   .. tb-tab:: Answer

      Below is one way to implement the program. The planets in our solar system
      are Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, and Neptune.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_1a
         :caption: Example c192_cp_13_ac_1a

         #include <iostream>

         enum planet { mercury = 1, venus, earth, mars, jupiter, saturn, uranus, neptune };


.. tb-group::
   :name: c192_cp_13_3

   .. tb-tab:: Question

      A Bingo board has 25 Spaces in a matrix-like grid. A space has a number value randomly selected from 1 to 75 and can
      either be filled or not. Write the struct definitions for ``space`` and ``bingo_board``.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_3q
         :caption: Example c192_cp_13_ac_3q

         #include <iostream>
         #include <vector>

         // Write your code for the struct space here.

         // Write your code for the struct bingo_board here.

   .. tb-tab:: Answer

      Below is one way to implement the program. We declare the ``space`` and ``bingo_board`` struct
      and create the instance variables in order. Make sure to set ``is_filled`` to ``false``!

      .. tb-code:: cpp
         :name: c192_cp_13_ac_3a
         :caption: Example c192_cp_13_ac_3a

         #include <iostream>
         #include <vector>

         struct space {
             int value;
             bool is_filled;
         };

         struct bingo_board {
             std::vector<std::vector<space> > board;
         };


.. tb-group::
   :name: c192_cp_13_5

   .. tb-tab:: Question

      Now we need a way to swap the values at two indices in a vector. Write the function ``swap_values``,
      which takes a ``vector`` of ``int``\s and two indices as parameters.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_5q
         :caption: Example c192_cp_13_ac_5q

         #include <iostream>
         #include <vector>

         // Write your code for the swap_values function here.

   .. tb-tab:: Answer

      Below is one way to implement the program. We store the value at ``index1`` in a ``temp``
      variable, replace the value at ``index1`` with the value at ``index2``, and then finally
      replace the value at ``index2`` with the value of ``temp``. Make sure to pass
      ``vec`` by reference!

      .. tb-code:: cpp
         :name: c192_cp_13_ac_5a
         :caption: Example c192_cp_13_ac_5a

         #include <cstddef>
         #include <iostream>
         #include <vector>

         void swap_values (std::vector<int> &vec, std::size_t index1, std::size_t index2) {
             int temp = vec[index1];
             vec[index1] = vec[index2];
             vec[index2] = temp;
         }


.. tb-group::
   :name: c192_cp_13_7

   .. tb-tab:: Question

      We can now fill our ``bingo_board`` with values! Write the ``bingo_board``
      member function ``make_board``. Use the ``generate_rand_vec``
      function and select the first 25 values to fill up the board. Make sure
      to create a free space in the middle of the board! Set the value of the
      free space to 0 and ``is_filled`` to ``true``.  All other
      spaces should have ``is_filled`` set to ``false``.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_7q-support
         :hidden:

         std::size_t random_int(std::size_t low, std::size_t high) {
             static std::mt19937 engine(std::random_device{}());
             return std::uniform_int_distribution<std::size_t>{low, high}(engine);
         }

         void swap_values(std::vector<int> &vec, std::size_t index1, std::size_t index2) {
             int temp = vec[index1];
             vec[index1] = vec[index2];
             vec[index2] = temp;
         }

         std::vector<int> generate_rand_vec() {
             std::vector<int> vec(75);
             iota(vec.begin(), vec.end(), 1);
             for (std::size_t i = 0; i < vec.size(); ++i) {
                 std::size_t m_x = random_int(i, vec.size() - 1);
                 swap_values(vec, i, m_x);
             }
             return vec;
         }


      .. tb-code:: cpp
         :name: c192_cp_13_ac_7q
         :caption: Example c192_cp_13_ac_7q
         :run-after: c192_cp_13_ac_7q-support

         #include <cstddef>
         #include <random>
         #include <iostream>
         #include <vector>
         #include <cstdlib>
         #include <numeric>

         struct space {
             int value;
             bool is_filled;
         };

         struct bingo_board {
             std::vector<std::vector<space> > board;
             void make_board ();
         };

         std::size_t random_int(std::size_t low, std::size_t high);
         void swap_values (std::vector<int> &vec, std::size_t index1, std::size_t index2);
         std::vector<int> generate_rand_vec ();

         // Write your code for the make_board function here.

   .. tb-tab:: Answer

      Below is one way to implement the program. First we need to initialize
      the board to the correct dimensions. Then, we use ``generate_rand_vec``
      to create a ``vector`` of random values from 1 to 75. Afterwards, we set
      the values of the 25 ``space``\s to the first 25 values in the
      random ``vector``. Lastly, we set the middle ``space`` to 0 and
      set its ``is_filled`` to ``true``.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_7a-support
         :hidden:

         std::size_t random_int(std::size_t low, std::size_t high) {
             static std::mt19937 engine(std::random_device{}());
             return std::uniform_int_distribution<std::size_t>{low, high}(engine);
         }

         void swap_values(std::vector<int> &vec, std::size_t index1, std::size_t index2) {
             int temp = vec[index1];
             vec[index1] = vec[index2];
             vec[index2] = temp;
         }

         std::vector<int> generate_rand_vec() {
             std::vector<int> vec(75);
             iota(vec.begin(), vec.end(), 1);
             for (std::size_t i = 0; i < vec.size(); ++i) {
                 std::size_t m_x = random_int(i, vec.size() - 1);
                 swap_values(vec, i, m_x);
             }
             return vec;
         }


      .. tb-code:: cpp
         :name: c192_cp_13_ac_7a
         :caption: Example c192_cp_13_ac_7a
         :run-after: c192_cp_13_ac_7a-support

         #include <cstddef>
         #include <random>
         #include <iostream>
         #include <vector>
         #include <cstdlib>
         #include <numeric>

         struct space {
             int value;
             bool is_filled;
         };

         struct bingo_board {
             std::vector<std::vector<space> > board;
             void make_board ();
         };

         std::size_t random_int(std::size_t low, std::size_t high);
         void swap_values (std::vector<int> &vec, std::size_t index1, std::size_t index2);
         std::vector<int> generate_rand_vec ();

         void bingo_board::make_board() {
             // Initialize board
             space s = {0, false};
             std::vector<space> cols(5, s);
             for (std::size_t i = 0; i < 5; ++i) {
                 board.push_back(cols);
             }

             // Fill board with random values
             std::vector<int> vec = generate_rand_vec();
             std::size_t count = 0;
             for (std::size_t row = 0; row < board.size(); ++row) {
                 for (std::size_t col = 0; col < board[row].size(); ++col) {
                 board[row][col].value = vec[count];
                 ++count;
                 }
             }

             // Create free space
             board[2][2].value = 0;
             board[2][2].is_filled = true;
         }


.. tb-group::
   :name: c192_cp_13_9

   .. tb-tab:: Question

      Bubble sort is a method of sorting that involves repeatedly swapping the
      adjacent elements if they are in the wrong order. For example, let's say
      we have the ``vector`` with elements {3, 2, 4, 1}. On the first pass, we take
      a look at the first two elements, 3 and 2. Since 3 is bigger than 2, we swap them.
      Thus, the ``vector`` now looks like {2, 3, 4, 1}. Next, we look at the next two
      elements, 3 and 4. Since 3 is less than 4, we don't swap. Lastly, we look at
      the last two elements, 4 and 1. Since 4 is greater than 1, we swap the.
      Thus the ``vector`` now looks like {2, 3, 1, 4}. Now we restart and look at the
      first two elements again and the process continues. This way, the biggest elements
      "bubble" to the back. Write the function ``bubble_sort``,
      which takes a ``vector`` as a parameter and sorts it. Feel free to use the provided
      ``swap_values`` function.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_9q
         :caption: Example c192_cp_13_ac_9q

         #include <cstddef>
         #include <iostream>
         #include <vector>

         void swap_values(std::vector<int> &vec, std::size_t index1, std::size_t index2) {
             int temp = vec[index1];
             vec[index1] = vec[index2];
             vec[index2] = temp;
         }

         // Write your code for the bubble_sort function here.

         int main() {
             std::vector<int> vec = { 5, 1, 4, 2, 8 };
             bubble_sort (vec);
             for (std::size_t i = 0; i < vec.size(); ++i) {
                 std::cout << vec[i] << ' ';
             }
         }

   .. tb-tab:: Answer

      Below is one way to implement the program. We must loop through all elements
      in the vector. Since we know the last ``i`` elements are already in place,
      our inner loop only goes up to ``vec.size() - 1 - i``. If the next element
      is greater than the current element, we swap the two elements.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_9a
         :caption: Example c192_cp_13_ac_9a

         #include <cstddef>
         #include <iostream>
         #include <vector>

         void swap_values(std::vector<int> &vec, std::size_t index1, std::size_t index2) {
             int temp = vec[index1];
             vec[index1] = vec[index2];
             vec[index2] = temp;
         }

         void bubble_sort(std::vector<int> &vec) {
             for (std::size_t i = 0; i + 1 < vec.size(); ++i) {
                 for (std::size_t j = 0; j + 1 < vec.size() - i; ++j) {
                     if (vec[j] > vec[j + 1]) {
                         swap_values(vec, j, j + 1);
                     }
                 }
             }
         }

         int main() {
             std::vector<int> vec = { 5, 1, 4, 2, 8 };
             bubble_sort (vec);
             for (std::size_t i = 0; i < vec.size(); ++i) {
                 std::cout << vec[i] << ' ';
             }
         }

.. _objects-vectors-additional-coding-exercises:

Additional coding exercises
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. tb-group::
   :name: c192_cp_13_ac_2_q

   .. tb-tab:: Question

       How long is a year on other planets? Let's write a program that prints out the number of days
       in a year on each planet using a switch statement. These values are, in planetary order,
       88 days, 225 days, 365 days, 687 days, 4333 days, 10759 days, 30687 days, and 60190 days.
       Print out this information in the following format: planet ``planet`` has ``num_days`` number of days in
       a year! Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_2q
         :caption: Example c192_cp_13_ac_2q

         #include <iostream>

         enum planet { mercury = 1, venus, earth, mars, jupiter, saturn, uranus, neptune };

         int main() {
             planet p = jupiter;
             // Write your code here.
         }
.. tb-group::
   :name: c192_cp_13_ac_4_q

   .. tb-tab:: Question

       Now let's generate a ``bingo_board``! We want to fill the 25 ``space``\s on the ``bingo_board`` with
       random values from 1 to 75 without repititon. To do this, we'll make a ``vector``
       of numbers from 1 to 75 and shuffle it using the same method as shown in this chapter. Then
       we will select the first 25 values for the 25 spaces on the ``bingo_board``. We will
       do this entire process in multiple steps. First, write the function ``random_int``, which
       generates a random value between low and high, inclusive. Be sure to include the relevant libraries!
       Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_4q
         :caption: Example c192_cp_13_ac_4q

         #include <iostream>
         // Add any relevant libraries here.

         // Write your code for the random_int function here.
.. tb-group::
   :name: c192_cp_13_ac_6_q

   .. tb-tab:: Question

       Now that we have the functions ``random_int`` and ``swap_values``, we can write the function
       ``generate_rand_vec``. ``generate_rand_vec`` creates a ``vector`` with values from 1 to 75,
       shuffles it using ``random_int`` and ``swap_values``, and returns the shuffled ``vector``.
       Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_6q
         :caption: Example c192_cp_13_ac_6q

         #include <iostream>
         #include <vector>
         #include <cstdlib>
         #include <numeric>

         // Write your code for the generate_rand_vec function here.
.. tb-group::
   :name: c192_cp_13_ac_8_q

   .. tb-tab:: Question

       Let's print out our ``bingo_board``! Write the ``bingo_board`` member function
       ``print_board``. Insert tabs between each value in each row to make the board
       print out neater. Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_8q-support
         :hidden:

         std::size_t random_int(std::size_t low, std::size_t high) {
             static std::mt19937 engine(std::random_device{}());
             return std::uniform_int_distribution<std::size_t>{low, high}(engine);
         }

         void swap_values(std::vector<int> &vec, std::size_t index1, std::size_t index2) {
             int temp = vec[index1];
             vec[index1] = vec[index2];
             vec[index2] = temp;
         }

         std::vector<int> generate_rand_vec() {
             std::vector<int> vec(75);
             iota(vec.begin(), vec.end(), 1);
             for (std::size_t i = 0; i < vec.size(); ++i) {
                 std::size_t m_x = random_int(i, vec.size() - 1);
                 swap_values(vec, i, m_x);
             }
             return vec;
         }

         void bingo_board::make_board() {
             // Initialize board
             space s = {0, false};
             std::vector<space> cols(5, s);
             for (std::size_t i = 0; i < 5; ++i) {
                 board.push_back(cols);
             }

             // Fill board with random values
             std::vector<int> vec = generate_rand_vec();
             std::size_t count = 0;
             for (std::size_t row = 0; row < board.size(); ++row) {
                 for (std::size_t col = 0; col < board[row].size(); ++col) {
                 board[row][col].value = vec[count];
                 ++count;
                 }
             }

             // Create free space
             board[2][2].value = 0;
             board[2][2].is_filled = true;
         }

      .. tb-code:: cpp
         :name: c192_cp_13_ac_8q
         :caption: Example c192_cp_13_ac_8q
         :run-after: c192_cp_13_ac_8q-support

         #include <cstddef>
         #include <random>
         #include <iostream>
         #include <vector>
         #include <cstdlib>
         #include <numeric>

         struct space {
             int value;
             bool is_filled;
         };

         struct bingo_board {
             std::vector<std::vector<space> > board;
             void make_board ();
             void print_board ();
         };

         std::size_t random_int(std::size_t low, std::size_t high);
         void swap_values (std::vector<int> &vec, std::size_t index1, std::size_t index2);
         std::vector<int> generate_rand_vec ();

         // Write your code for the print_board function here.

         int main() {
             bingo_board bingo;
             bingo.make_board ();
             bingo.print_board ();
         }
.. tb-group::
   :name: c192_cp_13_ac_10_q

   .. tb-tab:: Question

       You may have noticed that in some cases, our version of ``bubble_sort`` does
       an unnecessary amount of work. For example, if our ``vector`` was {1, 2, 3, 5, 4},
       ``bubble_sort`` would swap 4 and 5, but then keep going even though our ``vector``
       is already in order! We can save some work by including a ``bool`` called ``is_changed``.
       If we swap values during a pass, we set ``is_changed`` to true. If nothing has been swapped,
       then ``is_changed`` stays false, and we know to break out of the loop since our ``vector``
       is already sorted. Write the function ``fast_bubble_sort``, which is ``bubble_sort`` with this
       modification. Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_10q
         :caption: Example c192_cp_13_ac_10q

         #include <cstddef>
         #include <iostream>
         #include <vector>

         void swap_values(std::vector<int> &vec, std::size_t index1, std::size_t index2) {
             int temp = vec[index1];
             vec[index1] = vec[index2];
             vec[index2] = temp;
         }

         // Write your code for the fast_bubble_sort function here.

         int main() {
             std::vector<int> vec = { 1, 3, 5, 4, 6, 8, 9 };
             fast_bubble_sort (vec);
             for (std::size_t i = 0; i < vec.size(); ++i) {
                 std::cout << vec[i] << ' ';
             }
         }
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

         enum m_day { mon = 1, tue, wed, thu, fri, sat, sun };

         int main () {
             m_day m_day = sun;
             switch (m_day > 5) {
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
