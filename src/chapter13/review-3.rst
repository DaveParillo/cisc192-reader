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
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         // Write your code for the enumerated type planet.

   .. tb-tab:: Answer

      Below is one way to implement the program. The planets in our solar system
      are Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, and Neptune.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_1a
         :caption: Example c192_cp_13_ac_1a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         enum planet { mercury = 1, venus, earth, mars, jupiter, saturn, uranus, neptune };

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_13_ac_2_sq`` is represented by these exercises:

   * :doc:`c192_cp_13_ac_2q <coding_practice_sq>`

   * :doc:`c192_cp_13_ac_2_pp <coding_practice_sq>`

.. tb-group::
   :name: c192_cp_13_3

   .. tb-tab:: Question

      A Bingo board has 25 Spaces in a matrix-like grid. A space has a number value randomly selected from 1 to 75 and can
      either be filled or not. Write the struct definitions for ``space`` and ``bingo_board``.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_3q
         :caption: Example c192_cp_13_ac_3q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>

         struct space {
             int value;
             bool is_filled;
         };

         struct bingo_board {
             std::vector<std::vector<space> > board;
         };

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_13_ac_4_sq`` is represented by these exercises:

   * :doc:`c192_cp_13_ac_4q <coding_practice_sq>`

   * :doc:`c192_cp_13_ac_4_pp <coding_practice_sq>`

.. tb-group::
   :name: c192_cp_13_5

   .. tb-tab:: Question

      Now we need a way to swap the values at two indices in a vector. Write the function ``swap_values``,
      which takes a ``vector`` of ``int``\s and two indices as parameters.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_5q
         :caption: Example c192_cp_13_ac_5q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <cstddef>
         #include <iostream>
         #include <vector>

         void swap_values (std::vector<int> &vec, std::size_t index1, std::size_t index2) {
             int temp = vec[index1];
             vec[index1] = vec[index2];
             vec[index2] = temp;
         }

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_13_ac_6_sq`` is represented by these exercises:

   * :doc:`c192_cp_13_ac_6q <coding_practice_sq>`

   * :doc:`c192_cp_13_ac_6_pp <coding_practice_sq>`

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
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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
                 std::size_t x = random_int(i, vec.size() - 1);
                 swap_values(vec, i, x);
             }
             return vec;
         }


      .. tb-code:: cpp
         :name: c192_cp_13_ac_7q
         :caption: Example c192_cp_13_ac_7q
         :run-after: c192_cp_13_ac_7q-support
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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
                 std::size_t x = random_int(i, vec.size() - 1);
                 swap_values(vec, i, x);
             }
             return vec;
         }


      .. tb-code:: cpp
         :name: c192_cp_13_ac_7a
         :caption: Example c192_cp_13_ac_7a
         :run-after: c192_cp_13_ac_7a-support
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_13_ac_8_sq`` is represented by these exercises:

   * :doc:`c192_cp_13_ac_8q <coding_practice_sq>`

   * :doc:`c192_cp_13_ac_8_pp <coding_practice_sq>`

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
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_13_ac_10_sq`` is represented by these exercises:

   * :doc:`c192_cp_13_ac_10q <coding_practice_sq>`

   * :doc:`c192_cp_13_ac_10_pp <coding_practice_sq>`

