Activecode Exercises
--------------------

Answer the following **Activecode** questions to assess what you have learned in this chapter.

.. tb-group::
   :name: c192_mucp_14_1_ac

   .. tb-tab:: Question

       Let's write the class definition for ``circle``. ``circle`` should have its
       radius stored in a private member variable. Also write the constructor
       for ``circle``, which takes a radius as a parameter, in addition to the
       public member function ``calculate_area``, which returns the area of
       the ``circle``. Make sure to include the ``private`` and ``public`` keywords!
       Use 3.14 for the value of pi.

      .. tb-code:: cpp
         :name: c192_mucp_14_1_ac_q
         :caption: Example c192_mucp_14_1_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to wrte the class definition and constructor for ``circle``.

      .. tb-code:: cpp
         :name: c192_mucp_14_11_ac_a
         :caption: Example c192_mucp_14_11_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         class circle {
             private:
                 double radius;
             public:
                 circle (double r) { radius = r; }
                 double calculate_area () { return 3.14 * radius * radius; }
         };

.. tb-group::
   :name: c192_mucp_14_2_ac

   .. tb-tab:: Question

       Now that we have our ``circle`` class, let's write some accessor
       functions! Write the ``circle`` member functions ``get_radius``
       and ``set_radius``. It doesn't make sense for a ``circle``'s
       radius to be negative, so in your ``set_radius`` function,
       output an error message if the given radius is negative.

      .. tb-code:: cpp
         :name: c192_mucp_14_2_ac_q
         :caption: Example c192_mucp_14_2_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the accessor functions for ``get_radius`` and ``set_radius``.

      .. tb-code:: cpp
         :name: c192_mucp_14_2_ac_a
         :caption: Example c192_mucp_14_2_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         class circle {
             private:
                 double radius;
             public:
                 circle (double r) { radius = r; }
                 double calculate_area () { return 3.14 * radius * radius; }
                 double get_radius () {
                     return radius;
                 }
                 void set_radius (double r) {
                     if (r < 0) { std::cout << "Error! Cannot have a negative radius!" << std::endl; }
                     else { radius = r; }
                 }
         };

.. tb-group::
   :name: c192_mucp_14_3_ac

   .. tb-tab:: Question

       Write a ``main``. in ``main``, create a ``circle`` with radius 2.4
       and output the radius. Then change the radius to 3.6 and output

      .. tb-code:: cpp
         :name: c192_mucp_14_3_ac_q
         :caption: Example c192_mucp_14_3_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the code.

      .. tb-code:: cpp
         :name: c192_mucp_14_3_ac_a
         :caption: Example c192_mucp_14_3_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         class circle {
             private:
                 double radius;
             public:
                 circle (double r) { radius = r; }
                 double calculate_area () { return 3.14 * radius * radius; }
                 double get_radius () {
                     return radius;
                 }
                 void set_radius (double r) {
                     if (r < 0) { std::cout << "Error! Cannot have a negative radius!" << std::endl; }
                     else { radius = r; }
                 }
         };

         int main() {
             circle c(2.4);
             std::cout << "Radius: " << c.get_radius () << std::endl;
             c.set_radius (3.6);
             std::cout << "New radius: " << c.get_radius () << std::endl;
         }

.. tb-group::
   :name: c192_mucp_14_4_ac

   .. tb-tab:: Question

       A ``rectangle`` can be constructed given only two points. First,
       write the class definition for ``point``, which stores an x and
       a y value in private member variables. Also write the default constructor, which
       sets x and y to 0, and a constructor that takes in an x_val and y_val.
       in addition, write its accessor functions,
       ``get_x``, ``get_y``, ``set_x``, and ``set_y``.

      .. tb-code:: cpp
         :name: c192_mucp_14_4_ac_q
         :caption: Example c192_mucp_14_4_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the code.

      .. tb-code:: cpp
         :name: c192_mucp_14_4_ac_a
         :caption: Example c192_mucp_14_4_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         class point {
             private:
                 double x, y;
             public:
                 point () { x = 0; y = 0; }
                 point (double x_val, double y_val) { x = x_val; y = y_val; }
                 double get_x () { return x; }
                 double get_y () { return y; }
                 void set_x (double x_val) { x = x_val; }
                 void set_y (double y_val) { y = y_val; }
         };

.. tb-group::
   :name: c192_mucp_14_5_ac

   .. tb-tab:: Question

       Now that we've defined the ``point`` class, we can go back to
       writing the ``rectangle`` class. ``rectangle`` should store
       it's upper-left and lower-right points as private member variables.
       Write accessor functions for these variables after the constructor.
       It should also have length and height stored as public member variables.
       Also write a constructor that
       takes an upper-left point and a lower-right point as parameters.

      .. tb-code:: cpp
         :name: c192_mucp_14_5_ac_q
         :caption: Example c192_mucp_14_5_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``rectangle`` class.

      .. tb-code:: cpp
         :name: c192_mucp_14_5_ac_a
         :caption: Example c192_mucp_14_5_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         class point {
             private:
                 double x, y;
             public:
                 point () { x = 0; y = 0; }
                 point (double x_val, double y_val) { x = x_val; y = y_val; }
                 double get_x () { return x; }
                 double get_y () { return y; }
                 void set_x (double x_val) { x = x_val; }
                 void set_y (double y_val) { y = y_val; }
         };

         class rectangle {
             private:
                 point upper_left, lower_right;
             public:
                 double length, height;
                 rectangle (point up_left, point low_right) { upper_left = up_left; lower_right = low_right; }
                 point get_upper_left () { return upper_left; }
                 point get_lower_right () { return lower_right; }
                 void set_upper_left (point p) { upper_left = p; }
                 void set_lower_right (point p) { lower_right = p; }
         };

.. tb-group::
   :name: c192_mucp_14_6_ac

   .. tb-tab:: Question

       Write the ``rectangle`` member function ``calculate_sides``, which finds
       the length and height of the rectangle using the stored ``point``s.
       Afterwards, write the ``rectangle`` member function ``calculate_area``,
       which returns the area of the rectangle.

      .. tb-code:: cpp
         :name: c192_mucp_14_6_ac_q
         :caption: Example c192_mucp_14_6_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``calculate_sides`` and ``calculate_area`` member functions.

      .. tb-code:: cpp
         :name: c192_mucp_14_6_ac_a
         :caption: Example c192_mucp_14_6_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         class point {
             private:
                 double x, y;
             public:
                 point () { x = 0; y = 0; }
                 point (double x_val, double y_val) { x = x_val; y = y_val; }
                 double get_x () { return x; }
                 double get_y () { return y; }
                 void set_x (double x_val) { x = x_val; }
                 void set_y (double y_val) { y = y_val; }
         };

         class rectangle {
             private:
                 point upper_left, lower_right;
             public:
                 double length, height;
                 rectangle (point up_left, point low_right) { upper_left = up_left; lower_right = low_right; }
                 point get_upper_left () { return upper_left; }
                 point get_lower_right () { return lower_right; }
                 void set_upper_left (point p) { upper_left = p; }
                 void set_lower_right (point p) { lower_right = p; }
         public:
             void calculate_sides();
             double calculate_area();
         };

         void rectangle::calculate_sides () {
             length = get_lower_right().get_x() - get_upper_left().get_x();
             height = get_upper_left().get_y() - get_lower_right().get_y();
         }

         double rectangle::calculate_area () {
             return length * height;
         }

.. tb-group::
   :name: c192_mucp_14_7_ac

   .. tb-tab:: Question

       Write a ``main`` in ``main``, create a ``rectangle`` with corners
       at (2.5, 7.5) and (8, 1.5). Print out the length and height, calculate the area,
       and print out the area. Then change the upper_left corner to be at (4.2, 10.7) and
       print out the new area.

      .. tb-code:: cpp
         :name: c192_mucp_14_7_ac_q
         :caption: Example c192_mucp_14_7_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to create this ``rectangle``.

      .. tb-code:: cpp
         :name: c192_mucp_14_7_ac_a
         :caption: Example c192_mucp_14_7_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         class point {
             private:
                 double x, y;
             public:
                 point () { x = 0; y = 0; }
                 point (double x_val, double y_val) { x = x_val; y = y_val; }
                 double get_x () { return x; }
                 double get_y () { return y; }
                 void set_x (double x_val) { x = x_val; }
                 void set_y (double y_val) { y = y_val; }
         };

         class rectangle {
             private:
                 point upper_left, lower_right;
             public:
                 double length, height;
                 rectangle (point up_left, point low_right) { upper_left = up_left; lower_right = low_right; }
                 point get_upper_left () { return upper_left; }
                 point get_lower_right () { return lower_right; }
                 void set_upper_left (point p) { upper_left = p; }
                 void set_lower_right (point p) { lower_right = p; }
         public:
             void calculate_sides();
             double calculate_area();
         };

         void rectangle::calculate_sides () {
             length = get_lower_right().get_x() - get_upper_left().get_x();
             height = get_upper_left().get_y() - get_lower_right().get_y();
         }

         double rectangle::calculate_area () {
             return length * height;
         }

         int main() {
             point p1(2.5, 7.5);
             point p2(8, 1.5);
             rectangle r(p1, p2);
             r.calculate_sides();
             std::cout << "Length: " << r.length << ", Height: " << r.height << std::endl;
             std::cout << "Area: " << r.calculate_area() << std::endl;
             point p3(4.2, 10.7);
             r.set_upper_left(p3);
             r.calculate_sides();
             std::cout << "New area: " << r.calculate_area() << std::endl;
         }

.. tb-group::
   :name: c192_mucp_14_8_ac

   .. tb-tab:: Question

       Let's write the ``date`` class. ``date`` stores information
       about the day, month, and year in private variables, in addition to a ``vector``
       of the number of days in each month. Write accessor functions
       for each variable, keeping in mind the valid values each variable can take.
       in addition, write the default constructor, which initializes
       the date to January 1, 2000. Write another constructor which takes in a day,
       month, and year in that order.

      .. tb-code:: cpp
         :name: c192_mucp_14_8_ac_q
         :caption: Example c192_mucp_14_8_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``date`` class and addtional constructors.

      .. tb-code:: cpp
         :name: c192_mucp_14_8_ac_a
         :caption: Example c192_mucp_14_8_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>

         class date {
             private:
                 int day, month, year;
                 std::vector<int> days_in_month = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
             public:
                 date () { day = 1; month = 1; year = 2000; }
                 date (int d, int m, int y) { day = d; month = m; year = y; }
                 int get_day () { return day; }
                 int get_month () { return month; }
                 int get_year () { return year; }
                 void set_day (int d) { if (d > 0 && d < 32) day = d; }
                 void set_month (int m) { if (m > 0 && m < 13) month = m; }
                 void set_year (int y) { year = y; }
         };

.. tb-group::
   :name: c192_mucp_14_9_ac

   .. tb-tab:: Question

       Let's write the ``date`` member function, ``print_date``,
       which prints the date out in the following format: month/day/year CE/BCE
       depending on whether the year is negative or not.

      .. tb-code:: cpp
         :name: c192_mucp_14_9_ac_q
         :caption: Example c192_mucp_14_9_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``print_date`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_14_9_ac_a
         :caption: Example c192_mucp_14_9_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>

         class date {
             private:
                 int day, month, year;
                 std::vector<int> days_in_month = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
             public:
                 date () { day = 1; month = 1; year = 2000; }
                 date (int d, int m, int y) { day = d; month = m; year = y; }
                 int get_day () { return day; }
                 int get_month () { return month; }
                 int get_year () { return year; }
                 void set_day (int d) { if (d > 0 && d < 32) day = d; }
                 void set_month (int m) { if (m > 0 && m < 13) month = m; }
                 void set_year (int y) { year = y; }
         public:
             void print_date();
         };

         void date::print_date () {
             if (get_year() < 0) {
                 std::cout << get_month() << "/" << get_day() << "/" << -get_year() << " BCE" << std::endl;
             }
             else {
                 std::cout << get_month() << "/" << get_day() << "/" << get_year() << " CE" << std::endl;
             }
         }

.. tb-group::
   :name: c192_mucp_14_10_ac

   .. tb-tab:: Question

       Write the ``date`` member function ``is_leap_year``, which returns true if
       the year is a leap year. Then write the ``date`` member function ``last_day_in_month``,
       which returns the last day in the ``date``'s month.

      .. tb-code:: cpp
         :name: c192_mucp_14_10_ac_q
         :caption: Example c192_mucp_14_10_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is onne way to write the ``is_leap_year`` and ``last_day_in_month`` member functions.

      .. tb-code:: cpp
         :name: c192_mucp_14_10_ac_a
         :caption: Example c192_mucp_14_10_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>

         class date {
             private:
                 int day, month, year;
                 std::vector<int> days_in_month = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
             public:
                 date () { day = 1; month = 1; year = 2000; }
                 date (int d, int m, int y) { day = d; month = m; year = y; }
                 int get_day () { return day; }
                 int get_month () { return month; }
                 int get_year () { return year; }
                 void set_day (int d) { if (d > 0 && d < 32) day = d; }
                 void set_month (int m) { if (m > 0 && m < 13) month = m; }
                 void set_year (int y) { year = y; }
         public:
             bool is_leap_year();
             int last_day_in_month();
         };

         bool date::is_leap_year () {
             if (get_year() % 4 != 0) { return false; }
             else if (get_year() % 100 != 0) { return true; }
             else if (get_year() % 400 != 0) { return false; }
             else { return true; }
         }

         int date::last_day_in_month () {
             if (is_leap_year() && get_month() == 2) {
                 return days_in_month[get_month() - 1] + 1;
             } else {
                 return days_in_month[get_month() - 1];
             }
         }

