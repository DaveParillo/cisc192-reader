Mixed Up Code Practice
----------------------

.. tabbed:: self_check

   .. tab:: Q1

      .. parsonsprob:: mucp_5_1
         :numbered: left
         :adaptive:
         :noindent:
         :practice: T

         Vacation time! But before you go, you need to convert your currency.
         Let's write the code for the dollarToYen function. dollarToYen
         takes dollar as a parameter and returns the equivalent amount of Japanese yen.
         The conversion rate is 1 USD equals 105.42 Japanese yen.
         Put the necessary blocks of code in the correct order.
         -----
         double dollarToYen (double dollar) {
         =====
         int dollarToYen (double dollar) {  #distractor
         =====
         void dollarToYen (double dollar) {  #distractor
         =====
         double dollarToYen () {  #distractor
         =====
            double yen;  #distractor
         =====
            return 105.42 * dollar;
         =====
            return 105.42 * yen;  #distractor
         =====
         }

   .. tab:: Q2

      .. parsonsprob:: mucp_5_2
         :numbered: left
         :adaptive:
         :noindent:
         :practice: T

         When you buy something, you also need to pay sales tax. For example,
         a nice shirt could be labeled with a price of exactly $20, but when 
         you pay, you actually need to pay $21.20 in a state with 6% sales tax.
         However, different states have different tax rates. Write the function
         priceWithTax, which takes price and percentTax as parameters.
         priceWithTax calculates the price after tax and returns it.
         For example, priceWithTax (20, 6) returns 21.2.
         Put the necessary blocks of code in the correct order.
         -----
         double priceWithTax (double price, double percentTax) {
         =====
         int priceWithTax (double price, int percentTax) {  #distractor
         =====
         double priceWithTax (price, percentTax) {  #distractor
         =====
            return (1 + percentTax / 100) * price;
         =====
            return (1 + percentTax) * price;  #distractor
         =====
            return percentTax * price;  #distractor
         =====
         }

   .. tab:: Q3

      .. parsonsprob:: mucp_5_3
         :numbered: left
         :adaptive:
         :noindent:
         :practice: T

         Most assignments and tests are graded as a percentage, but final
         grades are letters. Let's write the code for the percentToLetter function. 
         percentToLetter takes a percentage and returns the corresponding
         letter grade. A 90 and above is an 'A', an 80 and above is a 'B', a 70 and above
         is a 'C', and anything under a 70 is an 'F'.
         Put the necessary blocks of code in the correct order.
         -----
         char percentToLetter (double percentage) {
         =====
         void percentToLetter (double percentage) {  #distractor
         =====
         void percentToLetter (int percentage) {  #distractor
         =====
         char percentToLetter (percentage) {  #distractor
         =====
            if (percentage >= 90) {
         =====
               return 'A';
         =====
               return A;  #paired
         =====
            }
         =====
            else if (percentage >= 80) {
         =====
               return 'B';
         =====
               return 'B'  #paired
         =====
            }
         =====
            else if (percentage >= 70) {
         =====
            else if (percentage > 70) {  #paired
         =====
               return 'C';
         =====
            }
         =====
            else {
         =====
               return 'F';
         =====
            }
         =====
         }

   .. tab:: Q4

      .. parsonsprob:: mucp_5_4
         :numbered: left
         :adaptive:
         :noindent:
         :practice: T

         Let's write the code for the triangleArea function. triangleArea
         takes two parameters, base and height. It returns the 
         area of the triangle using the formula 1/2 * base * height.
         Put the necessary blocks of code in the correct order.
         -----
         double triangleArea (double base, double height) {
         =====
         int triangleArea (double base, double height) {  #distractor
         =====
         void triangleArea (double base, double height) {  #distractor
         =====
         double triangleArea (base, height) {  #distractor
         =====
            double area;  #distractor
         =====
            return 0.5 * base * height;
         =====
            cout << 0.5 * base * height << endl;  #distractor
         =====
         }

   .. tab:: Q5

      .. parsonsprob:: mucp_5_5
         :numbered: left
         :adaptive:
         :practice: T

         Let's write the code for the cylinderVolume function. cylinderVolume
         takes two parameters, radius and height. It returns the 
         volume of the cylinder using the formula pi * radius * radius * height.
         Put the necessary blocks of code in the correct order.
         -----
         double cylinderVolume (double radius, double height) {
         =====
         void cylinderVolume (double radius, double height) {  #distractor
         =====
         double cylinderVolume (radius, height) {  #distractor
         =====
            double pi = 3.14;
         =====
            return pi * radius * radius * height;
         =====
         }

   .. tab:: Q6

      .. parsonsprob:: mucp_5_6
         :numbered: left
         :adaptive:
         :practice: T

         On a distant planet, depending on the characteristics of an egg, a kenchic,
         an ooseg, or a guinpen might hatch from it. Let's write the function 
         birdType which returns an int corresponding to each type of bird
         (1 for kenchic, 2 for ooseg, and 3 for guinpen). If the egg is round, then it is a 
         guinpen. Otherwise, if the egg is round and it isn't gray, then it is a kenchic. If 
         it isn't a guinpen and it isn't a kenchic, then it's an ooseg. 
         Put the necessary blocks of code in the correct order.
         -----
         int birdType (bool isRound, bool isGray) {
         =====
         void birdType (bool isRound, bool isGray) {  #distractor
         =====
         double birdType (int isRound, char isGray) {  #distractor
         =====
            if (isRound && !isGray) {
         =====
            if (!isRound && !isGray) {  #paired
         =====
               return 1;
         =====
            }
         =====
            else if (!isRound || isGray) {
         =====
            else if (!(isRound || isGray)) {  #paired
         =====
               return 2;
         =====
            }
         =====
            else {
         =====
               return 3;
         =====
               return 0;  #distractor
         =====
            }
         =====
         }

   .. tab:: Q7

      .. parsonsprob:: mucp_5_7
         :numbered: left
         :adaptive:
         :practice: T

         Let's write the code for the isDoubleDigit function. isDoubleDigit
         takes num as a parameter. isDoubleDigit returns true if 
         num is a double digit number and returns false otherwise.
         Put the necessary blocks of code in the correct order.
         -----
         bool isDoubleDigit (int num) {
         =====
         isDoubleDigit (int num) {  #paired
         =====
            if (num >= 10 && num < 100) {
         =====
            if (10 <= num <= 99) {  #distractor
         =====
            if (num > 10 && num < 100) {  #distractor
         =====
            if (num > 10 && num <= 100) {  #distractor
         =====
               return true;
         =====
            }
         =====
            else {
         =====
               return false;
         =====
            }
         =====
         }

   .. tab:: Q8

      .. parsonsprob:: mucp_5_8
         :numbered: left
         :adaptive:
         :practice: T

         Let's write the code for the Compare function. Compare
         takes two integers a, b. Compare returns 1 if 
         a is greater than b, -1 if a is less than b and 0 if they are equal.
         Put the necessary blocks of code in the correct order.
         -----
         int Compare (int a, int b) {
         =====
         bool Compare (int a, int b) {   #paired
         =====
            if (a > b) {
         =====
            if (a > b && a &lt b) {  #distractor
         =====
               return 1;
         =====
            }
         =====
            else if (a &lt b) {  
         =====
            else if (a!=b) {  #distractor
         =====
               return -1;
         =====
            }
         =====
            else if (a > 0){ #distractor
         =====
            else {
         =====
               return 0;
         =====
            }
         =====
         }

   .. tab:: Q9

      .. parsonsprob:: mucp_5_9
         :numbered: left
         :adaptive:
         :practice: T

         Let's write the code for the isFactor function. isFactor
         takes two parameters, num and factor.
         isFactor returns true if factor is a factor of num 
         and returns false otherwise.
         Put the necessary blocks of code in the correct order.
         -----
         bool isFactor (int num, int factor) {
         =====
         void isFactor (int num, int factor) {  #paired
         =====
            if (num % factor == 0) {
         =====
            if (num / factor == 0) {  #distractor
         =====
            if (num % factor) {  #distractor
         =====
            if (factor % num == 0) {  #distractor
         =====
               return true;
         =====
            }
         =====
            else {
         =====
               return false;
         =====
            }
         =====
         }

   .. tab:: Q10

      .. parsonsprob:: mucp_5_10
         :numbered: left
         :adaptive:
         :practice: T

         Let's write the code for the isPerfectSquare function. isPerfectSquare
         takes input as a parameter and returns true if input is a 
         perfect square and returns false otherwise.
         Put the necessary blocks of code in the correct order.
         -----
         bool isPerfectSquare (int input) {
         =====
         bool isPerfectSquare (int input) #distractor
         =====
         int isPerfectSquare (int input) {  #distractor
         =====
            int root = sqrt (input);
         =====
            double root = sqrt (input);  #distractor
         =====
            if (pow (root, 2) == input) {
         =====
            if (sqrt (input)) {  #distractor
         =====
               return true;
         =====
            }
         =====
            else {
         =====
               return false;
         =====
            }
         =====
         }

   .. tab:: Q11

      .. parsonsprob:: mucp_5_11
         :numbered: left
         :adaptive:
         :practice: T

         Most bacteria cultures grow exponentially. For this problem,
         assume the number of cells in a bacterial culture doubles every hour.
         Let's write the code for the countBacteria function. countBacteria 
         takes hour as a parameter and returns the number of bacteria cells
         after hour hours. Assume when hour is 0, there is one cell. When 
         hour is one, the number of cells doubles to two. When hour is two, 
         the number of cells doubles to four. Use recursion. 
         Put the necessary blocks of code in the correct order.
         -----
         int countBacteria (int hour) {
         =====
         void countBacteria (int hour) {  #distractor
         =====
         bool countBacteria (int hour) {  #distractor
         =====
            if (hour == 0) {
         =====
            if (hour == 1) {  #paired
         =====
               return 1;
         =====
               return 2 * hour;  #distractor
         =====
            }
         =====
            else {
         =====
               return 2 * countBacteria (hour - 1);
         =====
               return 2 + countBacteria (hour - 1);  #distractor
         =====
               return 2 * countBacteria (hour);  #distractor
         =====
            }
         =====
         }
