Fixed-size sequences with std::array
====================================

``std::array`` is declared in ``<array>``. Its element type and size are both
part of its type: ``std::array<int, 3>`` and ``std::array<int, 4>`` are different
types. Use it when the number of elements is known at compile time.

.. tb-code:: cpp
   :name: c192_arrays_readings
   :caption: Example c192_arrays_readings
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <array>
   #include <iostream>

   int main() {
       std::array<int, 4> readings{18, 21, 19, 22};
       int total = 0;
       for (int reading : readings) {
           total += reading;
       }
       std::cout << readings.size() << " readings, total " << total << '\n';
       readings.at(0) = 20;
       std::cout << readings.front() << '\n';
   }

List initialization supplies the elements in order. ``std::array<int, 4> a{};``
initializes all four integers to zero. In contrast, a local declaration
``std::array<int, 4> a;`` does not initialize those integers; do not read them
before assigning values.

``size()`` returns an unsigned size type. If you need a position, use
``std::size_t`` from ``<cstddef>``; if you only need the elements, prefer a
range-based ``for`` loop. ``at()`` checks its index and throws
``std::out_of_range`` if it is invalid. ``operator[]`` does not perform this
check in C++20. Neither ``front()`` nor ``back()`` may be used on an empty array.

An array owns its elements and can be copied or assigned. Its size never
changes: it has no ``push_back`` or ``resize`` member. A built-in C array lacks
many of these conveniences, so we use ``std::array`` for fixed-size sequences.

Nested arrays can describe a rectangular table. The outer array contains
rows; each row contains columns. Access ``table[row][column]``, using two
pairs of brackets, not ``table[row, column]``.

.. tb-code:: cpp
   :name: c192_arrays_table
   :caption: Example c192_arrays_table
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <array>
   #include <iostream>

   int main() {
       std::array<std::array<int, 3>, 2> table{{{1, 2, 3}, {4, 5, 6}}};
       for (const auto& row : table) {
           for (int value : row) {
               std::cout << value << ' ';
           }
           std::cout << '\n';
       }
       std::cout << table.at(1).at(2) << '\n';
   }

The dimensions here are two rows and three columns. Each ``at()`` checks one
dimension. The elements in an array of arrays have fixed rectangular shape.

.. tb-choice::
   :name: mce_15_1

   We want to open a file and parse its data into our program. What library
   do we need to include?

   - [ ] ``iostream``

     - This library deals with communication through the standard input and output.

   - [ ] ``sstream``

     -  This library is used to manipulate string objects as if they were streams.

   - [x] ``fstream``

     + This library is used to manipulate files using streams.

   - [ ] ``iomanip``

     - This library is used to modify internal flags and formatting options.

.. tb-blank::
   :name: c192_question15_8_2

   In ``table[9][17]``, the row index is {{blank:blank1}} and the column index is {{blank:blank2}}.

   .. tb-answer:: blank1
      :match: 9
      :feedback: Correct!
      :incorrect: The first subscript chooses the row.

   .. tb-answer:: blank2
      :match: 17
      :incorrect: The second subscript chooses a column within that row.

