Mixed Up Code Practice
----------------------

.. tb-parsons::
   :name: c192_mucp_14_1
   :no-indent:

   Let's write the class definition for ``circle``. ``circle`` should have its
   radius stored in a private member variable. Also write the constructor
   for ``circle``, which takes a radius as a parameter, in addition to the
   public member function ``calculate_area``, which returns the area of
   the ``circle``. Make sure to include the ``private`` and ``public`` keywords!
   Use 3.14 for the value of pi. Put the necessary
   blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      class circle {
      {{endgroup}}
      {{distractor}}
      {{group}}
      struct circle {  #distractor
      {{endgroup}}
      {{group}}
         private:
      {{endgroup}}
      {{distractor}}
      {{group}}
         private {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         }  #distractor
      {{endgroup}}
      {{group}}
            double radius;
      {{endgroup}}
      {{group}}
         public:
      {{endgroup}}
      {{group}}
            circle (double r) { radius = r; }
      {{endgroup}}
      {{distractor}}
      {{group}}
            circle (int r) { radius = r; }  #distractor
      {{endgroup}}
      {{group}}
            double calculate_area () { return 3.14 * radius * radius; }
      };
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_14_2
   :no-indent:

   Now that we have our ``circle`` class, let's write some accessor
   functions! Write the ``circle`` member functions ``get_radius``
   and ``set_radius``. It doesn't make sense for a ``circle``'s
   radius to be negative, so in your ``set_radius`` function,
   output an error message if the given radius is negative.
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      class circle {
         private:
            double radius;
         public:
            circle (double r) { radius = r; }
            double calculate_area () { return 3.14 * radius * radius; }
      {{endgroup}}
      {{group}}
            double get_radius () {
      {{endgroup}}
      {{distractor}}
      {{group}}
            void get_radius () {  #distractor
      {{endgroup}}
      {{group}}
               return radius;
      {{endgroup}}
      {{group}}
            }
      {{endgroup}}
      {{group}}
            void set_radius (double r) {
      {{endgroup}}
      {{distractor}}
      {{group}}
            double set_radius (double r) {  #distractor
      {{endgroup}}
      {{group}}
               if (r < 0) { std::cout << "Error! Cannot have a negative radius!" << std::endl; }
      {{endgroup}}
      {{group}}
               else { radius = r; }
      {{endgroup}}
      {{group}}
            }
      {{endgroup}}
      {{group}}
      };
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_14_3
   :no-indent:

   Write a ``main``. in ``main``, create a ``circle`` with radius 2.4
   and output the radius. Then change the radius to 3.6 and output
   the new radius. Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         circle c(2.4);
      {{endgroup}}
      {{distractor}}
      {{group}}
         circle c;  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         c.radius = 2.4;  #distractor
      {{endgroup}}
      {{group}}
         std::cout << "Radius: " << c.get_radius () << std::endl;
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::cout << "Radius: " << c.radius << std::endl;  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         c.radius = 3.6;  #distractor
      {{endgroup}}
      {{group}}
         s.set_radius (3.6);
      {{endgroup}}
      {{group}}
         std::cout << "New radius: " << c.get_radius () << std::endl;
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::cout << "New radius: " << c.radius << std::endl;  #distractor
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_14_4

   A ``rectangle`` can be constructed given only two points. First,
   write the class definition for ``point``, which stores an x and
   a y value in private member variables. Also write the default constructor, which
   sets x and y to 0, and a constructor that takes in an x_val and y_val.
   in addition, write its accessor functions,
   ``get_x``, ``get_y``, ``set_x``, and ``set_y``.
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      class point {
      {{endgroup}}
      {{group}}
         private:
      {{endgroup}}
      {{group}}
            double x, y;
      {{endgroup}}
      {{group}}
         public:
      {{endgroup}}
      {{group}}
            point () { x = 0; y = 0; }
      {{endgroup}}
      {{group}}
            point (double x_val, double y_val) { x = x_val; y = y_val; }
      {{endgroup}}
      {{group}}
            double get_x () { return x; }
      {{endgroup}}
      {{group}}
            double get_y () { return y; }
      {{endgroup}}
      {{group}}
            void set_x (double x_val) { x = x_val; }
      {{endgroup}}
      {{group}}
            void set_y (double y_val) { y = y_val; }
      {{endgroup}}
      {{group}}
      };
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_14_5

   Now that we've defined the ``point`` class, we can go back to
   writing the ``rectangle`` class. ``rectangle`` should store
   it's upper-left and lower-right points as private member variables.
   Write accessor functions for these variables after the constructor.
   It should also have length and height stored as public member variables.
   Also write a constructor that
   takes an upper-left point and a lower-right point as parameters.

   .. code-block:: c++

      {{group}}
      class rectangle {
      {{endgroup}}
      {{group}}
         private:
      {{endgroup}}
      {{group}}
            point upper_left, lower_right;
      {{endgroup}}
      {{group}}
         public:
      {{endgroup}}
      {{group}}
            double length, height;
      {{endgroup}}
      {{group}}
            rectangle (point up_left, point low_right) { upper_left = up_left; lower_right = low_right; }
      {{endgroup}}
      {{group}}
            point get_upper_left () { return upper_left; }
      {{endgroup}}
      {{group}}
            point get_lower_right () { return lower_right; }
      {{endgroup}}
      {{group}}
            void set_upper_left (point p) { upper_left = p; }
      {{endgroup}}
      {{group}}
            void set_lower_right (point p) { lower_right = p; }
      {{endgroup}}
      {{group}}
      };
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_14_6

   Write the ``rectangle`` member function ``calculate_sides``, which finds
   the length and height of the rectangle using the stored ``point``s.
   Afterwards, write the ``rectangle`` member function ``calculate_area``,
   which returns the area of the rectangle.

   .. code-block:: c++

      {{group}}
      void rectangle::calculate_sides () {
      {{endgroup}}
      {{group}}
      double rectangle::calculate_sides () {
      {{endgroup}}
      {{group}}
         length = get_lower_right().get_x() - get_upper_left().get_x();
      {{endgroup}}
      {{group}}
         height = get_upper_left().get_y() - get_lower_right().get_y();
      {{endgroup}}
      {{distractor}}
      {{group}}
         length = lower_right.x - upper_left.x;  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         height = upper_left.y - lower_right.y;  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         return length;  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         return height;  #distractor
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
      {{group}}
      double rectangle::calculate_area () {
      {{endgroup}}
      {{group}}
         return length * height;
      {{endgroup}}
      {{distractor}}
      {{group}}
         return get_length() * get_height();  #distractor
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_14_7

   Write a ``main`` in ``main``, create a ``rectangle`` with corners
   at (2.5, 7.5) and (8, 1.5). Print out the length and height, calculate the area,
   and print out the area. Then change the upper_left corner to be at (4.2, 10.7) and
   print out the new area.

   .. code-block:: c++

      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         point p1(2.5, 7.5);
      {{endgroup}}
      {{group}}
         point p2(8, 1.5);
      {{endgroup}}
      {{group}}
         rectangle r(p1, p2);
      {{endgroup}}
      {{distractor}}
      {{group}}
         rectangle r(p2, p1);  #distractor
      {{endgroup}}
      {{group}}
         r.calculate_sides();
      {{endgroup}}
      {{group}}
         std::cout << "Length: " << r.length << ", Height: " << r.height << std::endl;
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::cout << "Length: " << r.get_length() << ", Height: " << r.get_height() << std::endl;  #distractor
      {{endgroup}}
      {{group}}
         std::cout << "Area: " << r.calculate_area() << std::endl;
      {{endgroup}}
      {{group}}
         point p3(4.2, 10.7);
      {{endgroup}}
      {{group}}
         r.set_upper_left(p3);
      {{endgroup}}
      {{distractor}}
      {{group}}
         r.upper_left = p3;  #distractor
      {{endgroup}}
      {{group}}
         r.calculate_sides();
      {{endgroup}}
      {{group}}
         std::cout << "New area: " << r.calculate_area() << std::endl;
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_14_8

   Let's write the ``date`` class. ``date`` stores information
   about the day, month, and year in private variables, in addition to a ``vector``
   of the number of days in each month. Write accessor functions
   for each variable, keeping in mind the valid values each variable can take.
   in addition, write the default constructor, which initializes
   the date to January 1, 2000. Write another constructor which takes in a day,
   month, and year in that order.

   .. code-block:: c++

      {{group}}
      class date {
      {{endgroup}}
      {{group}}
         private:
      {{endgroup}}
      {{group}}
            int day, month, year;
      {{endgroup}}
      {{group}}
            std::vector<int> days_in_month = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
      {{endgroup}}
      {{group}}
         public:
      {{endgroup}}
      {{group}}
            date () { day = 1; month = 1; year = 2000; }
      {{endgroup}}
      {{distractor}}
      {{group}}
            date () { day = 0; month = 0; year = 0; }  #distractor
      {{endgroup}}
      {{group}}
            date (int d, int m, int y) { day = d; month = m; year = y; }
      {{endgroup}}
      {{group}}
            int get_day () { return day; }
      {{endgroup}}
      {{group}}
            int get_month () { return month; }
      {{endgroup}}
      {{group}}
            int get_year () { return year; }
      {{endgroup}}
      {{group}}
            void set_day (int d) { if (d > 0 && d < 32) day = d; }
      {{endgroup}}
      {{group}}
            void set_month (int m) { if (m > 0 && m < 13) month = m; }
      {{endgroup}}
      {{group}}
            void set_year (int y) { year = y; }
      {{endgroup}}
      {{distractor}}
      {{group}}
            void set_day (int d) { if (d > 1 && d < 31) day = d; }  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
            void set_month (int m) { if (m >= 0 && m <= 12) month = m; }  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
            void set_year (int y) { if (y >= 2000 && y < 3000) year = y; }  #distractor
      {{endgroup}}
      {{group}}
      };
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_14_9

   Let's write the ``date`` member function, ``print_date``,
   which prints the date out in the following format: month/day/year CE/BCE
   depending on whether the year is negative or not.

   .. code-block:: c++

      {{group}}
      void date::print_date () {
      {{endgroup}}
      {{group}}
         if (get_year() < 0) {
      {{endgroup}}
      {{group}}
            std::cout << get_month() << "/" << get_day() << "/" << -get_year() << " BCE" << std::endl;
      {{endgroup}}
      {{distractor}}
      {{group}}
            std::cout << month << "/" << day << "/" << year << " BCE" << std::endl;  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
            std::cout << get_month() << "/" << get_day() << "/" << get_year() << " BCE" << std::endl;  #distractor
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         else {
      {{endgroup}}
      {{group}}
            std::cout << get_month() << "/" << get_day() << "/" << get_year() << " CE" << std::endl;
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_14_10

   Write the ``date`` member function ``is_leap_year``, which returns true if
   the year is a leap year. Then write the ``date`` member function ``last_day_in_month``,
   which returns the last day in the ``date``'s month.

   .. code-block:: c++

      {{group}}
      bool date::is_leap_year () {
      {{endgroup}}
      {{group}}
         if (get_year() % 4 != 0) { return false; }
      {{endgroup}}
      {{distractor}}
      {{group}}
         if (get_year() % 4 == 0) { return false; }  #distractor
      {{endgroup}}
      {{group}}
         else if (get_year() % 100 != 0) { return true; }
      {{endgroup}}
      {{group}}
         else if (get_year() % 400 != 0) { return false; }
      {{endgroup}}
      {{group}}
         else { return true; }
      {{endgroup}}
      {{distractor}}
      {{group}}
         else { return false; }  #distractor
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
      {{group}}
      int date::last_day_in_month () {
      {{endgroup}}
      {{group}}
         if (is_leap_year() && get_month() == 2) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         if (is_leap_year()) {  #distractor
      {{endgroup}}
      {{group}}
            return days_in_month[get_month() - 1] + 1;
      {{endgroup}}
      {{group}}
         else {
      {{endgroup}}
      {{group}}
            return days_in_month[get_month() - 1];
      {{endgroup}}
      {{distractor}}
      {{group}}
            return days_in_month[get_month()];  #distractor
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

