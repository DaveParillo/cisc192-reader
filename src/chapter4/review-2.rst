Mixed Up Code Practice
----------------------

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: mucp_5_1
         :no-indent:

         Vacation time! But before you go, you need to convert your currency.
         Let's write the code for the dollar_to_yen function. dollar_to_yen
         takes dollar as a parameter and returns the equivalent amount of Japanese yen.
         The conversion rate is 1 USD equals 105.42 Japanese yen.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            double dollar_to_yen (double dollar) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            int dollar_to_yen (double dollar) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            void dollar_to_yen (double dollar) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            double dollar_to_yen () {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               double yen;  #distractor
            {{endgroup}}
            {{group}}
               return 105.42 * dollar;
            {{endgroup}}
            {{distractor}}
            {{group}}
               return 105.42 * yen;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: mucp_5_2
         :no-indent:

         When you buy something, you also need to pay sales tax. For example,
         a nice shirt could be labeled with a price of exactly $20, but when 
         you pay, you actually need to pay $21.20 in a state with 6% sales tax.
         However, different states have different tax rates. Write the function
         price_with_tax, which takes price and percent_tax as parameters.
         price_with_tax calculates the price after tax and returns it.
         For example, price_with_tax (20, 6) returns 21.2.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            double price_with_tax (double price, double percent_tax) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            int price_with_tax (double price, int percent_tax) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            double price_with_tax (price, percent_tax) {  #distractor
            {{endgroup}}
            {{group}}
               return (1 + percent_tax / 100) * price;
            {{endgroup}}
            {{distractor}}
            {{group}}
               return (1 + percent_tax) * price;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               return percent_tax * price;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: mucp_5_3
         :no-indent:

         Most assignments and tests are graded as a percentage, but final
         grades are letters. Let's write the code for the percent_to_letter function. 
         percent_to_letter takes a percentage and returns the corresponding
         letter grade. A 90 and above is an 'A', an 80 and above is a 'B', a 70 and above
         is a 'C', and anything under a 70 is an 'F'.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            char percent_to_letter (double percentage) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void percent_to_letter (double percentage) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            void percent_to_letter (int percentage) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            char percent_to_letter (percentage) {  #distractor
            {{endgroup}}
            {{group}}
               if (percentage >= 90) {
            {{endgroup}}
            {{group}}
                  return 'A';
            {{endgroup}}
            {{distractor}}
            {{group}}
                  return A;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else if (percentage >= 80) {
            {{endgroup}}
            {{group}}
                  return 'B';
            {{endgroup}}
            {{distractor}}
            {{group}}
                  return 'B'
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else if (percentage >= 70) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               else if (percentage > 70) {
            {{endgroup}}
            {{group}}
                  return 'C';
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else {
            {{endgroup}}
            {{group}}
                  return 'F';
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q4

      .. tb-parsons::
         :name: mucp_5_4
         :no-indent:

         Let's write the code for the triangle_area function. triangle_area
         takes two parameters, base and height. It returns the 
         area of the triangle using the formula 1/2 * base * height.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            double triangle_area (double base, double height) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            int triangle_area (double base, double height) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            void triangle_area (double base, double height) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            double triangle_area (base, height) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               double area;  #distractor
            {{endgroup}}
            {{group}}
               return 0.5 * base * height;
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << 0.5 * base * height << '\n';  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q5

      .. tb-parsons::
         :name: mucp_5_5

         Let's write the code for the cylinder_volume function. cylinder_volume
         takes two parameters, radius and height. It returns the 
         volume of the cylinder using the formula pi * radius * radius * height.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            double cylinder_volume (double radius, double height) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void cylinder_volume (double radius, double height) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            double cylinder_volume (radius, height) {  #distractor
            {{endgroup}}
            {{group}}
               double pi = 3.14;
            {{endgroup}}
            {{group}}
               return pi * radius * radius * height;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q6

      .. tb-parsons::
         :name: mucp_5_6

         On a distant planet, depending on the characteristics of an egg, a kenchic,
         an ooseg, or a guinpen might hatch from it. Let's write the function 
         bird_type which returns an int corresponding to each type of bird
         (1 for kenchic, 2 for ooseg, and 3 for guinpen). If the egg is round, then it is a 
         guinpen. Otherwise, if the egg is round and it isn't gray, then it is a kenchic. If 
         it isn't a guinpen and it isn't a kenchic, then it's an ooseg. 
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            int bird_type (bool is_round, bool is_gray) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void bird_type (bool is_round, bool is_gray) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            double bird_type (int is_round, char is_gray) {  #distractor
            {{endgroup}}
            {{group}}
               if (is_round && !is_gray) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (!is_round && !is_gray) {
            {{endgroup}}
            {{group}}
                  return 1;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else if (!is_round || is_gray) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               else if (!(is_round || is_gray)) {
            {{endgroup}}
            {{group}}
                  return 2;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else {
            {{endgroup}}
            {{group}}
                  return 3;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  return 0;  #distractor
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q7

      .. tb-parsons::
         :name: mucp_5_7

         Let's write the code for the is_double_digit function. is_double_digit
         takes num as a parameter. is_double_digit returns true if 
         num is a double digit number and returns false otherwise.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            bool is_double_digit (int num) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            is_double_digit (int num) {
            {{endgroup}}
            {{group}}
               if (num >= 10 && num < 100) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (10 <= num <= 99) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (num > 10 && num < 100) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (num > 10 && num <= 100) {  #distractor
            {{endgroup}}
            {{group}}
                  return true;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else {
            {{endgroup}}
            {{group}}
                  return false;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q8

      .. tb-parsons::
         :name: mucp_5_8

         Let's write the code for the compare function. compare
         takes two integers a, b. compare returns 1 if 
         a is greater than b, -1 if a is less than b and 0 if they are equal.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            int compare (int a, int b) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            bool compare (int a, int b) {
            {{endgroup}}
            {{group}}
               if (a > b) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (a > b && a &lt b) {  #distractor
            {{endgroup}}
            {{group}}
                  return 1;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else if (a &lt b) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               else if (a!=b) {  #distractor
            {{endgroup}}
            {{group}}
                  return -1;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{distractor}}
            {{group}}
               else if (a > 0){ #distractor
            {{endgroup}}
            {{group}}
               else {
            {{endgroup}}
            {{group}}
                  return 0;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q9

      .. tb-parsons::
         :name: mucp_5_9

         Let's write the code for the is_factor function. is_factor
         takes two parameters, num and factor.
         is_factor returns true if factor is a factor of num 
         and returns false otherwise.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            bool is_factor (int num, int factor) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void is_factor (int num, int factor) {
            {{endgroup}}
            {{group}}
               if (num % factor == 0) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (num / factor == 0) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (num % factor) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (factor % num == 0) {  #distractor
            {{endgroup}}
            {{group}}
                  return true;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else {
            {{endgroup}}
            {{group}}
                  return false;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q10

      .. tb-parsons::
         :name: mucp_5_10

         Let's write the code for the is_perfect_square function. is_perfect_square
         takes input as a parameter and returns true if input is a 
         perfect square and returns false otherwise.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            bool is_perfect_square (int input) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            bool is_perfect_square (int input) #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            int is_perfect_square (int input) {  #distractor
            {{endgroup}}
            {{group}}
               int root = sqrt (input);
            {{endgroup}}
            {{distractor}}
            {{group}}
               double root = sqrt (input);  #distractor
            {{endgroup}}
            {{group}}
               if (pow (root, 2) == input) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (sqrt (input)) {  #distractor
            {{endgroup}}
            {{group}}
                  return true;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else {
            {{endgroup}}
            {{group}}
                  return false;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q11

      .. tb-parsons::
         :name: mucp_5_11

         Most bacteria cultures grow exponentially. For this problem,
         assume the number of cells in a bacterial culture doubles every hour.
         Let's write the code for the count_bacteria function. count_bacteria 
         takes hour as a parameter and returns the number of bacteria cells
         after hour hours. Assume when hour is 0, there is one cell. When 
         hour is one, the number of cells doubles to two. When hour is two, 
         the number of cells doubles to four. Use recursion. 
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            int count_bacteria (int hour) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void count_bacteria (int hour) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            bool count_bacteria (int hour) {  #distractor
            {{endgroup}}
            {{group}}
               if (hour == 0) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (hour == 1) {
            {{endgroup}}
            {{group}}
                  return 1;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  return 2 * hour;  #distractor
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else {
            {{endgroup}}
            {{group}}
                  return 2 * count_bacteria (hour - 1);
            {{endgroup}}
            {{distractor}}
            {{group}}
                  return 2 + count_bacteria (hour - 1);  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
                  return 2 * count_bacteria (hour);  #distractor
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

