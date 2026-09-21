.. _classes-invariants-mixed-up-code-exercises:

Mixed-Up Code Exercises
-----------------------

Arrange the following **Mixed-Up Code** exercises to
assess what you have learned in this chapter.

.. _classes-invariants-parsons-exercises:

Parsons exercises
~~~~~~~~~~~~~~~~~

.. tb-parsons::
   :name: c192_cp_14_ac_2q_pp

    There are errors in the code below. Modify the code so that ``main`` runs
    successfully. Use the lines to construct the code, then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
       class room {
           private:
               int length;
               int width;
               int height;
      {{endgroup}}
      {{group}}
           public:
               int calculate_area () {
                   return length * width;
               }
      {{endgroup}}
      {{group}}
               int calculate_volume () {
                   return length * width * height;
               }
      {{endgroup}}
      {{group}}
               void set_length (int l) {
                   length = l;
               }
      {{endgroup}}
      {{group}}
               int get_length () const {
                   return length;
               }
      {{endgroup}}
      {{group}}
               void set_width (int w) {
                   width = w;
               }
      {{endgroup}}
      {{group}}
               int get_width () const {
                   return width;
               }
      {{endgroup}}
      {{group}}
               void set_height (int h) {
                   height = h;
               }
      {{endgroup}}
      {{group}}
               int get_height () const {
                   return height;
               }
      {{endgroup}}
      {{group}}
       };
      {{endgroup}}
      {{group}}
       int main() {
      {{endgroup}}
      {{group}}
           room r;
      {{endgroup}}
      {{group}}
           r.set_length(12);
      {{endgroup}}
      {{group}}
           r.set_width(14);
      {{endgroup}}
      {{group}}
           r.set_height(10);
      {{endgroup}}
      {{group}}
           std::cout << "The room with dimensions " << r.get_length() << ", " << r.get_width()
               << ", and " << r.get_height() << " has an area of " << r.calculate_area()
               << " and a volume of " << r.calculate_volume() << '\n';
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_14_ac_4q_pp

    in ``main`` create a ``temp`` object to calculate
    what 100 degrees Celsius is in Fahrenheit.
    Use the lines to construct the code, then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
       int main() {
      {{endgroup}}
      {{group}}
           temp t;
      {{endgroup}}
      {{group}}
           t.set_celsius(100);
      {{endgroup}}
      {{group}}
           t.set_fahrenheit(t.get_fahrenheit());
      {{endgroup}}
      {{group}}
           t.print_temp();
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_14_ac_6q_pp

    What if we had an existing ``vector`` with data that we want to copy
    into our ``my_vector``? Write a constructor that takes a ``vector``
    and copies the data into the ``elements`` vector.
    Use the lines to construct the code, then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
       my_vector (std::vector<int> vec) {
      {{endgroup}}
      {{group}}
          elements = vec;
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_14_ac_8q_pp

    Now we can write some of our own fun functions! No longer
    do we need to write ``for`` loops every time we want to
    print out a ``vector``. With ``my_vector``, we can just
    call the member function ``print``! Write the ``my_vector``
    member function ``print``, which prints out the contents
    of ``my_vector``. For example, if our ``my_vector`` contained
    the elements 2, 5, 1, and 8, ``print`` should print out
    [2, 5, 1, 8] followed by a newline. Use the lines to construct
    the code, then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
       void print() {
      {{endgroup}}
      {{group}}
          std::cout << '[';
      {{endgroup}}
      {{group}}
          for (std::size_t i = 0; i < elements.size(); ++i) {
      {{endgroup}}
      {{group}}
              if (i != 0) std::cout << ", ";
              std::cout << elements[i];
      {{endgroup}}
      {{group}}
          }
      {{endgroup}}
      {{group}}
          std::cout << ']' << '\n';
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_14_ac_10q_pp

    What if we wanted to return the largest and smallest elements in our
    ``my_vector``? Write the public member functions ``max`` and ``min``
    which calls the private member functions ``find_max`` and ``find_min``.
    ``find_max`` and ``find_min`` return the indices of the max and min
    values, and ``max`` and ``min`` call these private member functions
    and return the max and min values. Use the lines to construct the code,
    then complete the code in the correct order. Include ``<stdexcept>`` for the empty-vector check. Be sure to declare the ``max`` and ``min``
    functions in ``public`` when you complete the code.

   .. code-block:: c++

      {{group}}
       // find_max private member function
       std::size_t find_max (const std::vector<int>& vec) {
      {{endgroup}}
      {{group}}
           if (vec.empty()) throw std::out_of_range("empty vector");
           std::size_t in_max = 0;
      {{endgroup}}
      {{group}}
           int max = vec[0];
      {{endgroup}}
      {{group}}
           for (std::size_t i = 1; i < vec.size(); i++) {
      {{endgroup}}
      {{group}}
               if (vec[i] > max) {
      {{endgroup}}
      {{group}}
                   max = vec[i];
      {{endgroup}}
      {{group}}
                   in_max = i;
      {{endgroup}}
      {{group}}
               }
      {{endgroup}}
      {{group}}
           }
      {{endgroup}}
      {{group}}
           return in_max;
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
      {{group}}
       // find_min private member function
       std::size_t find_min (const std::vector<int>& vec) {
      {{endgroup}}
      {{group}}
           if (vec.empty()) throw std::out_of_range("empty vector");
           std::size_t in_min = 0;
      {{endgroup}}
      {{group}}
           int min = vec[0];
      {{endgroup}}
      {{group}}
           for (std::size_t i = 0; i < vec.size(); i++) {
      {{endgroup}}
      {{group}}
               if (vec[i] < min) {
      {{endgroup}}
      {{group}}
                   min = vec[i];
      {{endgroup}}
      {{group}}
                   in_min = i;
      {{endgroup}}
      {{group}}
               }
      {{endgroup}}
      {{group}}
           }
      {{endgroup}}
      {{group}}
           return in_min;
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
      {{group}}
       // max public member function
       int my_vector::max () {
      {{endgroup}}
      {{group}}
           return elements[find_max(elements)];
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
      {{group}}
       // min public member function
       int my_vector::min () {
      {{endgroup}}
      {{group}}
           return elements[find_min(elements)];
      {{endgroup}}
      {{group}}
       }
      {{endgroup}}
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
               if (r < 0) { std::cout << "Error! Cannot have a negative radius!" << '\n'; }
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
         std::cout << "Radius: " << c.get_radius () << '\n';
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::cout << "Radius: " << c.radius << '\n';  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         c.radius = 3.6;  #distractor
      {{endgroup}}
      {{group}}
         s.set_radius (3.6);
      {{endgroup}}
      {{group}}
         std::cout << "New radius: " << c.get_radius () << '\n';
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::cout << "New radius: " << c.radius << '\n';  #distractor
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
         std::cout << "length: " << r.length << ", Height: " << r.height << '\n';
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::cout << "length: " << r.get_length() << ", Height: " << r.get_height() << '\n';  #distractor
      {{endgroup}}
      {{group}}
         std::cout << "Area: " << r.calculate_area() << '\n';
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
         std::cout << "New area: " << r.calculate_area() << '\n';
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
            std::cout << get_month() << '/' << get_day() << '/' << -get_year() << " BCE" << '\n';
      {{endgroup}}
      {{distractor}}
      {{group}}
            std::cout << month << '/' << day << '/' << year << " BCE" << '\n';  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
            std::cout << get_month() << '/' << get_day() << '/' << get_year() << " BCE" << '\n';  #distractor
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         else {
      {{endgroup}}
      {{group}}
            std::cout << get_month() << '/' << get_day() << '/' << get_year() << " CE" << '\n';
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
