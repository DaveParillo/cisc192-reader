Coding Practice
---------------

Write a function called ``calculator`` which takes two ``double``\s, ``first`` and
``second``, and a ``char operation`` as parameters. ``calculator`` performs
addition, subtraction, multiplication, or division with the two ``double``\s 
depending on what operation is passed in (``+``, ``-``, ``*``, ``/``). 
It then returns the result.
Run and test your code!

.. tabbed:: self_check

   .. tab:: Q1 

      .. tabbed:: cp_5_1

          .. tab:: Question

              Write a function called ``calculator`` which takes two ``double``\s, ``first`` and
              ``second``, and a ``char operation`` as parameters. ``calculator`` performs
              addition, subtraction, multiplication, or division with the two ``double``\s 
              depending on what operation is passed in (``+``, ``-``, ``*``, ``/``). 
              It then returns the result.
              Run and test your code!

              .. activecode:: cp_5_AC_1q
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :practice: T

                 double calculator (double first, double second, char operation) {
                     // Write your implementation here.
                 }
                 ====
                 #include <functional>
                 #include <iomanip>
                 #include <iostream>
                 #include <string>

                 template <class T, class Compare = std::equal_to<T>>
                 void check (const std::string& name, const T& actual, 
                             const T& expected, const Compare& op = Compare())
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

          .. tab:: Answer

              Below is one way to implement the ``calculator`` function. Using conditionals,
              we return the correct result depending on which operation was given.

              .. activecode:: cp_5_AC_1a
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :optional:

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

                  ====
                  #include <functional>
                  #include <iomanip>
                  #include <iostream>
                  #include <string>
                  template <class T, class Compare = std::equal_to<T>>
                  void check (const std::string& name, const T& actual, 
                              const T& expected, const Compare& op = Compare())
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


   .. tab:: Q2 

      .. activecode:: cp_5_AC_2q
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:
         :practice: T

         A binary number is one that is expressed in the base-2 numeral system.
         Write a function ``convertToBinary`` which takes a ``decimal`` as
         a parameter. ``convertToBinary`` takes the number in decimal, converts
         it into a binary number, and returns the binary number. 
         Run and test your code!
         ~~~~
         int to_binary (int decimal) {
             // Write your implementation here.
         }

         ====
         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, const T& actual, 
                     const T& expected, const Compare& op = Compare())
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




   .. tab:: Q3

      .. tabbed:: cp_5_3

          .. tab:: Question

              An interior angle of a polygon is the angle between two adjacent 
              sides of the polygon. Each interior angle in an equilateral triangle
              measures 60 degree, each interior angle in a square measures 90 degrees,
              and in a regular pentagon, each interior angle measures 108 degrees.
              Write the function ``interior_angle``, which takes a ``sides``
              as a parameter and returns a ``double``. ``interior_angle`` finds the 
              interior angle of a regular polygon with ``sides`` sides. The formula
              to find the interior angle of a regular ngon is (n - 2) x 180 / n.
              Run and test your code!

              .. activecode:: cp_5_AC_3q
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :practice: T

                 double interior_angle (int sides) {
                     // Write your implementation here.
                 }

                 ====
                 #include <functional>
                 #include <iomanip>
                 #include <iostream>
                 #include <string>
                 template <class T, class Compare = std::equal_to<T>>
                 void check (const std::string& name, const T& actual, 
                             const T& expected, const Compare& op = Compare())
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




          .. tab:: Answer

              Below is one way to implement the program. Using the formula given,
              we can find the interior angle and return it. Notice how we use 180.0
              instead of 180 to avoid integer division. 

              .. activecode:: cp_5_AC_3a
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :optional:

                 double interior_angle (int sides) {
                     return (sides - 2) * 180.0 / sides;
                 }
                 ====
                 #include <functional>
                 #include <iomanip>
                 #include <iostream>
                 #include <string>
                 template <class T, class Compare = std::equal_to<T>>
                 void check (const std::string& name, const T& actual, 
                             const T& expected, const Compare& op = Compare())
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


   .. tab:: Q4

      .. activecode:: cp_5_AC_4q
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:
         :practice: T

         The astronomical start and end dates of the four seasons are based on
         the position of the Earth relative to the Sun. As a result, it
         changes every year and can be difficult to remember. However, the
         meteorological start and end dates are based on the Gregorian
         calendar and is easier to remember. Spring starts on March 1, summer
         starts on June 1, fall starts on September 1, and winter starts on
         December 1. Write a function called ``birthSeason``, which takes two
         parameters, ``month`` and ``day``. ``birthSeason`` calculates which
         season the birthday falls in according to the meteorological start
         and returns a ``string`` with the correct season.  For example,
         ``birthSeason (7, 5)`` returns "summer" since July 5 is in the
         summer. 
         
         Run and test your code!
         ~~~~
         string birthSeason (int month, int day) {
             // Write your implementation here.
         }

         ====
         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, const T& actual, 
                     const std::string& expected, const Compare& op = Compare())
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
           check("May 3rd",   birthSeason(5, 3), "spring");
           check("March 1st", birthSeason(3, 1), "spring");
           check("May 31st",  birthSeason(5, 31), "spring");
           check("July 5th",   birthSeason(7, 5), "summer");
           check("June 1st", birthSeason(6, 1), "summer");
           check("August 31st",  birthSeason(8, 31), "summer");
           check("November 24th",   birthSeason(11, 24), "fall");
           check("September 1st", birthSeason(9, 1), "fall");
           check("November 30th",  birthSeason(11, 30), "fall");
           check("February 20th",   birthSeason(2, 20), "winter");
           check("December 1st", birthSeason(12, 1), "winter");
           check("February 28th",  birthSeason(2, 28), "winter");
         }


   .. tab:: Q5

      .. tabbed:: cp_5_5

          .. tab:: Question

              Dog owners will know that figuring out a dog's age is more complicated
              than just counting age directly. Dogs mature faster than humans do,
              so to get a more accurate calculation of a dog's age, write the
              ``dogToHumanYears`` function, which takes an ``dogAge`` as a parameter.
              ``dogToHumanYears`` converts and returns the dog's age to human years. 
              A one year old dog is 15 years old in human years; a two year old dog is 24 years old in human years. 
              Each year after the second year counts as 4 additional human years. For example, a dog that is
              3 years old is actually 28 years old in human years. Run and test your code!

              .. activecode:: cp_5_AC_5q
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :practice: T

                 int dogToHumanYears (int dogAge) {
                     // Write your implementation here.
                 }

                 ====
                 #include <functional>
                 #include <iomanip>
                 #include <iostream>
                 #include <string>
                 template <class T, class Compare = std::equal_to<T>>
                 void check (const std::string& name, 
                             const T& actual, 
                             const T& expected,
                             const Compare& op = Compare())
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
                   check("age == 1", dogToHumanYears(1), 15);
                   check("age == 2", dogToHumanYears(2), 24);
                   check("age == 3", dogToHumanYears(3), 28);
                   check("age == 5", dogToHumanYears(5), 36);
                   std::cout << "Simple error handling\n";
                   check("age == 0", dogToHumanYears(0), 0);
                   check("age == -1", dogToHumanYears(-1), 0);
                   check("age == -99", dogToHumanYears(-99), 0);
                 }


          .. tab:: Answer

              Below is one way to implement the program. We can use a conditional to 
              check to see if the dog is one year old. If it is older than one, then 
              we can use the formula to return the correct age in human years.
              We also don't try to convert negative dog years.

              .. activecode:: cp_5_AC_5a
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :optional:

                 int dogToHumanYears (int dogAge) {
                     if (dogAge < 1) {
                         return 0;
                     }
                     if (dogAge == 1) {
                         return 15;
                     }
                     return 24 + (dogAge - 2) * 4;
                 }

                 ====
                 #include <functional>
                 #include <iomanip>
                 #include <iostream>
                 #include <string>
                 template <class T, class Compare = std::equal_to<T>>
                 void check (const std::string& name, 
                             const T& actual, 
                             const T& expected,
                             const Compare& op = Compare())
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
                   check("age == 1", dogToHumanYears(1), 15);
                   check("age == 2", dogToHumanYears(2), 24);
                   check("age == 3", dogToHumanYears(3), 28);
                   check("age == 5", dogToHumanYears(5), 36);
                   std::cout << "Simple error handling\n";
                   check("age == 0", dogToHumanYears(0), 0);
                   check("age == -1", dogToHumanYears(-1), 0);
                   check("age == -99", dogToHumanYears(-99), 0);
                 }


   .. tab:: Q6

      .. activecode:: cp_5_AC_6q
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:
         :practice: T

         A number is a common factor of two other numbers if it divides evenly into both of the
         other numbers. For example, 2 is a common factor of 4 and 18, because 2 goes evenly into 
         4 and 18. Write the function ``isCommonFactor``, which takes three parameters,
         ``num1``, ``num2``, and ``factor``. ``isCommonFactor`` returns ``true`` if ``factor`` is a
         factor of both ``num1`` and ``num2``, and returns ``false`` otherwise. Run and test your code!
         ~~~~
         bool isCommonFactor (int num1, int num2, int factor) {
             // Write your implementation here.
         }

         ====
         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, 
                     const T& actual, 
                     const T& expected,
                     const Compare& op = Compare())
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
           check("4 is a factor of 24 and 8", isCommonFactor(24,8,4), true);
           check("5 is a factor of 75 and 20", isCommonFactor(75,20,5), true);
           check("11 is not a factor of 132 and 42", isCommonFactor(132,42,11), false);
           check("3 is not a factor of 74 and 24", isCommonFactor(74,24,3), false);
         }


   .. tab:: Q7

      .. tabbed:: cp_5_7

          .. tab:: Question

             If a year is divisible by 4, then it is a leap year. However, if it is also divisible by 100,
             then it is not a leap year. However, if it is also divisible by 400, then it is a leap year.
             Thus, 2001 is not a leap year, 2004 is a leap year, 2100 is not a leap year, and 2000 is a leap year.
             Write the boolean function ``isLeapYear``, which takes a ``year`` as a parameter and returns ``true`` 
             if the year is a leap year and ``false`` otherwise. Run and test your code!

             .. activecode:: cp_5_AC_7q
                :language: cpp
                :compileargs: ['-Wall', '-std=c++11']
                :nocodelens:
                :practice: T

                bool isLeapYear (int year) {
                    // Write your implementation here.
                }
                ====
                #include <functional>
                #include <iomanip>
                #include <iostream>
                #include <string>
                template <class T, class Compare = std::equal_to<T>>
                void check (const std::string& name, 
                            const T& actual, 
                            const T& expected,
                            std::string help,
                            const Compare& op = Compare())
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
                  check("is 2001?", isLeapYear(2001), false, "year is not divisible by 4");
                  check("is 2005?", isLeapYear(2005), false, "year is not divisible by 4");
                  check("is 1730?", isLeapYear(1730), false, "year is not divisible by 4");
                  check("is 2004?", isLeapYear(2004), true, "year is divisible by 4");
                  check("is 2020?", isLeapYear(2020), true, "year is divisible by 4");
                  check("is 1776?", isLeapYear(1776), true, "year is divisible by 4");
                  check("is 1900?", isLeapYear(1900), false, "year is divisible by 100");
                  check("is 2100?", isLeapYear(2100), false, "year is divisible by 100");
                  check("is 2000?", isLeapYear(2000), true, "year is divisible by 400");
                  check("is 2400?", isLeapYear(2400), true, "year is divisible by 400");
                }


          .. tab:: Answer

              Below is one way to implement the program. We can use conditionals in this
              order to efficiently determine whether or not a given year is a leap year.

              .. activecode:: cp_5_AC_7a
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :optional:

                 bool isLeapYear (int year) {
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
                 ====

                 #include <functional>
                 #include <iomanip>
                 #include <iostream>
                 #include <string>
                 template <class T, class Compare = std::equal_to<T>>
                 void check (const std::string& name, 
                             const T& actual, 
                             const T& expected,
                             const std::string& help,
                             const Compare& op = Compare())
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
                   check("is 2001?", isLeapYear(2001), false, "year is not divisible by 4");
                   check("is 2005?", isLeapYear(2005), false, "year is not divisible by 4");
                   check("is 1730?", isLeapYear(1730), false, "year is not divisible by 4");
                   check("is 2004?", isLeapYear(2004), true, "year is divisible by 4");
                   check("is 2020?", isLeapYear(2020), true, "year is divisible by 4");
                   check("is 1776?", isLeapYear(1776), true, "year is divisible by 4");
                   check("is 1900?", isLeapYear(1900), false, "year is divisible by 100");
                   check("is 2100?", isLeapYear(2100), false, "year is divisible by 100");
                   check("is 2000?", isLeapYear(2000), true, "year is divisible by 400");
                   check("is 2400?", isLeapYear(2400), true, "year is divisible by 400");
                 }


   .. tab:: Q8

      .. activecode:: cp_5_AC_8q
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:
         :practice: T

         In the enchanted Mushroom Forest, there are many different types of 
         mushrooms as far as the eye can see. Most of these mushrooms
         can make delicious stews and dishes, but some of them are poisonous.
         Write the function ``poisonous``, which takes an ``char size``,
         ``int numSpots``, and ``bool isRed`` as parameters. If a mushroom is large
         ('L') and has fewer than 3 spots, it is poisonous. If a mushroom is small ('S')
         and is red, it is poisonous. If a mushroom has fewer than 3 spots or is not red,
         it is poisonous. Otherwise, it is not. ``poisonous`` should return ``true`` if 
         the mushroom is poisonous and ``false`` otherwise. Run and test your code!
         ~~~~
         bool poisonous (char size, int numSpots, bool isRed) {
             // Write your implementation here.
         }

         ====
         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, 
                     const T& actual, 
                     const T& expected,
                     const std::string& help,
                     const Compare& op = Compare())
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


   .. tab:: Q9

      .. tabbed:: cp_5_9

          .. tab:: Question

              We know that a factorial is the product of an integer and all the integers below it.
              For example, four factorial (4!) is 24. A triangular number is the same as a factorial,
              except you add all the numbers instead of multiplying. For example, the 1st triangular
              number is 1, the 2nd is 3, the 3rd is 6, the 4th is 10, the 5th is 15, etc. You can imagine 
              rows of dots, where each successive row has one more dot, thus forming a triangular shape.
              Write the ``triangularNum`` function, which takes an ``int n`` as a parameter and returns
              the ``n``\th triangular number. Use recursion. Run and test your code!

              .. activecode:: cp_5_AC_9q
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :practice: T

                 int triangularNum (int n) {
                     // Write your implementation here.
                 }
                 ====

                 #include <functional>
                 #include <iomanip>
                 #include <iostream>
                 #include <string>
                 template <class T, class Compare = std::equal_to<T>>
                 void check (const std::string& name, 
                             const T& actual, 
                             const T& expected,
                             const Compare& op = Compare())
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
                   check("num == 1", triangularNum(1), 1);
                   check("num == 3", triangularNum(3), 6);
                   check("num == 6", triangularNum(6), 21);
                   check("num == 17", triangularNum(17), 153);
                 }


          .. tab:: Answer

              Below is one way to implement the program. We can use conditionals to 
              separate the base case and recursive cases. Our base case is when ``n``
              is 1, and in that case we return 1. Otherwise, we recursively
              call ``triangularNum`` on ``n-1``.

              .. activecode:: cp_5_AC_9a
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :optional:

                 int triangularNum (int n) {
                     if (n == 1) {
                         return 1;
                     } 
                     return n + triangularNum(n - 1);
                 }
                 ====

                 #include <functional>
                 #include <iomanip>
                 #include <iostream>
                 #include <string>
                 template <class T, class Compare = std::equal_to<T>>
                 void check (const std::string& name, 
                             const T& actual, 
                             const T& expected,
                             const Compare& op = Compare())
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
                   check("num == 1", triangularNum(1), 1);
                   check("num == 3", triangularNum(3), 6);
                   check("num == 6", triangularNum(6), 21);
                   check("num == 17", triangularNum(17), 153);
                 }



   .. tab:: Q10

      .. activecode:: cp_5_AC_10q
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:
         :practice: T

         Write the function ``digit_sum`` which takes an ``int num`` as a parameter
         and returns the sum of all its digits. For example, ``digit_sum (1423)``
         would return 10. Use recursion. Run and test your code!
         ~~~~
         int digit_sum (int num) {
             // Write your implementation here.
         }
         ====
         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, 
                     const T& actual, 
                     const T& expected,
                     const Compare& op = Compare())
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

