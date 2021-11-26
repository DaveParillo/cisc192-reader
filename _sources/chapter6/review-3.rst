Coding Practice
---------------

.. tabbed:: self_check

   .. tab:: Q1

      .. tabbed:: cp_6_1

          .. tab:: Question

              Write a program that prints out a 5x5 triangle using asterisks. 
              An example is shown below. Your code should use while loops.

              :: 
         
                 *
                 **
                 ***
                 ****
                 *****

              .. activecode:: cp_6_AC_1q
                 :language: cpp
                 :practice: T

                 #include <iostream>

                 int main() {
                     // Write your implementation here.
                 }


          .. tab:: Answer

              Below is one way to implement the program. We use nested loops
              similar to the last version of the ``multiples_table`` function
              to print out the triangular shape.

              .. activecode:: cp_6_AC_1a
                 :language: cpp
                 :optional:

                 #include <iostream>
                 using std::cout;

                 int main() {
                     int row = 0;
                     while (row < 5) {
                         int col = 0;
                         while (col <= row) {
                             cout << '*';
                             col++;
                         }
                         cout << '\n';
                         row++;
                     }
                 }

   .. tab:: Q2

      .. activecode:: cp_6_AC_2q
         :language: cpp

         Encapsulate the triangle printing program into a function called
         ``print_triangle``. Generalize it so that it takes a parameter
         ``int n`` to generate a nxn triangle. Call your function in main
         with an input of 4, which should result in the following output:

         :: 

             *
             **
             ***
             ****
         ~~~~
         #include <iostream>

         void print_triangle (int n) {
             // Write your implementation here.
         }

         int main() {
             // Write your implementation here.
         }

   .. tab:: Q3

      .. tabbed:: cp_6_3

          .. tab:: Question

             Write a function called ``print_pyramid`` that prints out an ``n``\x``n`` pyramid using asterisks. 
             An example is shown below with ``n`` equal to 5. Your code should use while loops.

             :: 
         
                     *
                    ***
                   *****
                  *******
                 *********

             .. activecode:: cp_6_AC_3q
                :language: cpp
                :practice: T

                #include <iostream>

                void print_pyramid (int n) {
                    // Write your implementation here.
                }

                int main() {
                    print_pyramid (5);
                }


          .. tab:: Answer

             Below is one way to implement the program. We use multiple ``while``
             loops to print out spaces and asterisks. The outer loop creates the 
             number of rows, and within the outer loop, the two inner loops
             print out the correct number of spaces and asterisks.

             .. activecode:: cp_6_AC_3a
                :language: cpp
                :optional:

                #include <iostream>
                using std::cout;

                void print_pyramid(int n) {
                    int count = 1;
                    while (count <= n) {
                        int space = n - count;
                        while (space > 0) {
                            cout << ' ';
                            space--;
                        }
                        int numAsterisks = 2 * count - 1;
                        while (numAsterisks > 0) {
                            cout << '*';
                            numAsterisks--;
                        }
                        cout << '\n';
                        count++;
                    }
                }

                int main() {
                    print_pyramid (5);
                }

   .. tab:: Q4

      .. activecode:: cp_6_AC_4q
         :language: cpp
         :practice: T

         Write a function called ``number_pyramid`` that prints out an ``n`` x ``n`` number pyramid. 
         An example is shown below with ``n`` equal to 5. Your code should use while loops.
         (Hint: similar to the previous question, if you want the output to look nice, using conditionals
         that print different amounts of spaces.)

         :: 
         
                 1
                222
               33333
              4444444
             555555555
         ~~~~
         #include <iostream>

         void number_pyramid (int n) {
             // Write your implementation here.
         }

         int main() {
             number_pyramid (5);
         }

   .. tab:: Q5

      .. tabbed:: cp_6_5

          .. tab:: Question

             A common coding interview question that's also a popular children's game used to teach division is
             FizzBuzz. Write a program that uses a while loop and prints the numbers 1 through 100, but every
             multiple of 3 is replaced with the word "Fizz," every multiple of 5 is replaced with the word "Buzz," 
             and every multiple of both 3 and 5 is replaced with "FizzBuzz." Your output should be the following:

             :: 
         
                 1
                 2
                 Fizz
                 4
                 Buzz
                 ...
                 14
                 FizzBuzz
                 16
                 ...
                 98
                 Fizz
                 Buzz

             .. activecode:: cp_6_AC_5q
                :language: cpp
                :practice: T

                #include <iostream>

                int main() {
                    // Write your implementation here.
                }


          .. tab:: Answer

             Below is one way to implement the "FizzBuzz" program. We use conditionals
             with modulus operators in a while loop to categorize every number and print
             the correct output. Feel free to search up on the FizzBuzz coding interview 
             problem if you are interested in other ways to code this program!

             .. activecode:: cp_6_AC_5a
                :language: cpp
                :optional:

                #include <iostream>

                int main() {
                    using std::cout;
                    int n = 1;
                    while (n <= 100) {
                        if (n % 15 == 0) {
                            cout << "FizzBuzz\n";
                        }
                        else if (n % 3 == 0) {
                            cout << "Fizz\n";
                        }
                        else if (n % 5 == 0) {
                            cout << "Buzz\n";
                        }
                        else {
                            cout << n << '\n';
                        }
                        n++;
                    }
                }

   .. tab:: Q6

      .. activecode:: cp_6_AC_6q
         :language: cpp
         :practice: T

         Write the function ``addition_table`` which takes an ``int n`` as a parameter
         and prints out a nxn addition table. Call your function in ``main`` with
         "10" as the argument. Your output should look like this:

         :: 

             0       1       2       3       4       5       6       7       8       9       10
             1       2       3       4       5       6       7       8       9       10      11
             2       3       4       5       6       7       8       9       10      11      12
             3       4       5       6       7       8       9       10      11      12      13
             4       5       6       7       8       9       10      11      12      13      14
             5       6       7       8       9       10      11      12      13      14      15
             6       7       8       9       10      11      12      13      14      15      16
             7       8       9       10      11      12      13      14      15      16      17
             8       9       10      11      12      13      14      15      16      17      18
             9       10      11      12      13      14      15      16      17      18      19
             10      11      12      13      14      15      16      17      18      19      20
         ~~~~
         #include <iostream>

         void addition_table (int n) {
             // Write your implementation here.
         }

         int main() {
             // Call your function here.
         }

   .. tab:: Q7

      .. tabbed:: cp_6_7

          .. tab:: Question

             A number is a prime number if its only factors are 1 and itself.
             Write the function ``is_prime``, which takes an ``int num`` as a parameters.
             ``is_prime`` is a boolean function that returns ``true`` if ``num`` is a prime
             number and returns ``false`` otherwise. Run and test your code!

             .. activecode:: cp_6_AC_7q
                :language: cpp
                :practice: T

                bool is_prime (int num) {
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
                  check("1  is not prime", is_prime(1), false);
                  check("13 is prime", is_prime(13), true);
                  check("24 is not prime", is_prime(24), false);
                  check("997 is prime", is_prime(997), true);
                  check("0 is not prime", is_prime(0), false);
                }

          .. tab:: Answer

             Below is one way to implement the ``is_prime`` function. First, 
             we check to see if ``num`` is less than or equal to 1, and return
             ``false`` if that is the case. Next, we use a ``while`` loop
             to continuously check if a factor ``n`` divides ``num`` evenly.
             If it does, we return ``false``. If no value of ``n`` divides ``num``
             evenly, then we return ``true``. Notice the ``while`` loop only goes up to
             ``num / 2`` because if 2 doesn't divide evenly, then there isn't a smaller factor.

             .. activecode:: cp_6_AC_7a
                :language: cpp
                :optional:

                #include <iostream>

                bool is_prime (int num) {
                    if (num <= 1) {
                        return false;
                    }
                    int n = 2;
                    while (n < num / 2) {
                        if (num % n == 0) {
                            return false;
                        }
                        n++;
                    }
                    return true;
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
                  check("1  is not prime", is_prime(1), false);
                  check("13 is prime", is_prime(13), true);
                  check("24 is not prime", is_prime(24), false);
                  check("997 is prime", is_prime(997), true);
                  check("0 is not prime", is_prime(0), false);
                }

   .. tab:: Q8

      .. activecode:: cp_6_AC_8q
         :language: cpp
         :practice: T

         Write a program that uses a ``while`` loop to print out the alphabet from 'a' to 'z'.
         ~~~~
         #include <iostream>

         int main() {
             // Write your implementation here.
         }

   .. tab:: Q9

      .. tabbed:: cp_6_9

          .. tab:: Question

             The Fibonacci sequence is a sequence of numbers such that each
             successive number is the sum of the two previous numbers.
             This sequence is as follows: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34,
             and so on. Write a program that prints the first 20 Fibonacci
             numbers.

             .. activecode:: cp_6_AC_9q
                :language: cpp
                :practice: T

                #include <iostream>

                int main() {
                    // Write your implementation here.
                }


          .. tab:: Answer

             Below is one way to implement the program. First, 
             we initialize the first two Fibonacci numbers and print the
             first two values out right away.
             Next we use a ``while`` loop to compute the remaining values.
             The next number in the sequence is the sum of the previous two,
             so we compute the sum and then we need to update the values
             of the "previous two Fibonacci numbers" for the next loop iteration.

             .. activecode:: cp_6_AC_9a
                :language: cpp
                :optional:

                 #include <iostream>

                 int main() {
                     int first = 0;
                     int second = 1;
                     std::cout << first << ' '
                               << second << ' ';
                     int n = 2;
                     while (n < 20) {
                         int next = first + second;
                         std::cout << next << ' ';
                         first = second;
                         second = next;
                         ++n;
                     }
                 }

   .. tab:: Q10

      .. activecode:: cp_6_AC_10q
         :language: cpp
         :practice: T

         Write a function called ``factorial`` which takes an ``int n`` as a parameter
         and returns ``n`` factorial. Remembers that a factorial (denoted by !) is the product of all 
         positive integers less than or equal to ``n``, so 4! is 24. Use a ``while`` loop.
         Run and test your code!
         ~~~~
         #include <iostream>

         int factorial (int n) {
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
           check("factorial 4", factorial(4), 24);
           check("factorial 6", factorial(6), 720);
           check("factorial 8", factorial(8), 40320);
           check("factorial 9", factorial(9), 362880);
           check("factorial 11", factorial(11), 39916800);
         }

