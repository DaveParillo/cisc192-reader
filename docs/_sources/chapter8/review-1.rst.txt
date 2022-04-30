Multiple Choice Exercises
-------------------------

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: mce_8_1
          :practice: T

          Which of the following are compound values?

          .. code-block:: cpp
 
             struct student {
               string first_name, last_name;
               int year;
               double gpa;
             };
 
             struct professor {
               string first_name, last_name;
               string department;
               int class;
             };
 
             int main() {
               student x = { "John", "Doe", 2, 3.46 };
               student y = { "Jane", "Doe", 3, 3.68 };
               professor z = { "Richard", "Roe", "Computer Science", 101 };
               string college = "University of College";
               int student_pop = 3400;
               double avg_gpa = 3.2;
             }
              
          - ``x``

            + ``x`` is a ``student`` which is a ``struct``. 

          - ``y``

            + ``y`` is a ``student`` which is a ``struct``. 

          - ``z``

            + ``z`` is a ``professor`` which is a ``struct``. 

          - ``college``

            + ``college`` is a ``string`` which is made up of characters.

          - ``student_pop``

            - An ``int`` is not a compound value.

          - ``avg_gpa``

            - A ``double`` is not a compound value.

   .. tab:: Q2

      .. mchoice:: mce_8_2
          :practice: T

          What is wrong with the following ``struct`` definition?

          .. code-block:: cpp

             struct chicken {
               string name;
               int num_legs;
               int eggs;
               bool eggs;
             }

          - The word "struct" needs to be capitalized.

            - "struct" shouldn't be capitalized in a ``struct`` definition.

          - There needs to be a semicolon after the end curly brace.

            + It is a common error to forgot the semicolon at the end of ``struct`` definitions. 

          - The ``struct`` cannot have two instance variables that are both named ``eggs``.

            + Two symbol names in the same scope is a compile error

          - There is nothing wrong with the ``struct`` definition.

            - There is an error with the definition. Can you find it?

   .. tab:: Q3

      .. mchoice:: mce_8_3
          :practice: T

          How do we assign the value of 4 to the instance variable ``num_legs`` of the ``dog`` object?

          .. code-block:: cpp

             struct dog {
               string name;
               int num_legs;
               bool is_panting;
             };

            int main() {
              dog fido = { "Fido", 0, true };
            }

          - ``dog.num_legs = 4;``

            - The ``dog`` object is ``fido``. We can use the dot notation on an object.

          - ``fido.legs = 4;``

            - Check the name of the instance variable in the ``struct`` definition. 

          - ``fido[legs] = 4;``

            - We assign values to the instance variables of a ``struct`` using dot notation. 

          - ``fido.num_legs = 4;``

            + Using the member access operator on ``fido``, we can set the value of ``num_legs`` to 4.

   .. tab:: Q4

      .. mchoice:: mce_8_4
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

             struct Cube {
               int edgeLength;
               int volume;
               int mass;
             };
 
             int main() {
               Cube c;
               c.edgeLength = 4;
               c.volume = 64;
               c.mass = 128;
               cout << c.edgeLength << ", " << c.volume << ", " << c.mass << ", ";
               int density = c.mass / c.volume;
               cout << density;
             }

          - 4, 2, 64, 128

            - Check the ordering of the output statements.

          - 4, 64, 128

            - Take a closer look at the output statements. 

          - 4, 64, 128, 2

            + The code outputs all instance variables and the density in the proper order. 

          - edgeLength, volume, mass, density

            - Dot notation accesses the values of the instance variables, not the names.

   .. tab:: Q5

      .. mchoice:: mce_8_5
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

             struct Cube {
               int edgeLength;
               int volume;
               int mass;
             };
 
             int calculateDensity (Cube c) {
               return c.mass / c.volume;
             }
 
             int main() {
               Cube c = { 2, 8, 4 };
               int density = calculateDensity (c);
               cout << density;
             }

          - 0

            + Because of integer division, ``density`` is 0 and thus the output is 0.

          - 2

            - Density is mass divided by volume.

          - 0.5

            - Take a closer look at what kind of division we are doing. 

          - 1

            - Integer division truncates the extra digits.

   .. tab:: Q6

      .. mchoice:: mce_8_6
          :practice: T

          What is the value of ``s.coffee_cup_full`` when the code is done running?

          .. code-block:: cpp

             struct student {
               string name;
               bool is_sleepy;
               bool coffee_cup_full;
             };
 
             void pour_coffee (student s) {
               s.coffee_cup_full = true;
             }
 
             int main() {
               student s = { "Thor Odinson", true, false };
               if (s.is_sleepy) {
                 pour_coffee (s);
               }
             }

          - true

            - Take a closer look at the function definition of ``pour_coffee``. 

          - false

            + Since we pass a ``student`` object by value to ``pour_coffee``, the function makes a copy of the object and does not modify the original. If you wanted the original value to change, pass it by reference!

          - 1

            - The type of coffe_cup_full is ``bool``.

          - 0

            - The type of coffe_cup_full is ``bool``.

   .. tab:: Q7

      .. mchoice:: mce_8_7
          :practice: T

          What is the value of ``r.batteryLevelPercentage`` when the code is done running?

          .. code-block:: cpp

             struct Robot {
               string name;
               int batteryLevelPercentage;
               bool isFullyCharged;
             };
 
             void chargeRobot (Robot& r) {
               if (r.batteryLevelPercentage + 50 > 100) {
                 r.batteryLevelPercentage = 100;
                 r.isFullyCharged = true;
               }
               else {
                 r.batteryLevelPercentage = r.batteryLevelPercentage + 50;
               }
             }
 
             int main() {
               Robot r = { "Rob", 60, false };
               chargeRobot (r);
             }

          - 100

            + The ``Robot`` object is passed by reference to ``chargeRobot``, which caps the ``batteryLevelPercentage`` at 100.

          - 110

            - Take a closer look at the ``chargeRobot`` function.

          - 60

            - Is the ``Robot`` object passed by value or by reference to ``chargeRobot``?

          - 1

            - That is the final value of ``r.isFullyCharged``. 

   .. tab:: Q8

      .. mchoice:: mce_8_8
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

             void foo (int& x, int y) {
               x = x + 4;
               y = 2 * x + 3 * y;
             }
 
             void bar (int x, int y) {
               y = 2 * x;
               x = x - 1;
               foo (x, x);
             }
 
             void func (int &x, int& y) {
               x = x + 3;
               bar (y, x);
             }
 
             int main() {
               int x = 4;
               int y = 7;
               func (y, x);
               cout << x << ", " << y;
             }

          - 4, 7

            - Take a closer look at ``func`` and its parameters. Are they passed by value, passed by reference, or both?

          - 4, 10

            + Since ``bar`` doesn't pass either parameter by reference, neither ``bar`` nor ``foo`` affect the values of ``x`` and ``y``.

          - 7, 7

            - Check the order of the arguments passed into ``func``.

          - 35, 8

            - Take a closer look at the three functions. Are they all passed by reference?

   .. tab:: Q9

      .. mchoice:: mce_8_9
          :practice: T

          If the user inputted the string "R2-D2", what is the output of the code below?

          .. code-block:: cpp

             int main() {
               string name;
               cin >> name;
               cout << "Hello, " << name << "!";
             }

          - R2-D2

            - Take another look at the ``cout`` statement.

          - Hello name!

            - ``name`` is not in quotes so the value stored in ``name`` will be printed.

          - Hello, R2-D2!

            + "R2-D2" is stored in ``name`` and is then outputted in the ``cout`` statement.

          - name

            - ``cin`` reads input from the user.

   .. tab:: Q10

      .. mchoice:: mce_8_10
          :practice: T

          If the user inputted the string "C-3PO", what is the output of the code below?

          .. code-block:: cpp

             int main() {
               char name;
               cin >> name;
               cout << "Hello, " << name << "!";
             }

          - Hello, CPO!

            - ``cin`` reads the first ``char`` in from user input.

          - Hello, C!

            + Since 'C' is the first ``char`` in the input, this is the correct output. The program will ignore everything that comes after the first ``char``.

          - Hello, C-3PO!

            - Check the data type of ``name``.

          - Error, we cannot read a character from user input.

            - We can read characters from user input.


