Mixed Up Code Practice
----------------------

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: mucp_5_1
         :no-indent:

         Vacation time! But before you go, you need to convert your currency.
         Let's write the code for the dollarToYen function. dollarToYen
         takes dollar as a parameter and returns the equivalent amount of Japanese yen.
         The conversion rate is 1 USD equals 105.42 Japanese yen.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            double dollarToYen (double dollar) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            int dollarToYen (double dollar) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            void dollarToYen (double dollar) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            double dollarToYen () {  #distractor
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
         priceWithTax, which takes price and percentTax as parameters.
         priceWithTax calculates the price after tax and returns it.
         For example, priceWithTax (20, 6) returns 21.2.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            double priceWithTax (double price, double percentTax) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            int priceWithTax (double price, int percentTax) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            double priceWithTax (price, percentTax) {  #distractor
            {{endgroup}}
            {{group}}
               return (1 + percentTax / 100) * price;
            {{endgroup}}
            {{distractor}}
            {{group}}
               return (1 + percentTax) * price;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               return percentTax * price;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: mucp_5_3
         :no-indent:

         Most assignments and tests are graded as a percentage, but final
         grades are letters. Let's write the code for the percentToLetter function. 
         percentToLetter takes a percentage and returns the corresponding
         letter grade. A 90 and above is an 'A', an 80 and above is a 'B', a 70 and above
         is a 'C', and anything under a 70 is an 'F'.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            char percentToLetter (double percentage) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void percentToLetter (double percentage) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            void percentToLetter (int percentage) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            char percentToLetter (percentage) {  #distractor
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

         Let's write the code for the triangleArea function. triangleArea
         takes two parameters, base and height. It returns the 
         area of the triangle using the formula 1/2 * base * height.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            double triangleArea (double base, double height) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            int triangleArea (double base, double height) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            void triangleArea (double base, double height) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            double triangleArea (base, height) {  #distractor
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
               cout << 0.5 * base * height << endl;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q5

      .. tb-parsons::
         :name: mucp_5_5

         Let's write the code for the cylinderVolume function. cylinderVolume
         takes two parameters, radius and height. It returns the 
         volume of the cylinder using the formula pi * radius * radius * height.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            double cylinderVolume (double radius, double height) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void cylinderVolume (double radius, double height) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            double cylinderVolume (radius, height) {  #distractor
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
         birdType which returns an int corresponding to each type of bird
         (1 for kenchic, 2 for ooseg, and 3 for guinpen). If the egg is round, then it is a 
         guinpen. Otherwise, if the egg is round and it isn't gray, then it is a kenchic. If 
         it isn't a guinpen and it isn't a kenchic, then it's an ooseg. 
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            int birdType (bool isRound, bool isGray) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void birdType (bool isRound, bool isGray) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            double birdType (int isRound, char isGray) {  #distractor
            {{endgroup}}
            {{group}}
               if (isRound && !isGray) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (!isRound && !isGray) {
            {{endgroup}}
            {{group}}
                  return 1;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else if (!isRound || isGray) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               else if (!(isRound || isGray)) {
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

         Let's write the code for the isDoubleDigit function. isDoubleDigit
         takes num as a parameter. isDoubleDigit returns true if 
         num is a double digit number and returns false otherwise.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            bool isDoubleDigit (int num) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            isDoubleDigit (int num) {
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

         Let's write the code for the Compare function. Compare
         takes two integers a, b. Compare returns 1 if 
         a is greater than b, -1 if a is less than b and 0 if they are equal.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            int Compare (int a, int b) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            bool Compare (int a, int b) {
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

         Let's write the code for the isFactor function. isFactor
         takes two parameters, num and factor.
         isFactor returns true if factor is a factor of num 
         and returns false otherwise.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            bool isFactor (int num, int factor) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void isFactor (int num, int factor) {
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

         Let's write the code for the isPerfectSquare function. isPerfectSquare
         takes input as a parameter and returns true if input is a 
         perfect square and returns false otherwise.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            bool isPerfectSquare (int input) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            bool isPerfectSquare (int input) #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            int isPerfectSquare (int input) {  #distractor
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
         Let's write the code for the countBacteria function. countBacteria 
         takes hour as a parameter and returns the number of bacteria cells
         after hour hours. Assume when hour is 0, there is one cell. When 
         hour is one, the number of cells doubles to two. When hour is two, 
         the number of cells doubles to four. Use recursion. 
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            int countBacteria (int hour) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void countBacteria (int hour) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            bool countBacteria (int hour) {  #distractor
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
                  return 2 * countBacteria (hour - 1);
            {{endgroup}}
            {{distractor}}
            {{group}}
                  return 2 + countBacteria (hour - 1);  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
                  return 2 * countBacteria (hour);  #distractor
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

