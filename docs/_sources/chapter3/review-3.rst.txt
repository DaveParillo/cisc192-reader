Activecode Exercises
--------------------

Answer the following **Activecode** questions to
assess what you have learned in this chapter.

.. tabbed:: tab_check

   .. tab:: Q1

      .. tabbed:: functions_a1

         .. tab:: Question

            .. activecode:: functions_a1q
               :language: cpp
               :compileargs: ['-Wall', '-std=c++11']
               :nocodelens:

               Fix the errors in the code below so that it prints the area of a circle with radius 5.  Use cmath functions to get an accurate value for pi.
               ~~~~
               #include <iostream>
               using namespace std;

               void printArea(int r) {
                   double pi = acos(1.0);
                   double area = pi * r ^ 2;
                   cout << area;
               }

               int main () {
                   // DO NOT MODIFY ANYTHING BELOW THIS LINE
                   cout << "Testing with radius = 5..." << endl; cout << "    Your function had area = "; printArea(5); cout << endl; cout << "    The correct solution has area = 78.5398" << endl; cout << "Testing with radius = 7.5..." << endl; cout << "    Your function had area = "; printArea(7.5); cout << endl; cout << "    The correct solution has area = 176.715";
               }

         .. tab:: Answer

            .. activecode:: functions_a1a
               :language: cpp
               :compileargs: ['-Wall', '-std=c++11']
               :nocodelens:

               Below is one way to fix the program.  C++ doesn't use the ``^`` operator for exponents.  We can get the square of ``r`` by multiplying it by itself.  We call the function with an argument of ``5``.
               ~~~~
               #include <iostream>
               #include <cmath>
               using namespace std;

               void printArea(double r) {
                   double pi = acos(-1.0);
                   double area = pi * r * r;
                   cout << area;
               }


   .. tab:: Q2

      .. activecode:: functions_a2
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:

         Fix the code below so that it prints "2 elephants".
         ~~~~
         #include <iostream>
         using namespace std;

         void printAnimals(string a, int b) {
             cout << b << a;
         }

         int main () {
             // DO NOT MODIFY ANYTHING BELOW THIS LINE
             printAnimals(2, "elephants");
         }


   .. tab:: Q3

      .. tabbed:: functions_a3

         .. tab:: Question

            .. activecode:: functions_a3q
               :language: cpp
               :compileargs: ['-Wall', '-std=c++11']
               :nocodelens:

               Fix the code below so that it prints ``12 / 8 = 1.5.``
               ~~~~
               #include <iostream>
               using namespace std;

               void divide (int a, int b) {
                   cout << a / b;
               }

               int main () {
                   int a = 8;
                   int b = 12;

                   // DO NOT MODIFY ANYTHING BELOW THIS LINE
                   cout << b << " / " << a << " = "; divide (a, b);
               }

         .. tab:: Answer

            .. activecode:: functions_a3a
               :language: cpp
               :compileargs: ['-Wall', '-std=c++11']
               :nocodelens:

               Below is one way to fix the program.  It's crucial that you input your arguments in the correct order so as to avoid a semantic error.  Also, it's important that you understand that when you divide two integers... you will get an integer as a result.
               ~~~~
               #include <iostream>
               using namespace std;

               void divide (double a, double b) {
                   cout << a / b;
               }

               int main () {
                   int a = 8;
                   int b = 12;
                   cout << b << " / " << a << " = "; divide (b, a);
               }


   .. tab:: Q4

      .. activecode:: functions_a4
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:

         Finish the code below so that it calculates the common log of ``a`` minus the *natural* log of ``a`` and prints the difference. You will need to use cmath functions.
         ~~~~
         #include <iostream>
         using namespace std;

         void logSubtraction (double a) {
             // Create the variable difference and assign it to the difference mentioned in the instructions
             
             cout << difference;
         }

         int main () {
             // DO NOT MODIFY ANYTHING BELOW THIS LINE
             cout << "Testing with a = 8..." << endl; cout << "    Your solution has difference = "; logSubtraction(8); cout << endl; cout << "    The correct solution has difference = -1.17635" << endl; cout << "Testing with a = -2..." << endl; cout << "    Your solution has difference = "; logSubtraction(-2); cout << endl; cout << "    The correct solution has difference = nan";
         }


   .. tab:: Q5

      .. tabbed:: functions_a5

         .. tab:: Question

            .. activecode:: functions_a5q
               :language: cpp
               :compileargs: ['-Wall', '-std=c++11']
               :nocodelens:

               Finish the code below so that it prints "First Line", a border, and "Second Line." on three separate lines.
               ~~~~
               #include <iostream>
               using namespace std;

               void border () {
                   cout << "------------" << endl;
               }

               int main () {
                   // Write some code below to call the function appropriately
               
               }

         .. tab:: Answer

            .. activecode:: functions_a5a
               :language: cpp
               :compileargs: ['-Wall', '-std=c++11']
               :nocodelens:

               Below is one way to complete the program.
               ~~~~
               #include <iostream>
               using namespace std;

               void border () {
                   cout << "------------" << endl;
               }

               int main () {
                   cout << "First Line." << endl;
                   border();
                   cout << "Second Line." << endl;
               }


   .. tab:: Q6

      .. activecode:: functions_a6
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:

         Write a function called ``doubleDiv`` that takes two doubles as parameters and prints the quotient of the **integer division** of the first number divided by the second.  Be sure to include any necessary headers.
         ~~~~
         void intDivision () {

         }

         int main () {
             // DO NOT MODIFY ANYTHING BELOW THIS LINE
             cout << "Testing with a = 2.4, b = 6.8..." << endl; cout << "    Your solution has a quotient of "; intDivision(2.4, 6.8); cout << endl; cout << "    The correct solution has a quotient of 0" << endl; cout << "Testing with a = -8.6, b = 4.2..." << endl; cout << "    Your solution has a quotient of "; intDivision(-8.6, 4.2); cout << endl; cout << "    The correct solution has a quotient of -2";
         }


   .. tab:: Q7

      .. tabbed:: functions_a7

         .. tab:: Question

            .. activecode:: functions_a7q
               :language: cpp
               :compileargs: ['-Wall', '-std=c++11']
               :nocodelens:

               Write a function called gpaBoost that prints your GPA rounded up to the nearest point.  If your GPA is already at the nearest point, there is no rounding.  Be sure to include any necessary headers.
               ~~~~
               void gpaBoost () {

               }

               int main () {
                   // DO NOT MODIFY ANYTHING BELOW THIS LINE
                   cout << "Testing with GPA = 2.513..." << endl; cout << "    Your solution rounded the GPA to "; gpaBoost(2.513); cout << endl; cout << "    The correct solution rounds the GPA to 3.000" << endl; cout << "Testing with GPA = 4.000..." << endl; cout << "    Your solution rounded the GPA to "; gpaBoost(4.000); cout << endl; cout << "    The correct solution rounds the GPA to 4.000";
               }

         .. tab:: Answer

            .. activecode:: functions_a7a
               :language: cpp
               :compileargs: ['-Wall', '-std=c++11']
               :nocodelens:

               Below is one way to complete the program.  I used the ``ceil`` function from the ``cmath`` library, but you could have solved this problem without using any functions from ``cmath``.
               ~~~~
               #include <iostream>
               #include <cmath>
               using namespace std;

               void gpaBoost (double GPA) {
                   int betterGPA = ceil(GPA);
                   cout << betterGPA << ".000";
               }


   .. tab:: Q8

      .. activecode:: functions_a8
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:

         Write a function called ``volumePrism`` that takes three ``double`` sidelengths as parameters, and calculates and prints the volume of a the rectangular prism.  Be sure to include any necessary headers.
         ~~~~
         void volumePrism () {
            
         }

         int main () {
             // DO NOT MODIFY ANYTHING BELOW THIS LINE
             cout << "Testing with a = 3, b = 4, c = 5..." << endl; cout << "    Your solution calculated a volume of "; volumePrism(3,4,5); cout << endl; cout << "    The correct solution calculates a volume of 60" << endl; cout << "Testing with a = 5.7, b = 3.9, c = 1.3..." << endl; cout << "    Your solution calculated a volume of "; volumePrism(5.7,3.9,1.3); cout << endl; cout << "    The correct solution calculates a volume of 28.899";
         }


   .. tab:: Q9

      .. tabbed:: functions_a9

         .. tab:: Question

            .. activecode:: functions_a9q
               :language: cpp
               :compileargs: ['-Wall', '-std=c++11']
               :nocodelens:

               Write a function called ``tanD`` that prints the tangent of an angle given as a ``double`` in degrees. Use 3.14 for pi.  Be sure to include any necessary headers.
               ~~~~
               void tanDegrees () {

               }

               int main () {
                   // DO NOT MODIFY ANYTHING BELOW THIS LINE
                   cout << "Testing with degrees = 45..." << endl; cout << "    Your solution calculated a tangent of "; tanDegrees(45); cout << endl; cout << "    The correct solution calculates a tangent of 0.999204" << endl; cout << "Testing with degrees = 112.1..." << endl; cout << "    Your solution calculated a tangent of "; tanDegrees(112.1); cout << endl; cout << "    The correct solution calculates a tangent of -2.46973";
               }


         .. tab:: Answer

            .. activecode:: functions_a9a
               :language: cpp
               :compileargs: ['-Wall', '-std=c++11']
               :nocodelens:

               Below is one way to complete the program.  You need to make sure to convert your angle to radians before doing any calculations with sinusoidal functions.
               ~~~~
               #include <iostream>
               #include <cmath>
               using namespace std;

               void tanDegrees (double degrees) {
                   double radians = degrees * (2 * 3.14) / 360.0;
                   double tangent = tan(radians);
                   cout << tangent;
               }


   .. tab:: Q10

      .. activecode:: functions_a10
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:

         Write a function called ``volumeSphere`` that takes a ``double`` radius as a parameter, and calculates and prints the volume of a sphere with that radius.  Use 3.14 for ``pi``.  Be sure to include any necessary headers.
         ~~~~
         void volumeSphere () {
       
         }
         
         int main() {
             // DO NOT MODIFY ANYTHING BELOW THIS LINE
             cout << "Testing with radius = 3..." << endl; cout << "    Your solution calculated a volume of "; volumeSphere(3); cout << endl; cout << "    The correct solution calculates a volume of 113.04" << endl; cout << "Testing with radius = 3.24..." << endl; cout << "    Your solution calculated a volume of "; volumeSphere(3.24); cout << endl; cout << "    The correct solution calculates a volume of 142.398";
         }
