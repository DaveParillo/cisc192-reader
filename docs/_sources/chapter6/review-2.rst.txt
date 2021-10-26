Mixed Up Code Practice
----------------------

.. tabbed:: self_check

   .. tab:: Q1

      .. parsonsprob:: mucp_6_1
         :numbered: left
         :adaptive:
         :noindent:
         :practice: T

         The program below should print out the even numbers between 20 and 40, inclusive, 
         but the code is mixed up and contains extra blocks. Put the necessary blocks
         in the correct order.
         -----
         int main() {
         =====
         main(int) {                         #paired
         =====
            int n = 20;
         =====
            int n = 0; #distractor 
         =====
            while (n <= 40) {
         =====
            while (n < 40) {                        #paired 
         =====
               cout << n << endl;
         =====
               n = n + 2;
         =====
               n++;                 #distractor
         =====
               n = n * 2;                 #distractor
         =====
            }
         =====
         }

   .. tab:: Q2

      .. parsonsprob:: mucp_6_2
         :numbered: left
         :adaptive:
         :noindent:
         :practice: T

         The program below should count down from 100 to 0 in decrements of 
         10 but the code is mixed up and contains extra blocks. Put the necessary blocks
         in the correct order.
         -----
         int main() {
         =====
            int n = 100;
         =====
            int n = 10; #distractor 
         =====
            while (n >= 0) {
         =====
            while (n < 0) { #distractor
         =====
            while (n > 0) { #distractor
         =====
               cout << n << endl;
         =====
               n -= 10;
         =====
               n += 10;                 #distractor
         =====
            }
         =====
         }

   .. tab:: Q3

      .. parsonsprob:: mucp_6_3
         :numbered: left
         :adaptive:
         :noindent:
         :practice: T

         The program below should find the sum of the first 10 natural numbers,
         but the code is mixed up and contains extra blocks. Put the necessary blocks
         in the correct order.
         -----
         int main() {
         =====
            int n = 1;
         =====
            int n = 10; #distractor 
         =====
            int sum = 0;
         =====
            int sum = n;  #distractor
         =====
            while (n <= 10) {
         =====
            while (n < 100) {  #distractor
         =====
            while (n <= 9) {  #distractor
         =====
               cout << n << endl;  #distractor
         =====
               sum = sum + n;
         =====
               n++;
         =====
            }
         =====
         }

   .. tab:: Q4

      .. parsonsprob:: mucp_6_4
         :numbered: left
         :adaptive:
         :practice: T

         Let's write the code for the repeatHello function. repeatHello 
         should be a void function that takes no arguments and uses a while
         loop to print out "hello" three times.  
         -----
         void repeatHello () {
         =====
         repeatHello () {                         #paired
         =====
            int n = 0;
         =====
            int n = 0                        #paired 
         =====
            while (n < 3) {
         =====
            while (n > 3) {                        #paired 
         =====
               cout << "hello" << endl;
         =====
               n++;
         =====
            }
         =====
         }

   .. tab:: Q5

      .. parsonsprob:: mucp_6_5
         :numbered: left
         :adaptive:

         Now let's generalize the repeatHello function so that it repeats a given string three times.
         Let's write the code for the repeatString function, which takes 
         input as a parameter and uses a while loop to print out the string three times.  
         -----
         void repeatString (string input) {
         =====
         void repeatString () {                         #paired
         =====
            int n = 0;
         =====
            while (n < 3) {
         =====
            while (3 > n) {                        #paired 
         =====
               cout << input << endl;
         =====
               cout << string << endl;                        #paired 
         =====
               n++;
         =====
            }
         =====
         }

   .. tab:: Q6

      .. parsonsprob:: mucp_6_6
         :numbered: left
         :adaptive:

         We can further generalize repeatString so that it repeats a given string a given number of times. 
         Let's write the code for the new repeatString function, which takes 
         input and x as parameters and uses a while loop to print out the string x number of times.  
         -----
         void repeatString (string input, int x) {
         =====
         void repeatString (string input, string x) {                         #paired
         =====
            int n = 0;
         =====
            int n = x;                       #paired
         =====
            while (n < x) {
         =====
            while (x < n) {                        #paired 
         =====
               cout << input << endl;
         =====
               n++; 
         =====
               x++;                       #paired
         =====
            }
         =====
         }

   .. tab:: Q7

      .. parsonsprob:: mucp_6_7
         :numbered: left
         :adaptive:
         :practice: T

         On the last day of every year, we count down the seconds before the new year arrives.
         Write the function newYearCountdown, which prints out a countdown from 10 and then
         prints out "Happy New Year!".
         -----
         void newYearCountdown () {
         =====
         void newYearCountdown (string input) {                         #paired
         =====
            int n = 10;
         =====
            int n = 0;                       #paired
         =====
            while (n > 0) {
         =====
            while (n != 10) {                        #paired 
         =====
               cout << n << " ";
         =====
               n--; 
         =====
               n++;  #
         =====
            }
         =====
            cout << "Happy New Year!" << endl;
         }

   .. tab:: Q8

      .. parsonsprob:: mucp_6_8
         :numbered: left
         :adaptive:
         :practice: T

         Help Goku reach power levels of over 9000! Write the function
         powerUp which takes powerLevel as a parameter.
         powerUp checks to see if powerLevel is over 9000. If it 
         isn't, it repeatedly prints "More power!" and increments powerLevel by 
         1000 until powerLevel is over 9000. Then powerUp prints "It's over 9000!".
         Put the necessary blocks in the correct order.
         -----
         void powerUp (int powerLevel) {
         =====
         void powerUp () {                         #paired
         =====
            int n = 0;  #distractor
         =====
            while (powerLevel < 9000) {
         =====
            while (powerLevel > 9000) {  #paired
         =====
               cout << "More power!" << endl; 
         =====
               powerLevel = powerLevel + 1000;
         =====
               powerLevel++;  #paired
         =====
               n++;  #distractor
         =====
            }
         =====
            if (powerLevel < 9000) {  #distractor
         =====
            cout << "It's over 9000!" << endl;
         }

   .. tab:: Q9

      .. parsonsprob:: mucp_6_9
         :numbered: left
         :adaptive:
         :practice: T

         Write the function summation which takes two 
         parameters, start and end. summation adds
         all the integers from start to end, inclusive, together and returns
         the sum. Put the necessary blocks in the correct order.
         -----
         int summation (int start, int end) {
         =====
         void summation (int start, int end) {  #distractor
         =====
         int summation () {  #distractor
         =====
            int n = start;
         =====
            int sum = 0;
         =====
            int sum = start;  #distractor
         =====
            while (n <= end) {
         =====
            while (n < end) {  #paired
         =====
               sum = sum + n; 
         =====
               n++;
         =====
            }
         =====
            return sum;
         =====
            return n;  #distractor
         =====
         }

   .. tab:: Q10

      .. parsonsprob:: mucp_6_10
         :numbered: left
         :adaptive:
         :practice: T

         Write the function reverseNumber which takes num
         as a parameter and returns num but with its digits reversed.
         For example, reverseNumber (1324) returns 4231. 
         Put the necessary blocks in the correct order, with reverse
         declared first, then temp, and lastly remainder.
         -----
         int reverseNumber (int num) {
         =====
         void reverseNumber (int num) {  #distractor
         =====
            int reverse = 0;
         =====
            int reverse = 0  #distractor
         =====
            int temp = num;
         =====
            int remainder = 0;
         =====
            int remainder;  #distractor
         =====
            while (temp > 0) {
         =====
               remainder = temp % 10;
         =====
               reverse = reverse * 10 + remainder;
         =====
               temp = temp / 10;
         =====
            }
         =====
            return reverse;
         =====
            return temp;  #distractor
         =====
         }

