Activecode Exercises
--------------------

Answer the following **Activecode** questions to
assess what you have learned in this chapter.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-group::
         :name: functions_a1

         .. tb-tab:: Question

            Fix the errors in the code below so that it returns the area of
            a circle with radius ``r``.
            Use cmath functions to get an accurate value for pi.

            .. tb-code:: cpp
               :name: functions_a1q-support
               :hidden:
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

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
                   check("radius == 5", area(5),  78.5398, close_to);
                   check("radius == 7.5", area(7.5),  176.715, close_to);
               }




            .. tb-code:: cpp
               :name: functions_a1q
               :caption: Example functions_a1q
               :run-after: functions_a1q-support
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

               double area(int r) {
                   constexpr double pi = sin(1.0);
                   double area = pi * r ^ 2;
                   return area;
               }

         .. tb-tab:: Answer

            Below is one way to fix the program.
            C++ doesn't use the ``^`` operator for exponents.
            We can get the square of ``r`` by multiplying it by itself.

            .. tb-code:: cpp
               :name: functions_a1a-support
               :hidden:
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

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
                   check("radius == 5", area(5),  78.5398, close_to);
                   check("radius == 7.5", area(7.5),  176.715, close_to);
               }





            .. tb-code:: cpp
               :name: functions_a1a
               :caption: Example functions_a1a
               :run-after: functions_a1a-support
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

               #include <cmath>

               double area(double r) {
                   constexpr double pi = 4*atan(1.0);
                   double area = pi * r * r;
                   return area;
               }

   .. tb-tab:: Q2

      Fix the code below so that it prints "2 elephants".

      .. tb-code:: cpp
         :name: functions_a2
         :caption: Example functions_a2
         :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

         #include <iostream>
         using namespace std;

         void printAnimals(string a, int b) {
             cout << b << a;
         }

         int main () {
             // DO NOT MODIFY ANYTHING BELOW THIS LINE
             printAnimals(2, "elephants");
         }


   .. tb-tab:: Q3

      .. tb-group::
         :name: functions_a3

         .. tb-tab:: Question

            Fix the code below so that it prints ``12 / 8 = 1.5.``

            .. tb-code:: cpp
               :name: functions_a3q
               :caption: Example functions_a3q
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

               #include <iostream>

               void divide (int a, int b) {
                   cout << a / b;
               }

               int main () {
                   int a = 8;
                   int b = 12;

                   // DO NOT MODIFY ANYTHING BELOW THIS LINE
                   cout << b << " / " << a << " = "; divide (a, b);
               }

         .. tb-tab:: Answer

            Below is one way to fix the program.
            It's crucial that you input your arguments in the correct order
            so as to avoid a semantic error.
            Also, it's important that you understand that when you divide
            two integers... you will get an integer as a result.

            .. tb-code:: cpp
               :name: functions_a3a
               :caption: Example functions_a3a
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

               #include <iostream>

               void divide (double a, double b) {
                   std::cout << a / b;
               }

               int main () {
                   int a = 8;
                   int b = 12;
                   std::cout << b << " / " << a << " = "; divide (b, a);
               }


   .. tb-tab:: Q4

      Finish the code below so that it calculates the common log of ``a``
      minus the *natural* log of ``a`` and returns the difference.
      You will need to use cmath functions.

      .. tb-code:: cpp
         :name: functions_a4-support
         :hidden:
         :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

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
             check("test value == 8", log_subtract(8),  -1.17635, close_to);
             check("test value == 42", log_subtract(42), -2.11442, close_to);
             check("test value == pi", log_subtract(3.14159),  -0.64758, close_to);
             check("test value == 1776", log_subtract(1776), -4.23268, close_to);
         }






      .. tb-code:: cpp
         :name: functions_a4
         :caption: Example functions_a4
         :run-after: functions_a4-support
         :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']


         double log_subtract (double a) {

             return difference;
         }

         int main () {
             // DO NOT MODIFY ANYTHING BELOW THIS LINE
             cout << "Testing with a = 8..." << endl; 
             cout << "    Your solution has difference = "; 
             logSubtraction(8); 
             cout << endl; 
             cout << "    The correct solution has difference = -1.17635" << endl; 
             cout << "Testing with a = -2..." << endl; 
             cout << "    Your solution has difference = "; logSubtraction(-2); 
             cout << endl; 
             cout << "    The correct solution has difference = nan";
         }

   .. tb-tab:: Q5

      .. tb-group::
         :name: functions_a5

         .. tb-tab:: Question

            Finish the code below so that it prints "First Line", a border,
            and "Second Line." on three separate lines.

            .. tb-code:: cpp
               :name: functions_a5q
               :caption: Example functions_a5q
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

               #include <iostream>
               using namespace std;

               void border () {
                   cout << "------------\n";
               }

               int main () {
                   // Write some code below to call the function appropriately

               }

         .. tb-tab:: Answer

            Below is one way to complete the program.

            .. tb-code:: cpp
               :name: functions_a5a
               :caption: Example functions_a5a
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

               #include <iostream>
               using std::cout;

               void border () {
                   cout << "------------\n";
               }

               int main () {
                   cout << "First Line.\n";
                   border();
                   cout << "Second Line.\n";
               }


   .. tb-tab:: Q6

      Write a function called ``int_division`` that takes two doubles
      as parameters and returns the quotient of the **integer division**
      of the first number divided by the second.  Be sure to include any necessary headers.

      .. tb-code:: cpp
         :name: functions_a6-support
         :hidden:
         :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

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
             check("test a = 2.4, b = 6.8...", int_division(2.4, 6.8), 0);
             check("test a = -8.6, b = 4.2...", int_division(-8.6, 4.2), -2);
             check("test a = 42.2, b = 11.5...", int_division(42.2, 11.5), 3);
         }



      .. tb-code:: cpp
         :name: functions_a6
         :caption: Example functions_a6
         :run-after: functions_a6-support
         :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

         int int_division () {

             return quotient;
         }

   .. tb-tab:: Q7

      .. tb-group::
         :name: functions_a7

         .. tb-tab:: Question

            Write a function called ``gpa_boost`` that returns your GPA
            rounded up to the nearest whole value.
            If your GPA is already at the nearest whole value,
            then there is no rounding.
            Be sure to include any necessary headers.

            .. tb-code:: cpp
               :name: functions_a7q-support
               :hidden:
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

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
                   check("test gpa == 2.513", gpa_boost(2.513),  3.0, close_to);
                   check("test gpa == 4.000", gpa_boost(4.000),  4.0, close_to);
                   check("test gpa == 2.999", gpa_boost(2.999),  3.0, close_to);
                   check("test gpa == 3.0001", gpa_boost(3.0001),  4.0, close_to);
               }



            .. tb-code:: cpp
               :name: functions_a7q
               :caption: Example functions_a7q
               :run-after: functions_a7q-support
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

               double gpa_boost () {

               }

         .. tb-tab:: Answer

            Below is one way to complete the program.
            I used the :numeric:`ceil <math/ceil> function from the 
            ``cmath`` library, but you could have solved this problem
            without using any functions from ``cmath``.

            .. tb-code:: cpp
               :name: functions_a7a-support
               :hidden:
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

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
                   check("test gpa == 2.513", gpa_boost(2.513),  3.0, close_to);
                   check("test gpa == 4.000", gpa_boost(4.000),  4.0, close_to);
                   check("test gpa == 2.999", gpa_boost(2.999),  3.0, close_to);
                   check("test gpa == 3.0001", gpa_boost(3.0001),  4.0, close_to);
               }



            .. tb-code:: cpp
               :name: functions_a7a
               :caption: Example functions_a7a
               :run-after: functions_a7a-support
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

               #include <cmath>

               double gpa_boost (double gpa) {
                   return ceil(gpa);
               }

   .. tb-tab:: Q8

      Write a function called ``volume_prism`` that takes three ``double``
      side-lengths as parameters, and returns the volume of a the 
      rectangular prism.  Be sure to include any necessary headers.

      .. tb-code:: cpp
         :name: functions_a8-support
         :hidden:
         :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

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
             check("test a = 3, b = 4, c = 5...", volume_prism(3,4,5),  60.0, close_to);
             check("test a = 5.7, b = 3.9, c = 1.3...", volume_prism(5.7,3.9,1.3),  28.899, close_to);
         }




      .. tb-code:: cpp
         :name: functions_a8
         :caption: Example functions_a8
         :run-after: functions_a8-support
         :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

         volume_prism ();

   .. tb-tab:: Q9

      .. tb-group::
         :name: functions_a9

         .. tb-tab:: Question

            Write a function called ``tan_degrees`` that returns the 
            tangent of an angle given as a ``double`` in degrees.
            Use ``3.14159`` for pi.
            Be sure to include any necessary headers.

            .. tb-code:: cpp
               :name: functions_a9q-support
               :hidden:
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

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
                   check("test 45 degrees", tan_degrees(45),  0.9992, close_to);
                   check("test 112.1 degrees", tan_degrees(112.1),  -2.4627, close_to);
               }



            .. tb-code:: cpp
               :name: functions_a9q
               :caption: Example functions_a9q
               :run-after: functions_a9q-support
               :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

               tan_degrees ();

         .. tb-tab:: Answer

            Below is one way to complete the program.
            You need to make sure to convert your angle to radians before
            doing any calculations with trigonometric functions.

            .. tb-code:: cpp
               :name: functions_a9a-support
               :hidden:
               :compileargs: ['-Wall', '-std=c++11']

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
                   check("test 45 degrees", tan_degrees(45),  0.9992, close_to);
                   check("test 112.1 degrees", tan_degrees(112.1),  -2.4627, close_to);
               }



            .. tb-code:: cpp
               :name: functions_a9a
               :caption: Example functions_a9a
               :run-after: functions_a9a-support
               :compileargs: ['-Wall', '-std=c++11']

               #include <cmath>

               namespace mesa {
                   constexpr double pi = 3.14159;

                   double deg_to_radian (double degrees) {
                      return degrees * (pi / 180);
                   }
               }

               double tan_degrees (double degrees) {
                   double radians = mesa::deg_to_radian(degrees);
                   return tan(radians);
               }

   .. tb-tab:: Q10

      Write a function called ``volume_sphere`` that takes a ``double``
      radius as a parameter and returns the volume of a sphere with
      the provided radius.
      Use ``3.14159`` for pi.
      Be sure to include any necessary headers.

      .. tb-code:: cpp
         :name: functions_a10-support
         :hidden:
         :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

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
             check("test radius = 3", volume_sphere(3), 113.097, close_to);
             check("test radius = 3.24", volume_sphere(3.24), 142.47, close_to);
         }


      .. tb-code:: cpp
         :name: functions_a10
         :caption: Example functions_a10
         :run-after: functions_a10-support
         :compileargs: ['-Wall', '-Wextra', '-Wpedantic' '-Werror' '-std=c++11']

         volume_sphere ();

