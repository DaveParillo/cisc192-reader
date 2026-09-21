.. _vectors-objects-coding-practice:

Coding Practice
---------------

.. tb-group::
   :name: c192_cp_12_1

   .. tb-tab:: Question

      A pixel is the smallest controllable element of a picture represented on the screen. Images
      are comprised of numerous individual pixels, and each pixel's color sample has three numerical
      RGB (red, green, blue) components to represent the color of that pixel. The intensity value of
      each RGB component ranges from 0 to 255, where 0 is no intensity and 255 is highest intensity.
      Write the ``struct`` definition for ``pixel``, which has values for each component r, g, and b.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_1q
         :caption: Example c192_cp_12_ac_1q

         #include <iostream>
         #include <vector>

         // Write your code for the struct pixel here.

   .. tb-tab:: Answer

      Below is one way to implement the program. We declare the ``pixel`` struct
      and create the instance variables in order.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_1a
         :caption: Example c192_cp_12_ac_1a

         #include <iostream>
         #include <vector>

         struct pixel {
             int r;
             int g;
             int b;
         };


.. tb-group::
   :name: c192_cp_12_3

   .. tb-tab:: Question

      Let's print out a ``pixel``! Write the ``pixel`` member function ``print_pixel``,
      which prints out the values of the ``pixel`` in this form: (r, g, b).

      .. tb-code:: cpp
         :name: c192_cp_12_ac_3q
         :caption: Example c192_cp_12_ac_3q

         #include <iostream>
         #include <vector>

         struct pixel {
             int r;
             int g;
             int b;
             void print_pixel();
         };

         // Write your implementation of print_pixel here.

         int main() {
             pixel p = {0, 0, 0};
             p.print_pixel();
         }

   .. tb-tab:: Answer

      Below is one way to implement the program. We use the scope resolution
      operator to make ``print_pixel`` a ``pixel`` member function.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_3a
         :caption: Example c192_cp_12_ac_3a

         #include <iostream>
         #include <vector>

         struct pixel {
             int r;
             int g;
             int b;
             void print_pixel();
         };

         void pixel::print_pixel() {
             std::cout << '('<< r << ", " << g << ", " << b << ')';
         }

         int main() {
             pixel p = {0, 0, 0};
             p.print_pixel();
         }


.. tb-group::
   :name: c192_cp_12_5

   .. tb-tab:: Question

      Somebody photobombed our image! What if we wanted to crop the photobomber out?
      Let's write the ``image`` member function ``crop_image``, which takes four paramenters,
      a start and stop row and a start and stop column. It then modifies the matrix to the
      cropped matrix.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_5q-support
         :hidden:

         void pixel::print_pixel() {
             cout << '('<< r << ", " << g << ", " << b << ')';
         }

         void image::print_image() {
             for (std::size_t r = 0; r < m_height; ++r) {
             for (std::size_t c = 0; c < m_width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
             }
         }


      .. tb-code:: cpp
         :name: c192_cp_12_ac_5q
         :caption: Example c192_cp_12_ac_5q
         :run-after: c192_cp_12_ac_5q-support

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
             std::size_t m_height;
             std::size_t m_width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
         };

         // Write your implementation of crop_image here.

         int main() {
             std::vector<std::vector<pixel> > matrix = { { { 0, 255, 255 }, { 0, 0, 0 }, { 255, 255, 255 } },
                                               { { 30, 60, 50 }, { 20, 135, 200 }, { 60, 80, 125 } },
                                               { { 10, 0, 50 }, { 30, 65, 225 }, { 25, 105, 125 } },
                                               { { 255, 60, 0 }, { 20, 25, 255 }, { 65, 55, 0 } } };
             image image = { 4, 3, matrix };
             image.print_image();
             cout << '\n';
             image.crop_image(2, 3, 1, 2);
             image.print_image();
         }

   .. tb-tab:: Answer

      Below is one way to implement the program. First we make a new matrix
      with the correct amount of rows. Then we push back the pixels we want
      into the new matrix. Afterwards, we must update the height and width
      of the ``image`` and set the ``image``\'s matrix equal to the new one
      we created.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_5a-support
         :hidden:

         void pixel::print_pixel() {
             cout << '('<< r << ", " << g << ", " << b << ')';
         }

         void image::print_image() {
             for (std::size_t r = 0; r < m_height; ++r) {
             for (std::size_t c = 0; c < m_width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
             }
         }


      .. tb-code:: cpp
         :name: c192_cp_12_ac_5a
         :caption: Example c192_cp_12_ac_5a
         :run-after: c192_cp_12_ac_5a-support

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
             std::size_t m_height;
             std::size_t m_width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
         };

         void image::crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col) {
             // Crop coordinates are one-based and inclusive.
             if (start_row == 0 || start_col == 0 || stop_row < start_row ||
                 stop_col < start_col || stop_row > m_height || stop_col > m_width) {
                 throw std::out_of_range("crop coordinates");
             }
             std::vector<std::vector<pixel> > new_matrix(stop_row - start_row + 1);
             for (std::size_t r = start_row - 1; r < stop_row; ++r) {
                 for (std::size_t c = start_col - 1; c < stop_col; ++c) {
                     new_matrix[r - (start_row - 1)].push_back(matrix[r][c]);
                 }
             }
             m_height = stop_row - start_row + 1;
             m_width = stop_col - start_col + 1;
             matrix = new_matrix;
         }

         int main() {
             std::vector<std::vector<pixel> > matrix = { { { 0, 255, 255 }, { 0, 0, 0 }, { 255, 255, 255 } },
                                               { { 30, 60, 50 }, { 20, 135, 200 }, { 60, 80, 125 } },
                                               { { 10, 0, 50 }, { 30, 65, 225 }, { 25, 105, 125 } },
                                               { { 255, 60, 0 }, { 20, 25, 255 }, { 65, 55, 0 } } };
             image image = { 4, 3, matrix };
             image.print_image();
             cout << '\n';
             image.crop_image(2, 3, 1, 2);
             image.print_image();
         }


.. tb-group::
   :name: c192_cp_12_7

   .. tb-tab:: Question

      When you take a selfie on your phone, the image is mirrored.
      We can do the same to an image by flipping it horizontally.
      Write the ``image`` member function ``flip_horizontal``,
      which flips an image horizontally. Use the ``swap_pixel``
      function we created previously.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_7q-support
         :hidden:

         void pixel::print_pixel() {
             cout << '('<< r << ", " << g << ", " << b << ')';
         }

         void image::print_image() {
             for (std::size_t r = 0; r < m_height; ++r) {
             for (std::size_t c = 0; c < m_width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
             }
         }

         void image::crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col) {
             // Crop coordinates are one-based and inclusive.
             if (start_row == 0 || start_col == 0 || stop_row < start_row ||
                 stop_col < start_col || stop_row > m_height || stop_col > m_width) {
                 throw std::out_of_range("crop coordinates");
             }
             std::vector<std::vector<pixel> > new_matrix(stop_row - start_row + 1);
             for (std::size_t r = start_row - 1; r < stop_row; ++r) {
                 for (std::size_t c = start_col - 1; c < stop_col; ++c) {
                     new_matrix[r - (start_row - 1)].push_back(matrix[r][c]);
                 }
             }
             m_height = stop_row - start_row + 1;
             m_width = stop_col - start_col + 1;
             matrix = new_matrix;
         }

         void image::swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2) {
             pixel temp = { matrix[row1][col1].r, matrix[row1][col1].g,  matrix[row1][col1].b };
             matrix[row1][col1] = matrix[row2][col2];
             matrix[row2][col2] = temp;
         }


      .. tb-code:: cpp
         :name: c192_cp_12_ac_7q
         :caption: Example c192_cp_12_ac_7q
         :run-after: c192_cp_12_ac_7q-support

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
             std::size_t m_height;
             std::size_t m_width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
             void swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2);
             void flip_horizontal();
         };

         // Write your implementation of flip_horizontal here.

         int main() {
             std::vector<std::vector<pixel> > matrix = { { { 0, 0, 0 }, { 10, 10, 10 }, { 255, 255, 255 } },
                                               { { 50, 50, 50 }, { 10, 10, 10 }, { 255, 255, 255 } },
                                               { { 100, 100, 100 }, { 10, 10, 10 }, { 255, 255, 255 } },
                                               { { 150, 150, 150 }, { 10, 10, 10 }, { 255, 255, 255 } } };
             image image = { 4, 3, matrix };
             image.print_image();
             cout << '\n';
             image.flip_horizontal();
             image.print_image();
         }

   .. tb-tab:: Answer

      Below is one way to implement the program. We loop through
      each row in the matrix. We create start and end indices and
      repeatedly swap pixels, moving both indices toward the middle.
      Once they meet in the middle, we have finished flipping the image.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_7a-support
         :hidden:

         void pixel::print_pixel() {
             cout << '('<< r << ", " << g << ", " << b << ')';
         }

         void image::print_image() {
             for (std::size_t r = 0; r < m_height; ++r) {
             for (std::size_t c = 0; c < m_width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
             }
         }

         void image::crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col) {
             // Crop coordinates are one-based and inclusive.
             if (start_row == 0 || start_col == 0 || stop_row < start_row ||
                 stop_col < start_col || stop_row > m_height || stop_col > m_width) {
                 throw std::out_of_range("crop coordinates");
             }
             std::vector<std::vector<pixel> > new_matrix(stop_row - start_row + 1);
             for (std::size_t r = start_row - 1; r < stop_row; ++r) {
                 for (std::size_t c = start_col - 1; c < stop_col; ++c) {
                     new_matrix[r - (start_row - 1)].push_back(matrix[r][c]);
                 }
             }
             m_height = stop_row - start_row + 1;
             m_width = stop_col - start_col + 1;
             matrix = new_matrix;
         }

         void image::swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2) {
             pixel temp = { matrix[row1][col1].r, matrix[row1][col1].g,  matrix[row1][col1].b };
             matrix[row1][col1] = matrix[row2][col2];
             matrix[row2][col2] = temp;
         }


      .. tb-code:: cpp
         :name: c192_cp_12_ac_7a
         :caption: Example c192_cp_12_ac_7a
         :run-after: c192_cp_12_ac_7a-support

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
             std::size_t m_height;
             std::size_t m_width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
             void swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2);
             void flip_horizontal();
         };

         void image::flip_horizontal() {
             for (std::size_t r = 0; r < m_height; ++r) {
                 std::size_t start = 0;
                 std::size_t end = m_width == 0 ? 0 : m_width - 1;
                 while (start < end) {
                     swap_pixel(r, start, r, end);
                     ++start;
                     --end;
                 }
             }
         }

         int main() {
             std::vector<std::vector<pixel> > matrix = { { { 0, 0, 0 }, { 10, 10, 10 }, { 255, 255, 255 } },
                                               { { 50, 50, 50 }, { 10, 10, 10 }, { 255, 255, 255 } },
                                               { { 100, 100, 100 }, { 10, 10, 10 }, { 255, 255, 255 } },
                                               { { 150, 150, 150 }, { 10, 10, 10 }, { 255, 255, 255 } } };
             image image = { 4, 3, matrix };
             image.print_image();
             cout << '\n';
             image.flip_horizontal();
             image.print_image();
         }


.. tb-group::
   :name: c192_cp_12_9

   .. tb-tab:: Question

      Let's write the ``image`` member function called ``create_border``,
      which sets the ``pixel``\s on the edge of an ``image`` to a given
      ``pixel``.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_9q-support
         :hidden:

         void pixel::print_pixel() {
             cout << '('<< r << ", " << g << ", " << b << ')';
         }

         void image::print_image() {
             for (std::size_t r = 0; r < m_height; ++r) {
             for (std::size_t c = 0; c < m_width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
             }
         }

         void image::crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col) {
             // Crop coordinates are one-based and inclusive.
             if (start_row == 0 || start_col == 0 || stop_row < start_row ||
                 stop_col < start_col || stop_row > m_height || stop_col > m_width) {
                 throw std::out_of_range("crop coordinates");
             }
             std::vector<std::vector<pixel> > new_matrix(stop_row - start_row + 1);
             for (std::size_t r = start_row - 1; r < stop_row; ++r) {
                 for (std::size_t c = start_col - 1; c < stop_col; ++c) {
                     new_matrix[r - (start_row - 1)].push_back(matrix[r][c]);
                 }
             }
             m_height = stop_row - start_row + 1;
             m_width = stop_col - start_col + 1;
             matrix = new_matrix;
         }

         void image::swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2) {
             pixel temp = { matrix[row1][col1].r, matrix[row1][col1].g,  matrix[row1][col1].b };
             matrix[row1][col1] = matrix[row2][col2];
             matrix[row2][col2] = temp;
         }

         void image::flip_horizontal() {
             for (std::size_t r = 0; r < m_height; ++r) {
                 std::size_t start = 0;
                 std::size_t end = m_width == 0 ? 0 : m_width - 1;
                 while (start < end) {
                     swap_pixel(r, start, r, end);
                     ++start;
                     --end;
                 }
             }
         }

         void image::flip_vertical() {
             for (std::size_t c = 0; c < m_width; ++c) {
                 std::size_t start = 0;
                 std::size_t end = m_height == 0 ? 0 : m_height - 1;
                 while (start < end) {
                     swap_pixel(start, c, end, c);
                     ++start;
                     --end;
                 }
             }
         }


      .. tb-code:: cpp
         :name: c192_cp_12_ac_9q
         :caption: Example c192_cp_12_ac_9q
         :run-after: c192_cp_12_ac_9q-support

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
             std::size_t m_height;
             std::size_t m_width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
             void swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2);
             void flip_horizontal();
             void flip_vertical();
             void create_border(pixel p);
         };

         // Write your implementation of create_border here.

         int main() {
             std::vector<std::vector<pixel> > matrix = { { { 25, 65, 23 }, { 73, 56, 24 }, { 255, 255, 255 }, { 253, 61, 56 } },
                                               { { 50, 50, 50 }, { 145, 52, 102 }, { 2, 0, 25 }, { 52, 47, 35 } },
                                               { { 45, 34, 100 }, { 213, 67, 45 }, { 2, 45, 255 }, { 34, 16, 76 } },
                                               { { 2, 2, 78 }, { 164, 16, 23 }, { 5, 255, 25 }, { 32, 65, 34 } },
                                               { { 150, 150, 150 }, { 241, 42, 64 }, { 1, 4, 255 }, { 16, 73, 84 } } };
             image image = { 5, 4, matrix };
             image.print_image();
             cout << '\n';
             pixel p = { 0, 0, 0 };
             image.create_border(p);
             image.print_image();
         }

   .. tb-tab:: Answer

      Below is one way to implement the program. We set the first and last
      row and first and last column of ``pixel``\s in the ``image`` to the
      given ``pixel``.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_9a-support
         :hidden:

         void pixel::print_pixel() {
             cout << '('<< r << ", " << g << ", " << b << ')';
         }

         void image::print_image() {
             for (std::size_t r = 0; r < m_height; ++r) {
             for (std::size_t c = 0; c < m_width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
             }
         }

         void image::crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col) {
             // Crop coordinates are one-based and inclusive.
             if (start_row == 0 || start_col == 0 || stop_row < start_row ||
                 stop_col < start_col || stop_row > m_height || stop_col > m_width) {
                 throw std::out_of_range("crop coordinates");
             }
             std::vector<std::vector<pixel> > new_matrix(stop_row - start_row + 1);
             for (std::size_t r = start_row - 1; r < stop_row; ++r) {
                 for (std::size_t c = start_col - 1; c < stop_col; ++c) {
                     new_matrix[r - (start_row - 1)].push_back(matrix[r][c]);
                 }
             }
             m_height = stop_row - start_row + 1;
             m_width = stop_col - start_col + 1;
             matrix = new_matrix;
         }

         void image::swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2) {
             pixel temp = { matrix[row1][col1].r, matrix[row1][col1].g,  matrix[row1][col1].b };
             matrix[row1][col1] = matrix[row2][col2];
             matrix[row2][col2] = temp;
         }

         void image::flip_horizontal() {
             for (std::size_t r = 0; r < m_height; ++r) {
                 std::size_t start = 0;
                 std::size_t end = m_width == 0 ? 0 : m_width - 1;
                 while (start < end) {
                     swap_pixel(r, start, r, end);
                     ++start;
                     --end;
                 }
             }
         }

         void image::flip_vertical() {
             for (std::size_t c = 0; c < m_width; ++c) {
                 std::size_t start = 0;
                 std::size_t end = m_height == 0 ? 0 : m_height - 1;
                 while (start < end) {
                     swap_pixel(start, c, end, c);
                     ++start;
                     --end;
                 }
             }
         }


      .. tb-code:: cpp
         :name: c192_cp_12_ac_9a
         :caption: Example c192_cp_12_ac_9a
         :run-after: c192_cp_12_ac_9a-support

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
             std::size_t m_height;
             std::size_t m_width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
             void swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2);
             void flip_horizontal();
             void flip_vertical();
             void create_border(pixel p);
         };

         void image::create_border(pixel p) {
             if (m_height == 0 || m_width == 0) return;
             for (std::size_t r = 0; r < m_height; ++r) {
                 matrix[r][0] = p;
                 matrix[r][m_width - 1] = p;
             }
             for (std::size_t c = 0; c < m_width; ++c) {
                 matrix[0][c] = p;
                 matrix[m_height - 1][c] = p;
             }
         }

         int main() {
             std::vector<std::vector<pixel> > matrix = { { { 25, 65, 23 }, { 73, 56, 24 }, { 255, 255, 255 }, { 253, 61, 56 } },
                                               { { 50, 50, 50 }, { 145, 52, 102 }, { 2, 0, 25 }, { 52, 47, 35 } },
                                               { { 45, 34, 100 }, { 213, 67, 45 }, { 2, 45, 255 }, { 34, 16, 76 } },
                                               { { 2, 2, 78 }, { 164, 16, 23 }, { 5, 255, 25 }, { 32, 65, 34 } },
                                               { { 150, 150, 150 }, { 241, 42, 64 }, { 1, 4, 255 }, { 16, 73, 84 } } };
             image image = { 5, 4, matrix };
             image.print_image();
             cout << '\n';
             pixel p = { 0, 0, 0 };
             image.create_border(p);
             image.print_image();
         }

.. _vectors-objects-additional-coding-exercises:

Additional coding exercises
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. tb-group::
   :name: c192_cp_12_ac_2_q

   .. tb-tab:: Question

       An image is just a matrix of pixels. Write the ``struct`` definition for ``image``,
       which should store information about its height and width and contain a matrix
       of ``pixel``\s. Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_2q
         :caption: Example c192_cp_12_ac_2q

         #include <iostream>
         #include <vector>

         struct pixel {
             int r;
             int g;
             int b;
         };

         // Write your code for the struct image here.
.. tb-group::
   :name: c192_cp_12_ac_4_q

   .. tb-tab:: Question

       Now let's print an ``image``. Unfortunately we can't print out the actual
       image to the terminal, but we can print out the ``pixel``\s in the ``image``
       matrix. Write the ``image`` member function ``print_image``.
       Separate pixels in the same row with a space and add a new line
       at the end of each row. Use the ``print_pixel`` function we created previously.
       Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_4q-support
         :hidden:

         void pixel::print_pixel() {
             std::cout << '('<< r << ", " << g << ", " << b << ')';
         }

      .. tb-code:: cpp
         :name: c192_cp_12_ac_4q
         :caption: Example c192_cp_12_ac_4q
         :run-after: c192_cp_12_ac_4q-support

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
             std::size_t m_height;
             std::size_t m_width;
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
.. tb-group::
   :name: c192_cp_12_ac_6_q

   .. tb-tab:: Question

       Let's write a ``swap_pixel`` member function for ``image``. ``swap_pixel``
       takes two pairs of row indices and column indices from a matrix and swaps the two
       ``pixel``\s at those locations. Note that these indices are 0-indexed, unlike the
       previous ``crop_index`` parameters. Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_6q-support
         :hidden:

         void pixel::print_pixel() {
             cout << '('<< r << ", " << g << ", " << b << ')';
         }

         void image::print_image() {
             for (std::size_t r = 0; r < m_height; ++r) {
             for (std::size_t c = 0; c < m_width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
             }
         }

         void image::crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col) {
             // Crop coordinates are one-based and inclusive.
             if (start_row == 0 || start_col == 0 || stop_row < start_row ||
                 stop_col < start_col || stop_row > m_height || stop_col > m_width) {
                 throw std::out_of_range("crop coordinates");
             }
             std::vector<std::vector<pixel> > new_matrix(stop_row - start_row + 1);
             for (std::size_t r = start_row - 1; r < stop_row; ++r) {
                 for (std::size_t c = start_col - 1; c < stop_col; ++c) {
                     new_matrix[r - (start_row - 1)].push_back(matrix[r][c]);
                 }
             }
             m_height = stop_row - start_row + 1;
             m_width = stop_col - start_col + 1;
             matrix = new_matrix;
         }

      .. tb-code:: cpp
         :name: c192_cp_12_ac_6q
         :caption: Example c192_cp_12_ac_6q
         :run-after: c192_cp_12_ac_6q-support

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
             std::size_t m_height;
             std::size_t m_width;
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
             cout << '\n';
             image.swap_pixel(0, 0, 0, 2);
             image.print_image();
         }
.. tb-group::
   :name: c192_cp_12_ac_8_q

   .. tb-tab:: Question

       Oops! Somehow our image came out upside down. Let's write
       the ``image`` member function ``flip_vertical``, which
       reverts an image to be right side up.
       Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_8q-support
         :hidden:

         void pixel::print_pixel() {
             cout << '('<< r << ", " << g << ", " << b << ')';
         }

         void image::print_image() {
             for (std::size_t r = 0; r < m_height; ++r) {
             for (std::size_t c = 0; c < m_width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
             }
         }

         void image::crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col) {
             // Crop coordinates are one-based and inclusive.
             if (start_row == 0 || start_col == 0 || stop_row < start_row ||
                 stop_col < start_col || stop_row > m_height || stop_col > m_width) {
                 throw std::out_of_range("crop coordinates");
             }
             std::vector<std::vector<pixel> > new_matrix(stop_row - start_row + 1);
             for (std::size_t r = start_row - 1; r < stop_row; ++r) {
                 for (std::size_t c = start_col - 1; c < stop_col; ++c) {
                     new_matrix[r - (start_row - 1)].push_back(matrix[r][c]);
                 }
             }
             m_height = stop_row - start_row + 1;
             m_width = stop_col - start_col + 1;
             matrix = new_matrix;
         }

         void image::swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2) {
             pixel temp = { matrix[row1][col1].r, matrix[row1][col1].g,  matrix[row1][col1].b };
             matrix[row1][col1] = matrix[row2][col2];
             matrix[row2][col2] = temp;
         }

         void image::flip_horizontal() {
             for (std::size_t r = 0; r < m_height; ++r) {
                 std::size_t start = 0;
                 std::size_t end = m_width == 0 ? 0 : m_width - 1;
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
             std::size_t m_height;
             std::size_t m_width;
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
             cout << '\n';
             image.flip_vertical();
             image.print_image();
         }
.. tb-group::
   :name: c192_cp_12_ac_10_q

   .. tb-tab:: Question

       Let's return our image to the state of a clean slate. Write the
       function ``clear_image``, which sets the color of every ``pixel``
       to white. Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_12_ac_10q-support
         :hidden:

         void pixel::print_pixel() {
             cout << '('<< r << ", " << g << ", " << b << ')';
         }

         void image::print_image() {
             for (std::size_t r = 0; r < m_height; ++r) {
             for (std::size_t c = 0; c < m_width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
             }
         }

         void image::crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col) {
             // Crop coordinates are one-based and inclusive.
             if (start_row == 0 || start_col == 0 || stop_row < start_row ||
                 stop_col < start_col || stop_row > m_height || stop_col > m_width) {
                 throw std::out_of_range("crop coordinates");
             }
             std::vector<std::vector<pixel> > new_matrix(stop_row - start_row + 1);
             for (std::size_t r = start_row - 1; r < stop_row; ++r) {
                 for (std::size_t c = start_col - 1; c < stop_col; ++c) {
                     new_matrix[r - (start_row - 1)].push_back(matrix[r][c]);
                 }
             }
             m_height = stop_row - start_row + 1;
             m_width = stop_col - start_col + 1;
             matrix = new_matrix;
         }

         void image::swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2) {
             pixel temp = { matrix[row1][col1].r, matrix[row1][col1].g,  matrix[row1][col1].b };
             matrix[row1][col1] = matrix[row2][col2];
             matrix[row2][col2] = temp;
         }

         void image::flip_horizontal() {
             for (std::size_t r = 0; r < m_height; ++r) {
                 std::size_t start = 0;
                 std::size_t end = m_width == 0 ? 0 : m_width - 1;
                 while (start < end) {
                     swap_pixel(r, start, r, end);
                     ++start;
                     --end;
                 }
             }
         }

         void image::flip_vertical() {
             for (std::size_t c = 0; c < m_width; ++c) {
                 std::size_t start = 0;
                 std::size_t end = m_height == 0 ? 0 : m_height - 1;
                 while (start < end) {
                     swap_pixel(start, c, end, c);
                     ++start;
                     --end;
                 }
             }
         }

         void image::create_border(pixel p) {
             if (m_height == 0 || m_width == 0) return;
             for (std::size_t r = 0; r < m_height; ++r) {
                 matrix[r][0] = p;
                 matrix[r][m_width - 1] = p;
             }
             for (std::size_t c = 0; c < m_width; ++c) {
                 matrix[0][c] = p;
                 matrix[m_height - 1][c] = p;
             }
         }

      .. tb-code:: cpp
         :name: c192_cp_12_ac_10q
         :caption: Example c192_cp_12_ac_10q
         :run-after: c192_cp_12_ac_10q-support

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
             std::size_t m_height;
             std::size_t m_width;
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
             cout << '\n';
             image.clear_image();
             image.print_image();
         }
.. tb-group::
   :name: c192_mucp_12_1_ac

   .. tb-tab:: Question

       Let's write the struct definition for ``song``. song should have
       instance variables title, artist, and num_likes.

      .. tb-code:: cpp
         :name: c192_mucp_12_1_ac_q
         :caption: Example c192_mucp_12_1_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to define the ``song`` struct.

      .. tb-code:: cpp
         :name: c192_mucp_12_1_ac_a
         :caption: Example c192_mucp_12_1_ac_a

         #include <cstddef>
         #include <string>
         #include <iostream>

         struct song {
             std::string title;
             std::string artist;
             std::size_t num_likes;
         };
.. tb-group::
   :name: c192_mucp_12_2_ac

   .. tb-tab:: Question

       Let's make an album! Write the struct definition for
       ``album``, which should have instance variables name, year and
       a vector of Songs.

      .. tb-code:: cpp
         :name: c192_mucp_12_2_ac_q
         :caption: Example c192_mucp_12_2_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to define the ``album`` struct.

      .. tb-code:: cpp
         :name: c192_mucp_12_2_ac_a
         :caption: Example c192_mucp_12_2_ac_a

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct song {
             std::string title;
             std::string artist;
             std::size_t num_likes;
         };

         struct album {
             std::string name;
             int m_year;
             std::vector<song> songs;
         };
.. tb-group::
   :name: c192_mucp_12_3_ac

   .. tb-tab:: Question

       Two Songs are equal if the title and artist of the Songs are equal.
       Write the function ``song_equal``, which takes two Songs as parameters
       and returns true if they are equal.

      .. tb-code:: cpp
         :name: c192_mucp_12_3_ac_q
         :caption: Example c192_mucp_12_3_ac_q

         #include <iostream>

         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``song_equal`` function.

      .. tb-code:: cpp
         :name: c192_mucp_12_3_ac_a
         :caption: Example c192_mucp_12_3_ac_a

         #include <cstddef>
         #include <string>
         #include <iostream>

         struct song {
             std::string title;
             std::string artist;
             std::size_t num_likes;
         };

         bool song_equal (const song& a, const song& b) {
             if (a.title == b.title && a.artist == b.artist) {
                 return true;
             }
             else {
                 return false;
             }
         }
.. tb-group::
   :name: c192_mucp_12_4_ac

   .. tb-tab:: Question

       What if we'd like to search an album for our favorite song?
       Write the ``album`` member function search_album which takes a
       song as a parameter and returns the location of the song in
       the album. If the song isn't found, return -1. Use the
       song_equal function we defined earlier!

      .. tb-code:: cpp
         :name: c192_mucp_12_4_ac_q
         :caption: Example c192_mucp_12_4_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``album`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_12_4_ac_a
         :caption: Example c192_mucp_12_4_ac_a

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct song {
             std::string title;
             std::string artist;
             std::size_t num_likes;
         };

         struct album {
             std::string name;
             int m_year;
             std::vector<song> songs;
         public:
             std::ptrdiff_t search_album(const song& a);
         };

         std::ptrdiff_t album::search_album (const song& a) {
             for (std::size_t i = 0; i < songs.size(); ++i) {
                 if ((songs[i].title == a.title && songs[i].artist == a.artist)) {
                     return static_cast<std::ptrdiff_t>(i);
                 }
             }
             return -1;
         }
.. tb-group::
   :name: c192_mucp_12_5_ac

   .. tb-tab:: Question

       What's the most popular song within an album? Let's write
       the ``album`` member function most_liked_song, which prints out
       the information of the most liked song in the format "The most
       liked song is title by artist with num_likes likes."

      .. tb-code:: cpp
         :name: c192_mucp_12_5_ac_q
         :caption: Example c192_mucp_12_5_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``album`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_12_5_ac_a
         :caption: Example c192_mucp_12_5_ac_a

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>
         using std::cout;

         struct song {
             std::string title;
             std::string artist;
             std::size_t num_likes;
         };

         struct album {
             std::string name;
             int m_year;
             std::vector<song> songs;
         public:
             void most_liked_song();
         };

         void album::most_liked_song () {
             if (songs.empty()) { cout << "The album is empty.\n"; return; }
             std::size_t max_index = 0;
             std::size_t max_likes = 0;
             for (std::size_t i = 0; i < songs.size(); ++i) {
                 if (songs[i].num_likes > max_likes) {
                     max_index = i;
                     max_likes = songs[i].num_likes;
                 }
             }
             cout << "The most liked song is " << songs[max_index].title;
             cout << " by " << songs[max_index].artist << " with ";
             cout << songs[max_index].num_likes << " likes." << '\n';
         }
.. tb-group::
   :name: c192_mucp_12_6_ac

   .. tb-tab:: Question

       Let's write the struct definition for ``product``. ``product`` should have
       instance variables name and price.

      .. tb-code:: cpp
         :name: c192_mucp_12_6_ac_q
         :caption: Example c192_mucp_12_6_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to define the ``product`` struct.

      .. tb-code:: cpp
         :name: c192_mucp_12_6_ac_a
         :caption: Example c192_mucp_12_6_ac_a

         #include <string>
         #include <iostream>

         struct product {
             std::string name;
             double price;
         };
.. tb-group::
   :name: c192_mucp_12_7_ac

   .. tb-tab:: Question

       Let's make a shopping list! Write the struct definition for
       ``list``, which should have instance variables type and
       a vector of Products.

      .. tb-code:: cpp
         :name: c192_mucp_12_7_ac_q
         :caption: Example c192_mucp_12_7_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to define the ``list`` struct.

      .. tb-code:: cpp
         :name: c192_mucp_12_7_ac_a
         :caption: Example c192_mucp_12_7_ac_a

         #include <string>
         #include <iostream>
         #include <vector>

         struct product {
             std::string name;
             double price;
         };

         struct list {
             std::string type;
             std::vector<product> products;
         };
.. tb-group::
   :name: c192_mucp_12_8_ac

   .. tb-tab:: Question

       Two Products are equal if the name and price of the Products are equal.
       Write the function product_equal, which takes two Products as parameters
       and returns true if they are equal. What if we want to check to see if
       we have bananas in our shopping list? Write the list member function
       ``search_list``, which takes a product as a parameter and returns the location
       of the product in the list. Return -1 if it's not in the list.

      .. tb-code:: cpp
         :name: c192_mucp_12_8_ac_q
         :caption: Example c192_mucp_12_8_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``search_list`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_12_8_ac_a
         :caption: Example c192_mucp_12_8_ac_a

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct product {
             std::string name;
             double price;
         };

         bool product_equal (const product& a, const product& b) {
             if (a.name == b.name && a.price == b.price) {
                 return true;
             }
             else {
                 return false;
             }
         }

         struct list {
             std::string type;
             std::vector<product> products;
             std::ptrdiff_t search_list(const product& a);
         };

         std::ptrdiff_t list::search_list (const product& a) {
             for (std::size_t i = 0; i < products.size(); ++i) {
                 if (product_equal (products[i], a)) {
                     return static_cast<std::ptrdiff_t>(i);
                 }
             }
             return -1;
         }
.. tb-group::
   :name: c192_mucp_12_9_ac

   .. tb-tab:: Question

       time to checkout! Write the list member function ``total_price``
       which calculates and returns the total price of all the Products.

      .. tb-code:: cpp
         :name: c192_mucp_12_9_ac_q
         :caption: Example c192_mucp_12_9_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``total_price`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_12_9_ac_a
         :caption: Example c192_mucp_12_9_ac_a

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct product {
             std::string name;
             double price;
         };

         struct list {
             std::string type;
             std::vector<product> products;
         public:
             double total_price();
         };

         double list::total_price () {
             double total = 0;
             for (std::size_t i = 0; i < products.size(); ++i) {
                 total += products[i].price;
             }
             return total;
         }
.. tb-group::
   :name: c192_mucp_12_10_ac

   .. tb-tab:: Question

       Oops! We made a mistake and grabbed pineapple pizza.
       What if we want to remove an product from our list?
       Write the list member function ``remove_product``, which takes
       an index as a parameter and removes it. Then it fills
       the gap with the last product in the list.

      .. tb-code:: cpp
         :name: c192_mucp_12_10_ac_q
         :caption: Example c192_mucp_12_10_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``remove_product`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_12_10_ac_a
         :caption: Example c192_mucp_12_10_ac_a

         #include <stdexcept>
         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct product {
             std::string name;
             double price;
         };

         struct list {
             std::string type;
             std::vector<product> products;
         public:
             void remove_product(std::size_t index);
         };

         void list::remove_product (std::size_t index) {
             if (index >= products.size()) throw std::out_of_range("product index");
             products[index] = products.back();
             products.pop_back();
         }
