Coding Practice
---------------

.. tb-group::
   :name: c192_cp_12_ac_2_q

   .. tb-tab:: Activecode

       An image is just a matrix of pixels. Write the ``struct`` definition for ``image``,
       which should store information about its height and width and contain a matrix
       of ``pixel``\s. Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_2q
         :caption: Example c192_cp_12_ac_2q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>

         struct pixel {
             int r;
             int g;
             int b;
         };

         // Write your code for the struct image here.

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_12_ac_2_pp

          An image is just a matrix of pixels. Write the ``struct`` definition for ``image``,
          which should store information about its height and width and contain a matrix
          of ``pixel``\s. Use the lines to construct the code, then go back to complete the Activecode tab.

         .. code-block:: c++

            {{group}}
             struct image {
            {{endgroup}}
            {{group}}
                 std::size_t height;
            {{endgroup}}
            {{group}}
                 std::size_t width;
            {{endgroup}}
            {{group}}
                 std::vector<std::vector<pixel>> matrix;
            {{endgroup}}
            {{distractor}}
            {{group}}
                 std::vector<pixel> matrix; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
                 std::vector<std::vector> matrix; #distractor
            {{endgroup}}
            {{group}}
             };
            {{endgroup}}

.. tb-group::
   :name: c192_cp_12_ac_4_q

   .. tb-tab:: Activecode

       Now let's print an ``image``. Unfortunately we can't print out the actual
       image to the terminal, but we can print out the ``pixel``\s in the ``image``
       matrix. Write the ``image`` member function ``print_image``.
       Separate pixels in the same row with a space and add a new line
       at the end of each row. Use the ``print_pixel`` function we created previously.
       Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_4q-support
         :hidden:
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         void pixel::print_pixel() {
             std::cout << "("<< r << ", " << g << ", " << b << ")";
         }

      .. tb-code:: cpp
         :name: c192_cp_12_ac_4q
         :caption: Example c192_cp_12_ac_4q
         :run-after: c192_cp_12_ac_4q-support
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <cstddef>
         #include <iostream>
         #include <vector>

         struct pixel {
             int r;
             int g;
             int b;
             void print_pixel();
         };

         struct image {
             std::size_t height;
             std::size_t width;
             std::vector<std::vector<pixel>> matrix;
             void print_image();
         };

         // Write your implementation of print_image here.

         int main() {
             std::vector<std::vector<pixel> > matrix = { { { 0, 255, 255 }, { 0, 0, 0 }, { 255, 255, 255 } },
                                             { { 30, 60, 50 }, { 20, 135, 200 }, { 60, 80, 125 } } };
             image image = { 2, 3, matrix };
             image.print_image();
         }

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_12_ac_4_pp

          Now let's print an ``image``. Unfortunately we can't print out the actual
          image to the terminal, but we can print out the ``pixel``\s in the ``image``
          matrix. Write the ``image`` member function ``print_image``.
          Separate pixels in the same row with a space and add a new line
          at the end of each row. Use the ``print_pixel`` function we created previously.
          Use the lines to construct the code, then go back to complete the Activecode tab.

         .. code-block:: c++

            {{group}}
             void image::print_image() {
            {{endgroup}}
            {{group}}
                 for (std::size_t r = 0; r < height; ++r) {
            {{endgroup}}
            {{group}}
                 for (std::size_t c = 0; c < width; ++ c) {
            {{endgroup}}
            {{group}}
                     matrix[r][c].print_pixel();
            {{endgroup}}
            {{group}}
                     std::cout << " ";
            {{endgroup}}
            {{group}}
                 }
            {{endgroup}}
            {{group}}
                 std::cout << std::endl;
            {{endgroup}}
            {{group}}
                 }
            {{endgroup}}
            {{group}}
             }
            {{endgroup}}

.. tb-group::
   :name: c192_cp_12_ac_6_q

   .. tb-tab:: Activecode

       Let's write a ``swap_pixel`` member function for ``image``. ``swap_pixel``
       takes two pairs of row indices and column indices from a matrix and swaps the two
       ``pixel``\s at those locations. Note that these indices are 0-indexed, unlike the
       previous ``crop_index`` parameters. Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_6q-support
         :hidden:
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         void pixel::print_pixel() {
             cout << "("<< r << ", " << g << ", " << b << ")";
         }

         void image::print_image() {
             for (std::size_t r = 0; r < height; ++r) {
             for (std::size_t c = 0; c < width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << " ";
             }
             cout << std::endl;
             }
         }

         void image::crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col) {
             // Crop coordinates are one-based and inclusive.
             if (start_row == 0 || start_col == 0 || stop_row < start_row ||
                 stop_col < start_col || stop_row > height || stop_col > width) {
                 throw std::out_of_range("crop coordinates");
             }
             std::vector<std::vector<pixel> > new_matrix(stop_row - start_row + 1);
             for (std::size_t r = start_row - 1; r < stop_row; ++r) {
                 for (std::size_t c = start_col - 1; c < stop_col; ++c) {
                     new_matrix[r - (start_row - 1)].push_back(matrix[r][c]);
                 }
             }
             height = stop_row - start_row + 1;
             width = stop_col - start_col + 1;
             matrix = new_matrix;
         }

      .. tb-code:: cpp
         :name: c192_cp_12_ac_6q
         :caption: Example c192_cp_12_ac_6q
         :run-after: c192_cp_12_ac_6q-support
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <stdexcept>
         #include <cstddef>
         #include <iostream>
         #include <vector>
         using std::cout;

         struct pixel {
             int r;
             int g;
             int b;
             void print_pixel();
         };

         struct image {
             std::size_t height;
             std::size_t width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
             void swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2);
         };

         // Write your implementation of swap_pixel here.

         int main() {
             std::vector<std::vector<pixel> > matrix = { { { 0, 140, 255 }, { 0, 0, 0 }, { 15, 20, 255 } } };
             image image = { 1, 3, matrix };
             image.print_image();
             cout << std::endl;
             image.swap_pixel(0, 0, 0, 2);
             image.print_image();
         }

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_12_ac_6_pp

          Let's write a ``swap_pixel`` member function for ``image``. ``swap_pixel``
          takes two pairs of row indices and column indices from a matrix and swaps the two
          ``pixel``\s at those locations. Note that these indices are 0-indexed, unlike the
          previous ``crop_index`` parameters.
          Use the lines to construct the code, then go back to complete the Activecode tab.

         .. code-block:: c++

            {{group}}
             void image::swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2) {
            {{endgroup}}
            {{group}}
                 pixel temp = { matrix[row1][col1].r, matrix[row1][col1].g,  matrix[row1][col1].b };
            {{endgroup}}
            {{group}}
                 matrix[row1][col1] = matrix[row2][col2];
            {{endgroup}}
            {{group}}
                 matrix[row2][col2] = temp;
            {{endgroup}}
            {{group}}
             }
            {{endgroup}}

.. tb-group::
   :name: c192_cp_12_ac_8_q

   .. tb-tab:: Activecode

       Oops! Somehow our image came out upside down. Let's write
       the ``image`` member function ``flip_vertical``, which
       reverts an image to be right side up.
       Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_8q-support
         :hidden:
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         void pixel::print_pixel() {
             cout << "("<< r << ", " << g << ", " << b << ")";
         }

         void image::print_image() {
             for (std::size_t r = 0; r < height; ++r) {
             for (std::size_t c = 0; c < width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << " ";
             }
             cout << std::endl;
             }
         }

         void image::crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col) {
             // Crop coordinates are one-based and inclusive.
             if (start_row == 0 || start_col == 0 || stop_row < start_row ||
                 stop_col < start_col || stop_row > height || stop_col > width) {
                 throw std::out_of_range("crop coordinates");
             }
             std::vector<std::vector<pixel> > new_matrix(stop_row - start_row + 1);
             for (std::size_t r = start_row - 1; r < stop_row; ++r) {
                 for (std::size_t c = start_col - 1; c < stop_col; ++c) {
                     new_matrix[r - (start_row - 1)].push_back(matrix[r][c]);
                 }
             }
             height = stop_row - start_row + 1;
             width = stop_col - start_col + 1;
             matrix = new_matrix;
         }

         void image::swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2) {
             pixel temp = { matrix[row1][col1].r, matrix[row1][col1].g,  matrix[row1][col1].b };
             matrix[row1][col1] = matrix[row2][col2];
             matrix[row2][col2] = temp;
         }

         void image::flip_horizontal() {
             for (std::size_t r = 0; r < height; ++r) {
                 std::size_t start = 0;
                 std::size_t end = width == 0 ? 0 : width - 1;
                 while (start < end) {
                     swap_pixel(r, start, r, end);
                     ++start;
                     --end;
                 }
             }
         }

      .. tb-code:: cpp
         :name: c192_cp_12_ac_8q
         :caption: Example c192_cp_12_ac_8q
         :run-after: c192_cp_12_ac_8q-support
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <stdexcept>
         #include <cstddef>
         #include <iostream>
         #include <vector>
         using std::cout;

         struct pixel {
             int r;
             int g;
             int b;
             void print_pixel();
         };

         struct image {
             std::size_t height;
             std::size_t width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
             void swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2);
             void flip_horizontal();
             void flip_vertical();
         };

         // Write your implementation of flip_vertical here.

         int main() {
             std::vector<std::vector<pixel> > matrix = { { { 255, 255, 255 }, { 255, 255, 255 }, { 255, 255, 255 } },
                                             { { 50, 50, 50 }, { 10, 10, 10 }, { 50, 50, 50 } },
                                             { { 30, 30, 30 }, { 70, 70, 70 }, { 30, 30, 30 } },
                                             { { 0, 0, 0 }, { 0, 0, 0 }, { 0, 0, 0 } } };
             image image = { 4, 3, matrix };
             image.print_image();
             cout << std::endl;
             image.flip_vertical();
             image.print_image();
         }

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_12_ac_8_pp

          Oops! Somehow our image came out upside down. Let's write
          the ``image`` member function ``flip_vertical``, which
          reverts an image to be right side up.
          Use the lines to construct the code, then go back to complete the Activecode tab.

         .. code-block:: c++

            {{group}}
             void image::flip_vertical() {
                 for (std::size_t c = 0; c < width; ++c) {
            {{endgroup}}
            {{group}}
                     std::size_t start = 0;
            {{endgroup}}
            {{group}}
                     std::size_t end = height == 0 ? 0 : height - 1;
            {{endgroup}}
            {{group}}
                     while (start < end) {
            {{endgroup}}
            {{group}}
                         swap_pixel(start, c, end, c);
            {{endgroup}}
            {{group}}
                         ++start;
            {{endgroup}}
            {{group}}
                         --end;
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

.. tb-group::
   :name: c192_cp_12_ac_10_q

   .. tb-tab:: Activecode

       Let's return our image to the state of a clean slate. Write the
       function ``clear_image``, which sets the color of every ``pixel``
       to white. Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_10q-support
         :hidden:
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         void pixel::print_pixel() {
             cout << "("<< r << ", " << g << ", " << b << ")";
         }

         void image::print_image() {
             for (std::size_t r = 0; r < height; ++r) {
             for (std::size_t c = 0; c < width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << " ";
             }
             cout << std::endl;
             }
         }

         void image::crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col) {
             // Crop coordinates are one-based and inclusive.
             if (start_row == 0 || start_col == 0 || stop_row < start_row ||
                 stop_col < start_col || stop_row > height || stop_col > width) {
                 throw std::out_of_range("crop coordinates");
             }
             std::vector<std::vector<pixel> > new_matrix(stop_row - start_row + 1);
             for (std::size_t r = start_row - 1; r < stop_row; ++r) {
                 for (std::size_t c = start_col - 1; c < stop_col; ++c) {
                     new_matrix[r - (start_row - 1)].push_back(matrix[r][c]);
                 }
             }
             height = stop_row - start_row + 1;
             width = stop_col - start_col + 1;
             matrix = new_matrix;
         }

         void image::swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2) {
             pixel temp = { matrix[row1][col1].r, matrix[row1][col1].g,  matrix[row1][col1].b };
             matrix[row1][col1] = matrix[row2][col2];
             matrix[row2][col2] = temp;
         }

         void image::flip_horizontal() {
             for (std::size_t r = 0; r < height; ++r) {
                 std::size_t start = 0;
                 std::size_t end = width == 0 ? 0 : width - 1;
                 while (start < end) {
                     swap_pixel(r, start, r, end);
                     ++start;
                     --end;
                 }
             }
         }

         void image::flip_vertical() {
             for (std::size_t c = 0; c < width; ++c) {
                 std::size_t start = 0;
                 std::size_t end = height == 0 ? 0 : height - 1;
                 while (start < end) {
                     swap_pixel(start, c, end, c);
                     ++start;
                     --end;
                 }
             }
         }

         void image::create_border(pixel p) {
             if (height == 0 || width == 0) return;
             for (std::size_t r = 0; r < height; ++r) {
                 matrix[r][0] = p;
                 matrix[r][width - 1] = p;
             }
             for (std::size_t c = 0; c < width; ++c) {
                 matrix[0][c] = p;
                 matrix[height - 1][c] = p;
             }
         }

      .. tb-code:: cpp
         :name: c192_cp_12_ac_10q
         :caption: Example c192_cp_12_ac_10q
         :run-after: c192_cp_12_ac_10q-support
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <stdexcept>
         #include <cstddef>
         #include <iostream>
         #include <vector>
         using std::cout;

         struct pixel {
             int r;
             int g;
             int b;
             void print_pixel();
         };

         struct image {
             std::size_t height;
             std::size_t width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
             void swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2);
             void flip_horizontal();
             void flip_vertical();
             void create_border(pixel p);
             void clear_image();
         };

         // Write your implementation of clear_image here.

         int main() {
             std::vector<std::vector<pixel> > matrix = { { { 0, 0, 0 }, { 10, 10, 10 }, { 65, 70, 255 } },
                                             { { 26, 48, 205 }, { 43, 12, 15 }, { 45, 30, 70 } },
                                             { { 89, 36, 65 }, { 75, 43, 26 }, { 40, 75, 70 } } };
             image image = { 3, 3, matrix };
             image.print_image();
             cout << std::endl;
             image.clear_image();
             image.print_image();
         }

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_12_ac_10_pp

          Let's return our image to the state of a clean slate. Write the
          function ``clear_image``, which sets the color of every ``pixel``
          to white.
          Use the lines to construct the code, then go back to complete the Activecode tab.

         .. code-block:: c++

            {{group}}
             void image::clear_image () {
            {{endgroup}}
            {{group}}
                 for (std::size_t r = 0; r < height; r++) {
            {{endgroup}}
            {{group}}
                     for (std::size_t c = 0; c < width; c++) {
            {{endgroup}}
            {{group}}
                         matrix[r][c].r = 255;
            {{endgroup}}
            {{group}}
                         matrix[r][c].g = 255;
            {{endgroup}}
            {{group}}
                         matrix[r][c].b = 255;
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

