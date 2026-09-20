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

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_12_ac_2_sq`` is represented by these exercises:

   * :ref:`c192_cp_12_ac_2q <vectors-objects-coding-practice-2>`

   * :ref:`c192_cp_12_ac_2_pp <vectors-objects-coding-practice-2>`

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

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_12_ac_4_sq`` is represented by these exercises:

   * :ref:`c192_cp_12_ac_4q <vectors-objects-coding-practice-2>`

   * :ref:`c192_cp_12_ac_4_pp <vectors-objects-coding-practice-2>`

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
             for (std::size_t r = 0; r < height; ++r) {
             for (std::size_t c = 0; c < width; ++ c) {
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
             std::size_t height;
             std::size_t width;
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
             for (std::size_t r = 0; r < height; ++r) {
             for (std::size_t c = 0; c < width; ++ c) {
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
             std::size_t height;
             std::size_t width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
         };

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

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_12_ac_6_sq`` is represented by these exercises:

   * :ref:`c192_cp_12_ac_6q <vectors-objects-coding-practice-2>`

   * :ref:`c192_cp_12_ac_6_pp <vectors-objects-coding-practice-2>`

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
             for (std::size_t r = 0; r < height; ++r) {
             for (std::size_t c = 0; c < width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
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
             std::size_t height;
             std::size_t width;
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
             for (std::size_t r = 0; r < height; ++r) {
             for (std::size_t c = 0; c < width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
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
             std::size_t height;
             std::size_t width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
             void swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2);
             void flip_horizontal();
         };

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

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_12_ac_8_sq`` is represented by these exercises:

   * :ref:`c192_cp_12_ac_8q <vectors-objects-coding-practice-2>`

   * :ref:`c192_cp_12_ac_8_pp <vectors-objects-coding-practice-2>`

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
             for (std::size_t r = 0; r < height; ++r) {
             for (std::size_t c = 0; c < width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
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
             std::size_t height;
             std::size_t width;
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
             for (std::size_t r = 0; r < height; ++r) {
             for (std::size_t c = 0; c < width; ++ c) {
                 matrix[r][c].print_pixel();
                 cout << ' ';
             }
             cout << '\n';
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
             std::size_t height;
             std::size_t width;
             std::vector<std::vector<pixel> > matrix;
             void print_image();
             void crop_image(std::size_t start_row, std::size_t stop_row, std::size_t start_col, std::size_t stop_col);
             void swap_pixel(std::size_t row1, std::size_t col1, std::size_t row2, std::size_t col2);
             void flip_horizontal();
             void flip_vertical();
             void create_border(pixel p);
         };

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

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_12_ac_10_sq`` is represented by these exercises:

   * :ref:`c192_cp_12_ac_10q <vectors-objects-coding-practice-2>`

   * :ref:`c192_cp_12_ac_10_pp <vectors-objects-coding-practice-2>`

