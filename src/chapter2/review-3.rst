.. _variables-types-activecode-exercises:

Activecode Exercises
--------------------

Answer the following **Activecode** questions to assess what you have learned in this chapter.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-group::
         :name: VARS_a1

         .. tb-tab:: Question

            Fix the code below so that it compiles and runs without errors.
            Hint: you might need to change the names of some variables.

            .. tb-code:: cpp
               :name: VARS_a1q
               :caption: Example VARS_a1q

               #include <iostream>

               int main () {
                   char true = 't';
                   char false = 'F';
                   std::cout << "Program complete.\n";
               }

         .. tb-tab:: Answer

            Below is one way to fix the program.  ``true`` and ``false``
            are keywords, so they cannot be used as variable names.

            .. tb-code:: cpp
               :name: VARS_a1a
               :caption: Example VARS_a1a

               #include <iostream>

               int main () {
                   char t = 't';
                   char f = 'F';
                   std::cout << "Program complete.\n";
               }    

   .. tb-tab:: Q2

      Finish the code below so that it prints "I drive a 2014 Buick Regal".

      This code does not need to include a main.
      It is already provided as part of the test.

      .. tb-code:: cpp
         :name: VARS_a2-support
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
             std::string expected = "I drive a 2014 Buick Regal";
             check("test expected string", my_car,  expected);
         }






      .. tb-code:: cpp
         :name: VARS_a2
         :caption: Example VARS_a2
         :run-after: VARS_a2-support

         #include <string>

         std::string my_car;
         my_car = "Buick"

   .. tb-tab:: Q3

      .. tb-group::
         :name: VARS_a3

         .. tb-tab:: Question

            Fix the code below so that it prints "Cady scored 90% on the exam." 

            .. tb-code:: cpp
               :name: VARS_a3q
               :caption: Example VARS_a3q

               #include <iostream>

               int main() {
                   // Modify the next line so that Cady = 0.9.
                   int Cady = 3 * 5 * (6 / 100);

                   // DO NOT MODIFY ANYTHING BELOW THIS LINE.
                   std::cout << "Cady scored " << Cady * 100 << "% on the exam.";
               }

         .. tb-tab:: Answer

            Below is one way to fix the program.
            We want to use doubles so that our result isn't truncated
            to 0 through integer division.

            .. tb-code:: cpp
               :name: VARS_a3a
               :caption: Example VARS_a3a

               #include <iostream>

               int main() {
                   double Cady = (3 * 5) * 6 / 100.0;
                   std::cout << "Cady scored " << Cady * 100 << "% on the exam.";
               }    


   .. tb-tab:: Q4

      Finish the code below so that it shows the correct volume of a sphere.
      Hint: watch out for integer division.

      This code does not need to include a main.
      It is already provided as part of the test.

      .. tb-code:: cpp
         :name: VARS_a4-support
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
         bool close_to(double x, double y)
         {
             return std::abs(x-y) < 0.001;
         }
         int main() {
             check("test radius of 5...", volume,  523.598, close_to);
         }



      .. tb-code:: cpp
         :name: VARS_a4
         :caption: Example VARS_a4
         :run-after: VARS_a4-support

         int radius = 5;
         double pi = 3.14159;

         // Use these variables and the formula for volume to complete the next line.
         volume = 

   .. tb-tab:: Q5

      .. tb-group::
         :name: VARS_a5

         .. tb-tab:: Question

            Fix the code below so that assigns ``a`` its correct value of ``'a'``.
            Hint: use character operations!

            .. tb-code:: cpp
               :name: VARS_a5q
               :caption: Example VARS_a5q

               #include <iostream>

               int main () {
                  char a = 's';

                  // Fix the line below.  Do NOT change the numbers!  Instead, 
                  // change the location of the parentheses.
                  a = a - 3 * 4 + (1 + 3);

                  // DO NOT MODIFY ANYTHING BELOW THIS LINE.
                  std::cout << a;
               }

         .. tb-tab:: Answer

            Below is one way to complete the program.
            There are many creative ways that you could use the
            order of operations to come up with a complex expression that
            will bring you to ``'a'``, here is one way.

            .. tb-code:: cpp
               :name: VARS_a5a
               :caption: Example VARS_a5a

               #include <iostream>

               int main () {
                  char a = 's';
                  a = a - (3 * (4 + 1) + 3);
                  std::cout << a;
               }


   .. tb-tab:: Q6

      Finish this program so that it assigns
      "apples" to the variable oranges,
      and "oranges" to the variable apples, then swaps their values.
      Be sure to inclue any necessary headers.

      Avoid 'hardcoding' your solution.

      .. tb-code:: cpp
         :name: VARS_a6
         :caption: Example VARS_a6

         int main () {

             // DO NOT MODIFY ANYTHING BELOW THIS LINE.
             cout << "Your solution had apples = " << apples 
                  << " and oranges = " << oranges << ".\n"; 
             cout << "The correct solution has apples = apples, and oranges = oranges.";
         }


   .. tb-tab:: Q7

      .. tb-group::
         :name: VARS_a7

         .. tb-tab:: Question

            Write code that prints "Live", "Laugh", and "Love" on
            3 consecutive lines.
            Be sure to inclue any necessary headers.

            .. tb-code:: cpp
               :name: VARS_a7q
               :caption: Example VARS_a7q

               int main () {

               }

         .. tb-tab:: Answer

            Below is one way to implement the solution.

            .. tb-code:: cpp
               :name: VARS_a7a
               :caption: Example VARS_a7a

               #include <iostream>

               int main () {
                   std::cout << "Live\n_laugh\n_love";
               } 


   .. tb-tab:: Q8

      Write code that calculates how much you you will spend after 
      tipping 20% on your $36.25 dinner.
      Store the tip in a variable ``tip``.
      Save the final result of this calculation in ``plus_tip``.

      This code does not need to include a main.
      It is already provided as part of the test.

      .. tb-code:: cpp
         :name: VARS_a8-support
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
         bool close_to(double x, double y)
         {
             return std::abs(x-y) < 0.001;
         }
         int main() {
             check("test 20% tip on $36.25", tip,  7.25, close_to);
             check("test $36.25 plus tip ", plus_tip,  43.5, close_to);
         }




      .. tb-code:: cpp
         :name: VARS_a8
         :caption: Example VARS_a8
         :run-after: VARS_a8-support

         tip = 0;
         plus_tip = 0;

   .. tb-tab:: Q9

      .. tb-group::
         :name: VARS_a9

         .. tb-tab:: Question

            You have about three hours and fifteen minutes of homework to do today.
            Rather than starting it right away, you choose to procrastinate
            by calculating how many seconds you'll be spending on your work.
            Convert the time to seconds and store the result in ``seconds``.

            This code does not need to include a main.
            It is already provided as part of the test.

            .. tb-code:: cpp
               :name: VARS_a9q-support
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
                   check("test 3 hrs 15 min in seconds", seconds,  11700);
               }




            .. tb-code:: cpp
               :name: VARS_a9q
               :caption: Example VARS_a9q
               :run-after: VARS_a9q-support


               seconds = 0;

         .. tb-tab:: Answer

            Below is one way to implement the solution.

            .. tb-code:: cpp
               :name: VARS_a9a-support
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
                   check("test 3 hrs 15 min in seconds", seconds,  11700);
               }





            .. tb-code:: cpp
               :name: VARS_a9a
               :caption: Example VARS_a9a
               :run-after: VARS_a9a-support


               int hours = 3;
               int minutes = 15;
               int total_minutes = minutes + 60 * hours;
               int seconds = total_minutes * 60;

   .. tb-tab:: Q10

      Write code that calculates and prints the average of a and b if 
      a = 3.14, and b = 1.59.
      You may only use one line of code.
      Be sure to inclue any necessary headers.

      .. tb-code:: cpp
         :name: VARS_a10
         :caption: Example VARS_a10

         int main () {

             // DO NOT MODIFY ANYTHING BELOW THIS LINE.
             std::cout << "\n_your program should have printed 2.365\n";
         }

