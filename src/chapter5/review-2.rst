.. _iteration-mixed-up-code-practice:

Mixed Up Code Practice
----------------------

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: mucp_6_1
         :no-indent:

         The program below should print out the even numbers between 20 and 40, inclusive, 
         but the code is mixed up and contains extra blocks. Put the necessary blocks
         in the correct order.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{distractor}}
            {{group}}
            main(int) {
            {{endgroup}}
            {{group}}
               int n = 20;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int n = 0; #distractor
            {{endgroup}}
            {{group}}
               while (n <= 40) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (n < 40) {
            {{endgroup}}
            {{group}}
                  cout << n << '\n';
            {{endgroup}}
            {{group}}
                  n = n + 2;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  n++;                 #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
                  n = n * 2;                 #distractor
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: mucp_6_2
         :no-indent:

         The program below should count down from 100 to 0 in decrements of 
         10 but the code is mixed up and contains extra blocks. Put the necessary blocks
         in the correct order.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               int n = 100;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int n = 10; #distractor
            {{endgroup}}
            {{group}}
               while (n >= 0) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (n < 0) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (n > 0) { #distractor
            {{endgroup}}
            {{group}}
                  cout << n << '\n';
            {{endgroup}}
            {{group}}
                  n -= 10;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  n += 10;                 #distractor
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: mucp_6_3
         :no-indent:

         The program below should find the sum of the first 10 natural numbers,
         but the code is mixed up and contains extra blocks. Put the necessary blocks
         in the correct order.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               int n = 1;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int n = 10; #distractor
            {{endgroup}}
            {{group}}
               int sum = 0;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int sum = n;  #distractor
            {{endgroup}}
            {{group}}
               while (n <= 10) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (n < 100) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (n <= 9) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
                  cout << n << '\n';  #distractor
            {{endgroup}}
            {{group}}
                  sum = sum + n;
            {{endgroup}}
            {{group}}
                  n++;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q4

      .. tb-parsons::
         :name: mucp_6_4

         Let's write the code for the repeat_hello function. repeat_hello 
         should be a void function that takes no arguments and uses a while
         loop to print out "hello" three times.  

         .. code-block:: cpp

            {{group}}
            void repeat_hello () {
            {{endgroup}}
            {{distractor}}
            {{group}}
            repeat_hello () {
            {{endgroup}}
            {{group}}
               int n = 0;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int n = 0
            {{endgroup}}
            {{group}}
               while (n < 3) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (n > 3) {
            {{endgroup}}
            {{group}}
                  cout << "hello" << '\n';
            {{endgroup}}
            {{group}}
                  n++;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q5

      .. tb-parsons::
         :name: mucp_6_5

         Now let's generalize the repeat_hello function so that it repeats a given string three times.
         Let's write the code for the repeat_string function, which takes 
         input as a parameter and uses a while loop to print out the string three times.  

         .. code-block:: cpp

            {{group}}
            void repeat_string (string input) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void repeat_string () {
            {{endgroup}}
            {{group}}
               int n = 0;
            {{endgroup}}
            {{group}}
               while (n < 3) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (3 > n) {
            {{endgroup}}
            {{group}}
                  cout << input << '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
                  cout << string << '\n';
            {{endgroup}}
            {{group}}
                  n++;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q6

      .. tb-parsons::
         :name: mucp_6_6

         We can further generalize repeat_string so that it repeats a given string a given number of times. 
         Let's write the code for the new repeat_string function, which takes 
         input and x as parameters and uses a while loop to print out the string x number of times.  

         .. code-block:: cpp

            {{group}}
            void repeat_string (string input, int x) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void repeat_string (string input, string x) {
            {{endgroup}}
            {{group}}
               int n = 0;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int n = x;
            {{endgroup}}
            {{group}}
               while (n < x) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (x < n) {
            {{endgroup}}
            {{group}}
                  cout << input << '\n';
            {{endgroup}}
            {{group}}
                  n++;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  x++;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q7

      .. tb-parsons::
         :name: mucp_6_7

         On the last day of every year, we count down the seconds before the new year arrives.
         Write the function new_year_countdown, which prints out a countdown from 10 and then
         prints out "Happy New Year!".

         .. code-block:: cpp

            {{group}}
            void new_year_countdown () {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void new_year_countdown (string input) {
            {{endgroup}}
            {{group}}
               int n = 10;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int n = 0;
            {{endgroup}}
            {{group}}
               while (n > 0) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (n != 10) {
            {{endgroup}}
            {{group}}
                  cout << n << ' ';
            {{endgroup}}
            {{group}}
                  n--;
            {{endgroup}}
            {{group}}
                  n++;  #
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               cout << "Happy New Year!" << '\n';
            }
            {{endgroup}}

   .. tb-tab:: Q8

      .. tb-parsons::
         :name: mucp_6_8

         Help Goku reach power levels of over 9000! Write the function
         power_up which takes power_level as a parameter.
         power_up checks to see if power_level is over 9000. If it 
         isn't, it repeatedly prints "More power!" and increments power_level by 
         1000 until power_level is over 9000. Then power_up prints "It's over 9000!".
         Put the necessary blocks in the correct order.

         .. code-block:: cpp

            {{group}}
            void power_up (int power_level) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void power_up () {
            {{endgroup}}
            {{distractor}}
            {{group}}
               int n = 0;  #distractor
            {{endgroup}}
            {{group}}
               while (power_level < 9000) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (power_level > 9000) {
            {{endgroup}}
            {{group}}
                  cout << "More power!" << '\n';
            {{endgroup}}
            {{group}}
                  power_level = power_level + 1000;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  power_level++;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  n++;  #distractor
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (power_level < 9000) {  #distractor
            {{endgroup}}
            {{group}}
               cout << "It's over 9000!" << '\n';
            }
            {{endgroup}}

   .. tb-tab:: Q9

      .. tb-parsons::
         :name: mucp_6_9

         Write the function summation which takes two 
         parameters, start and end. summation adds
         all the integers from start to end, inclusive, together and returns
         the sum. Put the necessary blocks in the correct order.

         .. code-block:: cpp

            {{group}}
            int summation (int start, int end) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void summation (int start, int end) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            int summation () {  #distractor
            {{endgroup}}
            {{group}}
               int n = start;
            {{endgroup}}
            {{group}}
               int sum = 0;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int sum = start;  #distractor
            {{endgroup}}
            {{group}}
               while (n <= end) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (n < end) {
            {{endgroup}}
            {{group}}
                  sum = sum + n;
            {{endgroup}}
            {{group}}
                  n++;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               return sum;
            {{endgroup}}
            {{distractor}}
            {{group}}
               return n;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q10

      .. tb-parsons::
         :name: mucp_6_10

         Write the function reverse_number which takes num
         as a parameter and returns num but with its digits reversed.
         For example, reverse_number (1324) returns 4231. 
         Put the necessary blocks in the correct order, with reverse
         declared first, then temp, and lastly remainder.

         .. code-block:: cpp

            {{group}}
            int reverse_number (int num) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void reverse_number (int num) {  #distractor
            {{endgroup}}
            {{group}}
               int reverse = 0;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int reverse = 0  #distractor
            {{endgroup}}
            {{group}}
               int temp = num;
            {{endgroup}}
            {{group}}
               int remainder = 0;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int remainder;  #distractor
            {{endgroup}}
            {{group}}
               while (temp > 0) {
            {{endgroup}}
            {{group}}
                  remainder = temp % 10;
            {{endgroup}}
            {{group}}
                  reverse = reverse * 10 + remainder;
            {{endgroup}}
            {{group}}
                  temp = temp / 10;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               return reverse;
            {{endgroup}}
            {{distractor}}
            {{group}}
               return temp;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

