.. _fruitful-functions-coding-practice:

Coding Practice
---------------

Write a function called ``calculator`` which takes two ``double``\s, ``first`` and
``second``, and a ``char operation`` as parameters. ``calculator`` performs
addition, subtraction, multiplication, or division with the two ``double``\s 
depending on what operation is passed in (``+``, ``-``, ``*``, ``/``). 
It then returns the result.
Run and test your code!

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-group::
         :name: cp_5_1

         .. tb-tab:: Question

            Write a function called ``calculator`` which takes two ``double``\s, ``first`` and
            ``second``, and a ``char operation`` as parameters. ``calculator`` performs
            addition, subtraction, multiplication, or division with the two ``double``\s 
            depending on what operation is passed in (``+``, ``-``, ``*``, ``/``). 
            It then returns the result.
            Run and test your code!

            .. tb-code:: cpp
               :name: cp_5_AC_1q-support
               :hidden:

               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>

               template <class t, class compare = std::equal_to<t>>
               void check (const std::string& name, const t& actual, 
                           const t& expected, const compare& op = compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                 if(op(actual, expected)) {
                   std::cout << " OK      \n";
                   return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                 check("addition", calculator(3, 6, '+'),  9.);
                 check("add negatives", calculator(-2.6, 4, '+'), 1.4);
                 check("subtraction", calculator(19, 2, '-'), 17.0);
                 check("subtract negatives", calculator(-2.3, 2, '-'), -4.3);
                 check("multiplication", calculator(5, 8, '*'), 40.0);
                 check("multiply negatives", calculator(0.5, -6, '*'), -3.0);
                 check("division", calculator(16, 4, '/'), 4.0);
                 check("divide result < 0", calculator(3, 8, '/'), 0.375);
               }


            .. tb-code:: cpp
               :name: cp_5_AC_1q
               :caption: Example cp_5_AC_1q
               :run-after: cp_5_AC_1q-support

               double calculator (double first, double second, char operation) {
                   // Write your implementation here.
               }

         .. tb-tab:: Answer

            Below is one way to implement the ``calculator`` function. Using conditionals,
            we return the correct result depending on which operation was given.

            .. tb-code:: cpp
               :name: cp_5_AC_1a-support
               :hidden:

                #include <functional>
                #include <iomanip>
                #include <iostream>
                #include <string>
                template <class t, class compare = std::equal_to<t>>
                void check (const std::string& name, const t& actual, 
                            const t& expected, const compare& op = compare())
                {
                  std::cout << std::left << std::setfill('.') 
                            << std::setw(50) << name 
                            << std::setw(7) <<  std::left;
                   if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                  }
                  std::cout << " FAILED\n";
                  std::cout << "\treceived [" << actual
                            << "], but expected [" << expected << "]\n";
                  exit(1);
                }
                int main() {
                  check("addition", calculator(3, 6, '+'),  9.);
                  check("add negatives", calculator(-2.6, 4, '+'), 1.4);
                  check("subtraction", calculator(19, 2, '-'), 17.0);
                  check("subtract negatives", calculator(-2.3, 2, '-'), -4.3);
                  check("multiplication", calculator(5, 8, '*'), 40.0);
                  check("multiply negatives", calculator(0.5, -6, '*'), -3.0);
                  check("division", calculator(16, 4, '/'), 4.0);
                  check("divide result < 0", calculator(3, 8, '/'), 0.375);
                }



            .. tb-code:: cpp
               :name: cp_5_AC_1a
               :caption: Example cp_5_AC_1a
               :run-after: cp_5_AC_1a-support

                double calculator (double first, double second, char operation) {
                    if (operation == '+') {
                        return first + second;
                    }
                    if (operation == '-') {
                        return first - second;
                    }
                    if (operation == '*') {
                        return first * second;
                    }
                    return first / second;
                }

   .. tb-tab:: Q2

      A binary number is one that is expressed in the base-2 numeral system.
      Write a function ``convert_to_binary`` which takes a ``decimal`` as
      a parameter. ``convert_to_binary`` takes the number in decimal, converts
      it into a binary number, and returns the binary number. 
      Run and test your code!

      .. tb-code:: cpp
         :name: cp_5_AC_2q-support
         :hidden:

         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class t, class compare = std::equal_to<t>>
         void check (const std::string& name, const t& actual, 
                     const t& expected, const compare& op = compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
             if(op(actual, expected)) {
              std::cout << " OK      \n";
              return;
           }
           std::cout << " FAILED\n";
           std::cout << "\treceived [" << actual
                     << "], but expected [" << expected << "]\n";
           exit(1);
         }
         int main() {
           check("convert 1", to_binary(1), 1);
           check("convert 5", to_binary(5), 101);
           check("convert 16", to_binary(16), 10000);
           check("convert 31", to_binary(31), 11111);
         }





      .. tb-code:: cpp
         :name: cp_5_AC_2q
         :caption: Example cp_5_AC_2q
         :run-after: cp_5_AC_2q-support

         int to_binary (int decimal) {
             // Write your implementation here.
         }

   .. tb-tab:: Q3

      .. tb-group::
         :name: cp_5_3

         .. tb-tab:: Question

            An interior angle of a polygon is the angle between two adjacent 
            sides of the polygon. Each interior angle in an equilateral triangle
            measures 60 degree, each interior angle in a square measures 90 degrees,
            and in a regular pentagon, each interior angle measures 108 degrees.
            Write the function ``interior_angle``, which takes a ``sides``
            as a parameter and returns a ``double``. ``interior_angle`` finds the 
            interior angle of a regular polygon with ``sides`` sides. The formula
            to find the interior angle of a regular ngon is (n - 2) x 180 / n.
            Run and test your code!

            .. tb-code:: cpp
               :name: cp_5_AC_3q-support
               :hidden:

               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class t, class compare = std::equal_to<t>>
               void check (const std::string& name, const t& actual, 
                           const t& expected, const compare& op = compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                 check("3 sides", interior_angle(3), 60.0);
                 check("4 sides", interior_angle(4), 90.0);
                 check("5 sides", interior_angle(5), 108.0);
                 check("8 sides", interior_angle(8), 135.0);
               }





            .. tb-code:: cpp
               :name: cp_5_AC_3q
               :caption: Example cp_5_AC_3q
               :run-after: cp_5_AC_3q-support

               double interior_angle (int sides) {
                   // Write your implementation here.
               }

         .. tb-tab:: Answer

            Below is one way to implement the program. Using the formula given,
            we can find the interior angle and return it. Notice how we use 180.0
            instead of 180 to avoid integer division. 

            .. tb-code:: cpp
               :name: cp_5_AC_3a-support
               :hidden:

               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class t, class compare = std::equal_to<t>>
               void check (const std::string& name, const t& actual, 
                           const t& expected, const compare& op = compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                 check("3 sides", interior_angle(3), 60.0);
                 check("4 sides", interior_angle(4), 90.0);
                 check("5 sides", interior_angle(5), 108.0);
                 check("8 sides", interior_angle(8), 135.0);
               }



            .. tb-code:: cpp
               :name: cp_5_AC_3a
               :caption: Example cp_5_AC_3a
               :run-after: cp_5_AC_3a-support

               double interior_angle (int sides) {
                   return (sides - 2) * 180.0 / sides;
               }

   .. tb-tab:: Q4

      The astronomical start and end dates of the four seasons are based on
      the position of the Earth relative to the Sun. As a result, it
      changes every year and can be difficult to remember. However, the
      meteorological start and end dates are based on the Gregorian
      calendar and is easier to remember. Spring starts on March 1, summer
      starts on June 1, fall starts on September 1, and winter starts on
      December 1. Write a function called ``birth_season``, which takes two
      parameters, ``month`` and ``day``. ``birth_season`` calculates which
      season the birthday falls in according to the meteorological start
      and returns a ``string`` with the correct season.  For example,
      ``birth_season (7, 5)`` returns "summer" since July 5 is in the
      summer. 

      Run and test your code!

      .. tb-code:: cpp
         :name: cp_5_AC_4q-support
         :hidden:

         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class t, class compare = std::equal_to<t>>
         void check (const std::string& name, const t& actual, 
                     const std::string& expected, const compare& op = compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
            if(op(actual, expected)) {
              std::cout << " OK      \n";
              return;
           }
           std::cout << " FAILED\n";
           std::cout << "\treceived [" << actual
                     << "], but expected [" << expected << "]\n";
           exit(1);
         }
         int main() {
           check("May 3rd",   birth_season(5, 3), "spring");
           check("March 1st", birth_season(3, 1), "spring");
           check("May 31st",  birth_season(5, 31), "spring");
           check("July 5th",   birth_season(7, 5), "summer");
           check("June 1st", birth_season(6, 1), "summer");
           check("August 31st",  birth_season(8, 31), "summer");
           check("November 24th",   birth_season(11, 24), "fall");
           check("September 1st", birth_season(9, 1), "fall");
           check("November 30th",  birth_season(11, 30), "fall");
           check("February 20th",   birth_season(2, 20), "winter");
           check("December 1st", birth_season(12, 1), "winter");
           check("February 28th",  birth_season(2, 28), "winter");
         }



      .. tb-code:: cpp
         :name: cp_5_AC_4q
         :caption: Example cp_5_AC_4q
         :run-after: cp_5_AC_4q-support

         string birth_season (int month, int day) {
             // Write your implementation here.
         }

   .. tb-tab:: Q5

      .. tb-group::
         :name: cp_5_5

         .. tb-tab:: Question

            Dog owners will know that figuring out a dog's age is more complicated
            than just counting age directly. Dogs mature faster than humans do,
            so to get a more accurate calculation of a dog's age, write the
            ``dog_to_human_years`` function, which takes an ``dog_age`` as a parameter.
            ``dog_to_human_years`` converts and returns the dog's age to human years. 
            A one year old dog is 15 years old in human years; a two year old dog is 24 years old in human years. 
            Each year after the second year counts as 4 additional human years. For example, a dog that is
            3 years old is actually 28 years old in human years. Run and test your code!

            .. tb-code:: cpp
               :name: cp_5_AC_5q-support
               :hidden:

               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class t, class compare = std::equal_to<t>>
               void check (const std::string& name, 
                           const t& actual, 
                           const t& expected,
                           const compare& op = compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                 check("age == 1", dog_to_human_years(1), 15);
                 check("age == 2", dog_to_human_years(2), 24);
                 check("age == 3", dog_to_human_years(3), 28);
                 check("age == 5", dog_to_human_years(5), 36);
                 std::cout << "Simple error handling\n";
                 check("age == 0", dog_to_human_years(0), 0);
                 check("age == -1", dog_to_human_years(-1), 0);
                 check("age == -99", dog_to_human_years(-99), 0);
               }



            .. tb-code:: cpp
               :name: cp_5_AC_5q
               :caption: Example cp_5_AC_5q
               :run-after: cp_5_AC_5q-support

               int dog_to_human_years (int dog_age) {
                   // Write your implementation here.
               }

         .. tb-tab:: Answer

            Below is one way to implement the program. We can use a conditional to 
            check to see if the dog is one year old. If it is older than one, then 
            we can use the formula to return the correct age in human years.
            We also don't try to convert negative dog years.

            .. tb-code:: cpp
               :name: cp_5_AC_5a-support
               :hidden:

               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class t, class compare = std::equal_to<t>>
               void check (const std::string& name, 
                           const t& actual, 
                           const t& expected,
                           const compare& op = compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                 check("age == 1", dog_to_human_years(1), 15);
                 check("age == 2", dog_to_human_years(2), 24);
                 check("age == 3", dog_to_human_years(3), 28);
                 check("age == 5", dog_to_human_years(5), 36);
                 std::cout << "Simple error handling\n";
                 check("age == 0", dog_to_human_years(0), 0);
                 check("age == -1", dog_to_human_years(-1), 0);
                 check("age == -99", dog_to_human_years(-99), 0);
               }



            .. tb-code:: cpp
               :name: cp_5_AC_5a
               :caption: Example cp_5_AC_5a
               :run-after: cp_5_AC_5a-support

               int dog_to_human_years (int dog_age) {
                   if (dog_age < 1) {
                       return 0;
                   }
                   if (dog_age == 1) {
                       return 15;
                   }
                   return 24 + (dog_age - 2) * 4;
               }

   .. tb-tab:: Q6

      A number is a common factor of two other numbers if it divides evenly into both of the
      other numbers. For example, 2 is a common factor of 4 and 18, because 2 goes evenly into 
      4 and 18. Write the function ``is_common_factor``, which takes three parameters,
      ``num1``, ``num2``, and ``factor``. ``is_common_factor`` returns ``true`` if ``factor`` is a
      factor of both ``num1`` and ``num2``, and returns ``false`` otherwise. Run and test your code!

      .. tb-code:: cpp
         :name: cp_5_AC_6q-support
         :hidden:

         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class t, class compare = std::equal_to<t>>
         void check (const std::string& name, 
                     const t& actual, 
                     const t& expected,
                     const compare& op = compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
            if(op(actual, expected)) {
              std::cout << " OK      \n";
              return;
           }
           std::cout << " FAILED\n";
           std::cout << "\treceived [" << std::boolalpha << actual
                     << "], but expected [" << expected << "]\n";
           exit(1);
         }
         int main() {
           check("4 is a factor of 24 and 8", is_common_factor(24,8,4), true);
           check("5 is a factor of 75 and 20", is_common_factor(75,20,5), true);
           check("11 is not a factor of 132 and 42", is_common_factor(132,42,11), false);
           check("3 is not a factor of 74 and 24", is_common_factor(74,24,3), false);
         }



      .. tb-code:: cpp
         :name: cp_5_AC_6q
         :caption: Example cp_5_AC_6q
         :run-after: cp_5_AC_6q-support

         bool is_common_factor (int num1, int num2, int factor) {
             // Write your implementation here.
         }

   .. tb-tab:: Q7

      .. tb-group::
         :name: cp_5_7

         .. tb-tab:: Question

            If a year is divisible by 4, then it is a leap year. However, if it is also divisible by 100,
            then it is not a leap year. However, if it is also divisible by 400, then it is a leap year.
            Thus, 2001 is not a leap year, 2004 is a leap year, 2100 is not a leap year, and 2000 is a leap year.
            Write the boolean function ``is_leap_year``, which takes a ``year`` as a parameter and returns ``true`` 
            if the year is a leap year and ``false`` otherwise. Run and test your code!

            .. tb-code:: cpp
               :name: cp_5_AC_7q-support
               :hidden:

               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class t, class compare = std::equal_to<t>>
               void check (const std::string& name, 
                           const t& actual, 
                           const t& expected,
                           std::string help,
                           const compare& op = compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << std::boolalpha << actual
                           << "], but expected [" << expected << "]\n";
                 std::cout << '\t' << help << '\n';
                 exit(1);
               }
               int main() {
                 check("is 2001?", is_leap_year(2001), false, "year is not divisible by 4");
                 check("is 2005?", is_leap_year(2005), false, "year is not divisible by 4");
                 check("is 1730?", is_leap_year(1730), false, "year is not divisible by 4");
                 check("is 2004?", is_leap_year(2004), true, "year is divisible by 4");
                 check("is 2020?", is_leap_year(2020), true, "year is divisible by 4");
                 check("is 1776?", is_leap_year(1776), true, "year is divisible by 4");
                 check("is 1900?", is_leap_year(1900), false, "year is divisible by 100");
                 check("is 2100?", is_leap_year(2100), false, "year is divisible by 100");
                 check("is 2000?", is_leap_year(2000), true, "year is divisible by 400");
                 check("is 2400?", is_leap_year(2400), true, "year is divisible by 400");
               }



            .. tb-code:: cpp
               :name: cp_5_AC_7q
               :caption: Example cp_5_AC_7q
               :run-after: cp_5_AC_7q-support

               bool is_leap_year (int year) {
                   // Write your implementation here.
               }

         .. tb-tab:: Answer

            Below is one way to implement the program. We can use conditionals in this
            order to efficiently determine whether or not a given year is a leap year.

            .. tb-code:: cpp
               :name: cp_5_AC_7a-support
               :hidden:


               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class t, class compare = std::equal_to<t>>
               void check (const std::string& name, 
                           const t& actual, 
                           const t& expected,
                           const std::string& help,
                           const compare& op = compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << std::boolalpha << actual
                           << "], but expected [" << expected << "]\n";
                 std::cout << '\t' << help << '\n';
                 exit(1);
               }
               int main() {
                 check("is 2001?", is_leap_year(2001), false, "year is not divisible by 4");
                 check("is 2005?", is_leap_year(2005), false, "year is not divisible by 4");
                 check("is 1730?", is_leap_year(1730), false, "year is not divisible by 4");
                 check("is 2004?", is_leap_year(2004), true, "year is divisible by 4");
                 check("is 2020?", is_leap_year(2020), true, "year is divisible by 4");
                 check("is 1776?", is_leap_year(1776), true, "year is divisible by 4");
                 check("is 1900?", is_leap_year(1900), false, "year is divisible by 100");
                 check("is 2100?", is_leap_year(2100), false, "year is divisible by 100");
                 check("is 2000?", is_leap_year(2000), true, "year is divisible by 400");
                 check("is 2400?", is_leap_year(2400), true, "year is divisible by 400");
               }



            .. tb-code:: cpp
               :name: cp_5_AC_7a
               :caption: Example cp_5_AC_7a
               :run-after: cp_5_AC_7a-support

               bool is_leap_year (int year) {
                   if (year % 400 == 0) {
                       return true;
                   }
                   if (year % 100 == 0) {
                       return false;
                   }
                   if (year % 4 == 0) {
                       return true;
                   }
                   return false;
               }

   .. tb-tab:: Q8

      In the enchanted Mushroom Forest, there are many different types of 
      mushrooms as far as the eye can see. Most of these mushrooms
      can make delicious stews and dishes, but some of them are poisonous.
      Write the function ``poisonous``, which takes an ``char size``,
      ``int num_spots``, and ``bool is_red`` as parameters. If a mushroom is large
      ('L') and has fewer than 3 spots, it is poisonous. If a mushroom is small ('S')
      and is red, it is poisonous. If a mushroom has fewer than 3 spots or is not red,
      it is poisonous. Otherwise, it is not. ``poisonous`` should return ``true`` if 
      the mushroom is poisonous and ``false`` otherwise. Run and test your code!

      .. tb-code:: cpp
         :name: cp_5_AC_8q-support
         :hidden:

         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class t, class compare = std::equal_to<t>>
         void check (const std::string& name, 
                     const t& actual, 
                     const t& expected,
                     const std::string& help,
                     const compare& op = compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
            if(op(actual, expected)) {
              std::cout << " OK      \n";
              return;
           }
           std::cout << " FAILED\n";
           std::cout << "\treceived [" << std::boolalpha << actual
                     << "], but expected [" << expected << "]\n";
           std::cout << '\t' << help << '\n';
           exit(1);
         }
         int main() {
           check("small and red", poisonous('S', 10, true), true,
              "a small and red mushroom is poisonous");
           check("large, 1, red", poisonous('L', 1, true), true,
              "large and has fewer than 3 spots");
           check("large, 2, not red", poisonous('L', 2, false), true,
              "large and has fewer than 3 spots");
           check("large, 3, not red", poisonous('L', 3, false), true,
              "large and has fewer than 3 spots");
           check("small and not red", poisonous('S', 10, false), false,
              "small, not red, and has more than 3 spots");
           check("large, 4, red", poisonous('L', 4, true), false,"");
           check("large, 9, red", poisonous('L', 9, true), false,"");
         }



      .. tb-code:: cpp
         :name: cp_5_AC_8q
         :caption: Example cp_5_AC_8q
         :run-after: cp_5_AC_8q-support

         bool poisonous (char size, int num_spots, bool is_red) {
             // Write your implementation here.
         }

   .. tb-tab:: Q9

      .. tb-group::
         :name: cp_5_9

         .. tb-tab:: Question

            We know that a factorial is the product of an integer and all the integers below it.
            For example, four factorial (4!) is 24. A triangular number is the same as a factorial,
            except you add all the numbers instead of multiplying. For example, the 1st triangular
            number is 1, the 2nd is 3, the 3rd is 6, the 4th is 10, the 5th is 15, etc. You can imagine 
            rows of dots, where each successive row has one more dot, thus forming a triangular shape.
            Write the ``triangular_num`` function, which takes an ``int n`` as a parameter and returns
            the ``n``\th triangular number. Use recursion. Run and test your code!

            .. tb-code:: cpp
               :name: cp_5_AC_9q-support
               :hidden:


               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class t, class compare = std::equal_to<t>>
               void check (const std::string& name, 
                           const t& actual, 
                           const t& expected,
                           const compare& op = compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                 check("num == 1", triangular_num(1), 1);
                 check("num == 3", triangular_num(3), 6);
                 check("num == 6", triangular_num(6), 21);
                 check("num == 17", triangular_num(17), 153);
               }



            .. tb-code:: cpp
               :name: cp_5_AC_9q
               :caption: Example cp_5_AC_9q
               :run-after: cp_5_AC_9q-support

               int triangular_num (int n) {
                   // Write your implementation here.
               }

         .. tb-tab:: Answer

            Below is one way to implement the program. We can use conditionals to 
            separate the base case and recursive cases. Our base case is when ``n``
            is 1, and in that case we return 1. Otherwise, we recursively
            call ``triangular_num`` on ``n-1``.

            .. tb-code:: cpp
               :name: cp_5_AC_9a-support
               :hidden:


               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class t, class compare = std::equal_to<t>>
               void check (const std::string& name, 
                           const t& actual, 
                           const t& expected,
                           const compare& op = compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                 check("num == 1", triangular_num(1), 1);
                 check("num == 3", triangular_num(3), 6);
                 check("num == 6", triangular_num(6), 21);
                 check("num == 17", triangular_num(17), 153);
               }




            .. tb-code:: cpp
               :name: cp_5_AC_9a
               :caption: Example cp_5_AC_9a
               :run-after: cp_5_AC_9a-support

               int triangular_num (int n) {
                   if (n == 1) {
                       return 1;
                   } 
                   return n + triangular_num(n - 1);
               }

   .. tb-tab:: Q10

      Write the function ``digit_sum`` which takes an ``int num`` as a parameter
      and returns the sum of all its digits. For example, ``digit_sum (1423)``
      would return 10. Use recursion. Run and test your code!

      .. tb-code:: cpp
         :name: cp_5_AC_10q-support
         :hidden:

         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class t, class compare = std::equal_to<t>>
         void check (const std::string& name, 
                     const t& actual, 
                     const t& expected,
                     const compare& op = compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
            if(op(actual, expected)) {
              std::cout << " OK      \n";
              return;
           }
           std::cout << " FAILED\n";
           std::cout << "\treceived [" << actual
                     << "], but expected [" << expected << "]\n";
           exit(1);
         }
         int main() {
           check("num == 1", digit_sum(1), 1);
           check("num == 12", digit_sum(12), 3);
           check("num == 123", digit_sum(123), 6);
           check("num == 1243", digit_sum(1243), 10);
           check("num == 8739", digit_sum(8739), 27);
           check("num == 202", digit_sum(202), 4);
           check("num == 440", digit_sum(440), 8);
           check("num == 4050", digit_sum(4050), 9);
           check("num == 40005000", digit_sum(40005000), 9);
           check("num == 0", digit_sum(0), 0);
         }


      .. tb-code:: cpp
         :name: cp_5_AC_10q
         :caption: Example cp_5_AC_10q
         :run-after: cp_5_AC_10q-support

         int digit_sum (int num) {
             // Write your implementation here.
         }

