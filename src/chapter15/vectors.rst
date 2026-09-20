Growing sequences with std::vector
==================================

``std::vector`` is declared in ``<vector>``. It owns a sequence whose size can
change at run time. ``push_back`` appends an element, ``pop_back`` removes the
last element of a nonempty vector, and ``size()`` reports the number of stored
elements. Unlike an array's extent, a vector's size is not part of its type.

A vector's **capacity** is the number of elements it can hold before it must
allocate more storage. ``reserve(n)`` can increase capacity, but does not add
elements. ``resize(n)`` changes the number of elements. Prefer ``push_back``
when reading an unknown number of records instead of maintaining a separate
count of used slots yourself.

.. tb-code:: cpp
   :name: c192_vectors_growth
   :caption: Example c192_vectors_growth
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <iostream>
   #include <sstream>
   #include <vector>

   int main() {
       std::istringstream input("12 7 19");
       std::vector<int> readings;
       readings.reserve(10);
       int value = 0;
       while (input >> value) {
           readings.push_back(value);
       }
       std::cout << readings.size() << '\n';
       for (int reading : readings) {
           std::cout << reading << ' ';
       }
       std::cout << '\n';
   }

The vector contains three elements, not ten. Its capacity is at least ten;
the exact capacity is an implementation detail. A vector may contain repeated
values. Appending can invalidate references, pointers, and iterators to its
elements when storage is reallocated; do not keep using them after that happens.

For a table whose dimensions are known only at run time, create rows with
``std::vector<std::vector<int>>``. This initialization creates a rectangular
table of zeros:

.. tb-code:: cpp
   :name: c192_vectors_table
   :caption: Example c192_vectors_table
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <cstddef>
   #include <iostream>
   #include <vector>

   int main() {
       std::size_t rows = 2;
       std::size_t columns = 3;
       std::vector<std::vector<int>> table(rows, std::vector<int>(columns, 0));
       table.at(1).at(2) = 7;
       for (const auto& row : table) {
           for (int value : row) {
               std::cout << value << ' ';
           }
           std::cout << '\n';
       }
   }

Each row is a separate vector and can have a different length. If your
algorithm requires a rectangular table, preserve that condition when resizing
rows. Check both dimensions when accessing a value; ``table.at(r)[c]`` checks
only the row. A table with no rows has no first row from which to read a width.

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

