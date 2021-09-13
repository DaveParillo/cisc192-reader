Coding Practice
---------------

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
                 :practice: T
                 :datafile: catch.hpp

                 double calculator (double first, double second, char operation) {
                     // Write your implementation here.
                 }
                 ====
                 #define CATCH_CONFIG_MAIN
                 #include <catch.hpp>

                 TEST_CASE("calculator function: addition") {
                     REQUIRE(calculator(3, 6, '+') == 9);
                     REQUIRE(calculator(-2.6, 4, '+') == 1.4);
                 }

                 TEST_CASE("calculator function: subtraction") {
                     REQUIRE(calculator(19, 2, '-') == 17);
                     REQUIRE(calculator(-2.3, 2, '-') == -4.3);
                 }

                 TEST_CASE("calculator function: multiplication") {
                     REQUIRE(calculator(5, 8, '*') == 40);
                     REQUIRE(calculator(0.5, -6, '*') == -3.0);
                 }

                 TEST_CASE("calculator function: division") {
                     REQUIRE(calculator(16, 4, '/') == 4);
                     REQUIRE(calculator(3, 8, '/') == 0.375);
                 }

          .. tab:: Answer

              Below is one way to implement the ``calculator`` function. Using conditionals,
              we return the correct result depending on which operation was given.

              .. activecode:: cp_5_AC_1a
                 :language: cpp
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
                 #define CATCH_CONFIG_MAIN
                 #include <catch.hpp>

                 TEST_CASE("calculator function: addition") {
                     REQUIRE(calculator(3, 6, '+') == 9);
                     REQUIRE(calculator(-2.6, 4, '+') == 1.4);
                 }

                 TEST_CASE("calculator function: subtraction") {
                     REQUIRE(calculator(19, 2, '-') == 17);
                     REQUIRE(calculator(-2.3, 2, '-') == -4.3);
                 }

                 TEST_CASE("calculator function: multiplication") {
                     REQUIRE(calculator(5, 8, '*') == 40);
                     REQUIRE(calculator(0.5, -6, '*') == -3.0);
                 }

                 TEST_CASE("calculator function: division") {
                     REQUIRE(calculator(16, 4, '/') == 4);
                     REQUIRE(calculator(3, 8, '/') == 0.375);
                 }

   .. tab:: Q2 

      .. activecode:: cp_5_AC_2q
          :language: cpp
          :practice: T

          A binary number is one that is expressed in the base-2 numeral system.
          Write a function ``convertToBinary`` which takes a ``decimal`` as
          a parameter. ``convertToBinary`` takes the number in decimal, converts
          it into a binary number, and returns the binary number. Test your function
          in ``main``. Run and test your code!
          ~~~~
          int to_binary (int decimal) {
              // Write your implementation here.
          }
          ====
          #define CATCH_CONFIG_MAIN
          #include <catch.hpp>

          TEST_CASE("convertToBinary function") {
              REQUIRE(to_binary (1) == 1);
              REQUIRE(to_binary (5) == 101);
              REQUIRE(to_binary (16) == 10000);
              REQUIRE(to_binary (31) == 11111);
          }

   .. tab:: Q3

      .. tabbed:: cp_5_3

          .. tab:: Question

              An interior angle of a polygon is the angle between two adjacent 
              sides of the polygon. Each interior angle in an equilateral triangle
              measures 60 degree, each interior angle in a square measures 90 degrees,
              and in a regular pentagon, each interior angle measures 108 degrees.
              Write the function ``calculateIntAngle``, which takes a ``numSides``
              as a parameter and returns a ``double``. ``calculateIntAngle`` finds the 
              interior angle of a regular polygon with ``numSides`` sides. The formula
              to find the interior angle of a regular ngon is (n - 2) x 180 / n.
              Run and test your code!

              .. activecode:: cp_5_AC_3q
                 :language: cpp
                 :practice: T

                 #include <iostream>
                 using namespace std;

                 double calculateIntAngle (int numSides) {
                     // Write your implementation here.
                 }
                 ====
                 #define CATCH_CONFIG_MAIN
                 #include <catch.hpp>

                 TEST_CASE("calculateIntAngle function") {
                     REQUIRE(calculateIntAngle (3) == 60);
                     REQUIRE(calculateIntAngle (4) == 90);
                     REQUIRE(calculateIntAngle (5) == 108);
                     REQUIRE(calculateIntAngle (8) == 135);
                 }


          .. tab:: Answer

              Below is one way to implement the program. Using the formula given,
              we can find the interior angle and return it. Notice how we use 180.0
              instead of 180 to avoid integer division. 

              .. activecode:: cp_5_AC_3a
                 :language: cpp
                 :optional:

                 double calculateIntAngle (int numSides) {
                     return (numSides - 2) * 180.0 / numSides;
                 }
                 ====
                 #define CATCH_CONFIG_MAIN
                 #include <catch.hpp>

                 TEST_CASE("calculateIntAngle function") {
                     REQUIRE(calculateIntAngle (3) == 60);
                     REQUIRE(calculateIntAngle (4) == 90);
                     REQUIRE(calculateIntAngle (5) == 108);
                     REQUIRE(calculateIntAngle (8) == 135);
                 }

   .. tab:: Q4

      .. activecode:: cp_5_AC_4q
          :language: cpp
          :practice: T

          The astronomical start and end dates of the four seasons are based on the position of
          the Earth relative to the Sun. As a result, it changes every year and can be difficult to
          remember. However, the meteorological start and end dates are based on the Gregorian calendar
          and is easier to remember. Spring starts on March 1, summer starts on June 1, fall starts on 
          September 1, and winter starts on December 1. Write a function called ``birthSeason``, which takes
          two parameters, ``month`` and ``day``. ``birthSeason`` calculates which season
          the birthday falls in according to the meteorological start and returns a ``string`` with the correct season.
          For example, ``birthSeason (7, 5)`` returns "summer" since July 5 is in the summer.
          Run and test your code!
          ~~~~
          string birthSeason (int month, int day) {
              // Write your implementation here.
          }
          ====
          #define CATCH_CONFIG_MAIN
          #include <catch.hpp>

          TEST_CASE("birthSeason function: spring") {
              REQUIRE(birthSeason (5, 3) == "spring");
              REQUIRE(birthSeason (3, 1) == "spring");
              REQUIRE(birthSeason (5, 31) == "spring");
          }

          TEST_CASE("birthSeason function: summer") {
              REQUIRE(birthSeason (7, 5) == "summer");
              REQUIRE(birthSeason (6, 1) == "summer");
              REQUIRE(birthSeason (8, 31) == "summer");
          }

          TEST_CASE("birthSeason function: fall") {
              REQUIRE(birthSeason (11, 24) == "fall");
              REQUIRE(birthSeason (9, 1) == "fall");
              REQUIRE(birthSeason (11, 30) == "fall");
          }

          TEST_CASE("birthSeason function: winter") {
              REQUIRE(birthSeason (2, 20) == "winter");
              REQUIRE(birthSeason (12, 1) == "winter");
              REQUIRE(birthSeason (2, 28) == "winter");
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
                 :practice: T

                 int dogToHumanYears (int dogAge) {
                     // Write your implementation here.
                 }
                 ====
                 #define CATCH_CONFIG_MAIN
                 #include <catch.hpp>

                 TEST_CASE("dogToHumanYears function for 1 and under") {
                     REQUIRE(dogToHumanYears (1) == 15);
                 }

                 TEST_CASE("dogToHumanYears function for >1") {
                     REQUIRE(dogToHumanYears (2) == 24);
                     REQUIRE(dogToHumanYears (3) == 28);
                     REQUIRE(dogToHumanYears (5) == 36);
                 }


          .. tab:: Answer

              Below is one way to implement the program. We can use a conditional to 
              check to see if the dog is one year old. If it is older than one, then 
              we can use the formula to return the correct age in human years.

              .. activecode:: cp_5_AC_5a
                 :language: cpp
                 :optional:

                 int dogToHumanYears (int dogAge) {
                     if (dogAge == 1) {
                         return 15;
                     }
                     return 24 + (dogAge - 2) * 4;
                 }
                 ====
                 #define CATCH_CONFIG_MAIN
                 #include <catch.hpp>

                 TEST_CASE("dogToHumanYears function for 1 and under") {
                     REQUIRE(dogToHumanYears (1) == 15);
                 }

                 TEST_CASE("dogToHumanYears function for >1") {
                     REQUIRE(dogToHumanYears (2) == 24);
                     REQUIRE(dogToHumanYears (3) == 28);
                     REQUIRE(dogToHumanYears (5) == 36);
                 }

   .. tab:: Q6

      .. activecode:: cp_5_AC_6q
          :language: cpp
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
          #define CATCH_CONFIG_MAIN
          #include <catch.hpp>

          TEST_CASE("isCommonFactor function: true cases") {
              REQUIRE(isCommonFactor (24, 8, 4) == 1); 
              REQUIRE(isCommonFactor (75, 20, 5) == 1);
          }

          TEST_CASE("isCommonFactor function: false cases") {
              REQUIRE(isCommonFactor (132, 42, 11) == 0); 
              REQUIRE(isCommonFactor (74, 23, 3) == 0);
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
                 :practice: T

                 bool isLeapYear (int year) {
                     // Write your implementation here.
                 }
                 ====
                 #define CATCH_CONFIG_MAIN
                 #include <catch.hpp>

                 TEST_CASE("isLeapYear not divisible by 4") {
                     REQUIRE(isLeapYear (2001) == 0);
                     REQUIRE(isLeapYear (2005) == 0);
                 }

                 TEST_CASE("isLeapYear divisible by 4") {
                     REQUIRE(isLeapYear (2004) == 1);
                     REQUIRE(isLeapYear (2008) == 1);
                 }

                 TEST_CASE("isLeapYear divisible by 100") {
                     REQUIRE(isLeapYear (2100) == 0);
                     REQUIRE(isLeapYear (1900) == 0);
                 }

                 TEST_CASE("isLeapYear divisible by 400") {
                     REQUIRE(isLeapYear (2000) == 1);
                     REQUIRE(isLeapYear (2400) == 1);
                 }


          .. tab:: Answer

              Below is one way to implement the program. We can use conditionals in this
              order to efficiently determine whether or not a given year is a leap year.

              .. activecode:: cp_5_AC_7a
                 :language: cpp
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
                 #define CATCH_CONFIG_MAIN
                 #include <catch.hpp>

                 TEST_CASE("isLeapYear not divisible by 4") {
                     REQUIRE(isLeapYear (2001) == 0);
                     REQUIRE(isLeapYear (2005) == 0);
                 }

                 TEST_CASE("isLeapYear divisible by 4") {
                     REQUIRE(isLeapYear (2004) == 1);
                     REQUIRE(isLeapYear (2008) == 1);
                 }

                 TEST_CASE("isLeapYear divisible by 100") {
                     REQUIRE(isLeapYear (2100) == 0);
                     REQUIRE(isLeapYear (1900) == 0);
                 }

                 TEST_CASE("isLeapYear divisible by 400") {
                     REQUIRE(isLeapYear (2000) == 1);
                     REQUIRE(isLeapYear (2400) == 1);
                 }

   .. tab:: Q8

      .. activecode:: cp_5_AC_8q
          :language: cpp
          :practice: T

          In the enchanted Mushroom Forest, there are many different types of 
          mushrooms as far as the eye can see. Most of these mushrooms
          can make delicious stews and dishes, but some of them are poisonous.
          Write the function ``poisonous``, which takes an ``char size``,
          ``int numSpots``, and ``bool isRed`` as parameters. If a mushroom is large
          ('L') and has fewer than 3 spots, it is poisonous. If a mushroom is small ('S')
          and is red, it is poisonous. If a mushroom has fewer than 3 spots or is not red,
          it is poisonous. Otherwise, it is not. ``isPoisonous`` should return ``true`` if 
          the mushroom is poisonous and ``false`` otherwise. Run and test your code!
          ~~~~
          bool poisonous (char size, int numSpots, bool isRed) {
              // Write your implementation here.
          }
          ====
          #define CATCH_CONFIG_MAIN
          #include <catch.hpp>

          TEST_CASE("poisonous function: true cases") {
              REQUIRE(poisonous ('S', 10, 0) == 1); 
              REQUIRE(poisonous ('S', 10, 0) == 1);
              REQUIRE(poisonous ('L', 1, 1) == 1);
          }

          TEST_CASE("poisonous function: false cases") {
              REQUIRE(poisonous ('L', 4, 1) == 0); 
              REQUIRE(poisonous ('L', 9, 1) == 0);
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
                 :practice: T

                 int triangularNum (int n) {
                     // Write your implementation here.
                 }
                 ====
                 #define CATCH_CONFIG_MAIN
                 #include <catch.hpp>

                 TEST_CASE("triangularNum function") {
                     REQUIRE(triangularNum (1) == 1); 
                     REQUIRE(triangularNum (3) == 6); 
                     REQUIRE(triangularNum (6) == 21); 
                     REQUIRE(triangularNum (17) == 153); 
                 }


          .. tab:: Answer

              Below is one way to implement the program. We can use conditionals to 
              separate the base case and recursive cases. Our base case is when ``n``
              is 1, and in that case we return 1. Otherwise, we recursively
              call ``triangularNum`` on ``n-1``.

              .. activecode:: cp_5_AC_9a
                 :language: cpp
                 :optional:

                 int triangularNum (int n) {
                     if (n == 1) {
                         return 1;
                     } 
                     return n + triangularNum(n - 1);
                 }
                 ====
                 #define CATCH_CONFIG_MAIN
                 #include <catch.hpp>

                 TEST_CASE("triangularNum function") {
                     REQUIRE(triangularNum (1) == 1); 
                     REQUIRE(triangularNum (3) == 6); 
                     REQUIRE(triangularNum (6) == 21); 
                     REQUIRE(triangularNum (17) == 153); 
                 }

   .. tab:: Q10

      .. activecode:: cp_5_AC_10q
          :language: cpp
          :practice: T

          Write the function ``digit_sum`` which takes an ``int num`` as a parameter
          and returns the sum of all its digits. For example, ``digit_sum (1423)``
          would return 10. Use recursion. Run and test your code!
          ~~~~
          int digit_sum (int num) {
              // Write your implementation here.
          }
          ====
          #define CATCH_CONFIG_MAIN
          #include <catch.hpp>

          TEST_CASE("digit_sum function") {
              REQUIRE(digit_sum (123) == 6); 
              REQUIRE(digit_sum (8739) == 27); 
              REQUIRE(digit_sum (440) == 8); 
              REQUIRE(digit_sum (2) == 2); 
          }
