Activecode Exercises
--------------------

Answer the following **Activecode** questions to assess what you have learned in this chapter.

.. tabbed:: tab_check

   .. tab:: Q1

      .. tabbed:: VARS_a1

         .. tab:: Question

            .. activecode:: VARS_a1q
               :language: cpp
               :nocodelens:

               Fix the code below so that it compiles and runs without errors.
               Hint: you might need to change the names of some variables.
               ~~~~
               #include <iostream>

               int main () {
                   char true = 'T';
                   char false = 'F';
                   std::cout << "Program complete.\n";
               }

         .. tab:: Answer

            .. activecode:: VARS_a1a
               :language: cpp
               :nocodelens:

               Below is one way to fix the program.  ``true`` and ``false``
               are keywords, so they cannot be used as variable names.
               ~~~~
               #include <iostream>

               int main () {
                   char t = 'T';
                   char f = 'F';
                   std::cout << "Program complete.\n";
               }    

   .. tab:: Q2

      .. activecode:: VARS_a2
         :language: cpp
         :nocodelens:

         Finish the code below so that it prints "I drive a 2014 Buick Regal".

         This code does not need to include a main.
         It is already provided as part of the test.
         ~~~~
         #include <string>

         std::string my_car;
         my_car = "Buick"

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
             std::string expected = "I drive a 2014 Buick Regal";
             check("test expected string", my_car,  expected);
         }





   .. tab:: Q3

      .. tabbed:: VARS_a3

         .. tab:: Question

            .. activecode:: VARS_a3q
               :language: cpp
               :nocodelens:

               Fix the code below so that it prints "Cady scored 90% on the exam." 
               ~~~~
               #include <iostream>

               int main() {
                   // Modify the next line so that Cady = 0.9.
                   int Cady = 3 * 5 * (6 / 100);

                   // DO NOT MODIFY ANYTHING BELOW THIS LINE.
                   std::cout << "Cady scored " << Cady * 100 << "% on the exam.";
               }

         .. tab:: Answer

            .. activecode:: VARS_a3a
               :language: cpp
               :nocodelens:

               Below is one way to fix the program.
               We want to use doubles so that our result isn't truncated
               to 0 through integer division.
               ~~~~
               #include <iostream>

               int main() {
                   double Cady = (3 * 5) * 6 / 100.0;
                   std::cout << "Cady scored " << Cady * 100 << "% on the exam.";
               }    


   .. tab:: Q4

      .. activecode:: VARS_a4
         :language: cpp
         :nocodelens:

         Finish the code below so that it shows the correct volume of a sphere.
         Hint: watch out for integer division.

         This code does not need to include a main.
         It is already provided as part of the test.
         ~~~~
         int radius = 5;
         double pi = 3.14159;

         // Use these variables and the formula for volume to complete the next line.
         volume = 

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
         bool close_to(double x, double y)
         {
             return std::abs(x-y) < 0.001;
         }
         int main() {
             check("test radius of 5...", volume,  523.598, close_to);
         }


   .. tab:: Q5

      .. tabbed:: VARS_a5

         .. tab:: Question

            .. activecode:: VARS_a5q
               :language: cpp
               :nocodelens:

               Fix the code below so that assigns ``a`` its correct value of ``'a'``.
               Hint: use character operations!
               ~~~~
               #include <iostream>

               int main () {
                  char a = 's';

                  // Fix the line below.  Do NOT change the numbers!  Instead, 
                  // change the location of the parentheses.
                  a = a - 3 * 4 + (1 + 3);

                  // DO NOT MODIFY ANYTHING BELOW THIS LINE.
                  std::cout << a;
               }

         .. tab:: Answer

            .. activecode:: VARS_a5a
               :language: cpp
               :nocodelens:

               Below is one way to complete the program.
               There are many creative ways that you could use the
               order of operations to come up with a complex expression that
               will bring you to ``'a'``, here is one way.
               ~~~~
               #include <iostream>
            
               int main () {
                  char a = 's';
                  a = a - (3 * (4 + 1) + 3);
                  std::cout << a;
               }


   .. tab:: Q6

      .. activecode:: VARS_a6
         :language: cpp
         :nocodelens:

         Finish this program so that it assigns
         "apples" to the variable oranges,
         and "oranges" to the variable apples, then swaps their values.
         Be sure to inclue any necessary headers.

         Avoid 'hardcoding' your solution.
         ~~~~
         int main () {
             
             // DO NOT MODIFY ANYTHING BELOW THIS LINE.
             cout << "Your solution had apples = " << apples 
                  << " and oranges = " << oranges << ".\n"; 
             cout << "The correct solution has apples = apples, and oranges = oranges.";
         }


   .. tab:: Q7

      .. tabbed:: VARS_a7

         .. tab:: Question

            .. activecode:: VARS_a7q
               :language: cpp
               :nocodelens:

               Write code that prints "Live", "Laugh", and "Love" on
               3 consecutive lines.
               Be sure to inclue any necessary headers.
               ~~~~
               int main () {

               }

         .. tab:: Answer

            .. activecode:: VARS_a7a
               :language: cpp
               :nocodelens:

               Below is one way to implement the solution.
               ~~~~
               #include <iostream>

               int main () {
                   std::cout << "Live\nLaugh\nLove";
               } 


   .. tab:: Q8

      .. activecode:: VARS_a8
         :language: cpp
         :nocodelens:

         Write code that calculates how much you you will spend after 
         tipping 20% on your $36.25 dinner.
         Store the tip in a variable ``tip``.
         Save the final result of this calculation in ``plus_tip``.

         This code does not need to include a main.
         It is already provided as part of the test.
         ~~~~
         tip = 0;
         plus_tip = 0;

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
         bool close_to(double x, double y)
         {
             return std::abs(x-y) < 0.001;
         }
         int main() {
             check("test 20% tip on $36.25", tip,  7.25, close_to);
             check("test $36.25 plus tip ", plus_tip,  43.5, close_to);
         }



   .. tab:: Q9

      .. tabbed:: VARS_a9

         .. tab:: Question

            .. activecode:: VARS_a9q
               :language: cpp
               :nocodelens:

               You have about three hours and fifteen minutes of homework to do today.
               Rather than starting it right away, you choose to procrastinate
               by calculating how many seconds you'll be spending on your work.
               Convert the time to seconds and store the result in ``seconds``.

               This code does not need to include a main.
               It is already provided as part of the test.
               ~~~~

               seconds = 0;

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
                   check("test 3 hrs 15 min in seconds", seconds,  11700);
               }



         .. tab:: Answer

            .. activecode:: VARS_a9a
               :language: cpp
               :nocodelens:

               Below is one way to implement the solution.
               ~~~~

               int hours = 3;
               int minutes = 15;
               int total_minutes = minutes + 60 * hours;
               int seconds = total_minutes * 60;

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
                   check("test 3 hrs 15 min in seconds", seconds,  11700);
               }




   .. tab:: Q10

      .. activecode:: VARS_a10
         :language: cpp
         :nocodelens:

         Write code that calculates and prints the average of a and b if 
         a = 3.14, and b = 1.59.
         You may only use one line of code.
         Be sure to inclue any necessary headers.
         ~~~~
         int main () {

             // DO NOT MODIFY ANYTHING BELOW THIS LINE.
             std::cout << "\nYour program should have printed 2.365\n";
         }

