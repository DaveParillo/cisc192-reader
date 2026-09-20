Coding Practice
---------------

.. tb-group::
   :name: c192_cp_13_ac_2_q

   .. tb-tab:: Activecode

       How long is a year on other planets? Let's write a program that prints out the number of days
       in a year on each planet using a switch statement. These values are, in planetary order,
       88 days, 225 days, 365 days, 687 days, 4333 days, 10759 days, 30687 days, and 60190 days.
       Print out this information in the following format: planet ``planet`` has ``num_days`` number of days in
       a year! Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_2q
         :caption: Example c192_cp_13_ac_2q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         enum planet { mercury = 1, venus, earth, mars, jupiter, saturn, uranus, neptune };

         int main() {
             planet p = jupiter;
             // Write your code here.
         }

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_13_ac_2_pp

          How long is a year on other planets? Let's write a program that prints out the number of days
          in a year on each planet using a switch statement. These values are, in planetary order,
          88 days, 225 days, 365 days, 687 days, 4333 days, 10759 days, 30687 days, and 60190 days.
          Print out this information in the following format: planet ``planet`` has ``num_days`` number of days in
          a year! Use the lines to construct the code, then go back to complete the Activecode tab.

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

.. tb-group::
   :name: c192_cp_13_ac_4_q

   .. tb-tab:: Activecode

       Now let's generate a ``bingo_board``! We want to fill the 25 ``space``\s on the ``bingo_board`` with
       random values from 1 to 75 without repititon. To do this, we'll make a ``vector``
       of numbers from 1 to 75 and shuffle it using the same method as shown in this chapter. Then
       we will select the first 25 values for the 25 spaces on the ``bingo_board``. We will
       do this entire process in multiple steps. First, write the function ``random_int``, which
       generates a random value between low and high, inclusive. Be sure to include the relevant libraries!
       Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_4q
         :caption: Example c192_cp_13_ac_4q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         // Add any relevant libraries here.

         // Write your code for the random_int function here.

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_13_ac_4_pp

          Now let's generate a ``bingo_board``! We want to fill the 25 ``space``\s on the ``bingo_board`` with
          random values from 1 to 75 without repititon. To do this, we'll make a ``vector``
          of numbers from 1 to 75 and shuffle it using the same method as shown in this chapter. Then
          we will select the first 25 values for the 25 spaces on the ``bingo_board``. We will
          do this entire process in multiple steps. First, write the function ``random_int``, which
          generates a random value between low and high, inclusive. Be sure to include the relevant libraries!
          Use the lines to construct the code, then go back to complete the Activecode tab.

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

.. tb-group::
   :name: c192_cp_13_ac_6_q

   .. tb-tab:: Activecode

       Now that we have the functions ``random_int`` and ``swap_values``, we can write the function
       ``generate_rand_vec``. ``generate_rand_vec`` creates a ``vector`` with values from 1 to 75,
       shuffles it using ``random_int`` and ``swap_values``, and returns the shuffled ``vector``.
       Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_6q
         :caption: Example c192_cp_13_ac_6q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>
         #include <cstdlib>
         #include <numeric>

         // Write your code for the generate_rand_vec function here.

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_13_ac_6_pp

          Now that we have the functions ``random_int`` and ``swap_values``, we can write the function
          ``generate_rand_vec``. ``generate_rand_vec`` creates a ``vector`` with values from 1 to 75,
          shuffles it using ``random_int`` and ``swap_values``, and returns the shuffled ``vector``.
          Use the lines to construct the code, then go back to complete the Activecode tab.

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

.. tb-group::
   :name: c192_cp_13_ac_8_q

   .. tb-tab:: Activecode

       Let's print out our ``bingo_board``! Write the ``bingo_board`` member function
       ``print_board``. Insert tabs between each value in each row to make the board
       print out neater. Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_8q-support
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

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_13_ac_8_pp

          Let's print out our ``bingo_board``! Write the ``bingo_board`` member function
          ``print_board``. Insert tabs between each value in each row to make the board
          print out neater. Use the lines to construct the code, then go back to complete the Activecode tab.

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

.. tb-group::
   :name: c192_cp_13_ac_10_q

   .. tb-tab:: Activecode

       You may have noticed that in some cases, our version of ``bubble_sort`` does
       an unnecessary amount of work. For example, if our ``vector`` was {1, 2, 3, 5, 4},
       ``bubble_sort`` would swap 4 and 5, but then keep going even though our ``vector``
       is already in order! We can save some work by including a ``bool`` called ``is_changed``.
       If we swap values during a pass, we set ``is_changed`` to true. If nothing has been swapped,
       then ``is_changed`` stays false, and we know to break out of the loop since our ``vector``
       is already sorted. Write the function ``fast_bubble_sort``, which is ``bubble_sort`` with this
       modification. Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_13_ac_10q
         :caption: Example c192_cp_13_ac_10q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_13_ac_10_pp

          You may have noticed that in some cases, our version of ``bubble_sort`` does
          an unnecessary amount of work. For example, if our ``vector`` was {1, 2, 3, 5, 4},
          ``bubble_sort`` would swap 4 and 5, but then keep going even though our ``vector``
          is already in order! We can save some work by including a ``bool`` called ``is_changed``.
          If we swap values during a pass, we set ``is_changed`` to true. If nothing has been swapped,
          then ``is_changed`` stays false, and we know to break out of the loop since our ``vector``
          is already sorted. Write the function ``fast_bubble_sort``, which is ``bubble_sort`` with this
          modification. Use the lines to construct the code, then go back to complete the Activecode tab.

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

