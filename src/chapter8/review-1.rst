.. _structures-multiple-choice-exercises:

Multiple Choice Exercises
-------------------------

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: mce_8_1

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

         - [x] ``x``

           + ``x`` is a ``student`` which is a ``struct``. 

         - [x] ``y``

           + ``y`` is a ``student`` which is a ``struct``. 

         - [x] ``z``

           + ``z`` is a ``professor`` which is a ``struct``. 

         - [x] ``college``

           + ``college`` is a ``string`` which is made up of characters.

         - [ ] ``student_pop``

           - An ``int`` is not a compound value.

         - [ ] ``avg_gpa``

           - A ``double`` is not a compound value.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: mce_8_2

         What is wrong with the following ``struct`` definition?

         .. code-block:: cpp

            struct chicken {
              string name;
              int num_legs;
              int eggs;
              bool eggs;
            }

         - [ ] The word "struct" needs to be capitalized.

           - "struct" shouldn't be capitalized in a ``struct`` definition.

         - [x] There needs to be a semicolon after the end curly brace.

           + It is a common error to forgot the semicolon at the end of ``struct`` definitions. 

         - [x] The ``struct`` cannot have two instance variables that are both named ``eggs``.

           + Two symbol names in the same scope is a compile error

         - [ ] There is nothing wrong with the ``struct`` definition.

           - There is an error with the definition. Can you find it?

   .. tb-tab:: Q3

      .. tb-choice::
         :name: mce_8_3

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

         - [ ] ``dog.num_legs = 4;``

           - The ``dog`` object is ``fido``. We can use the dot notation on an object.

         - [ ] ``fido.legs = 4;``

           - Check the name of the instance variable in the ``struct`` definition. 

         - [ ] ``fido[legs] = 4;``

           - We assign values to the instance variables of a ``struct`` using dot notation. 

         - [x] ``fido.num_legs = 4;``

           + Using the member access operator on ``fido``, we can set the value of ``num_legs`` to 4.

   .. tb-tab:: Q4

      .. tb-choice::
         :name: mce_8_4

         What is the output of the code below?

         .. code-block:: cpp

            struct cube {
              int edge_length;
              int volume;
              int mass;
            };

            int main() {
              cube c;
              c.edge_length = 4;
              c.volume = 64;
              c.mass = 128;
              cout << c.edge_length << ", " << c.volume << ", " << c.mass << ", ";
              int density = c.mass / c.volume;
              cout << density;
            }

         - [ ] 4, 2, 64, 128

           - Check the ordering of the output statements.

         - [ ] 4, 64, 128

           - Take a closer look at the output statements. 

         - [x] 4, 64, 128, 2

           + The code outputs all instance variables and the density in the proper order. 

         - [ ] edge_length, volume, mass, density

           - Dot notation accesses the values of the instance variables, not the names.

   .. tb-tab:: Q5

      .. tb-choice::
         :name: mce_8_5

         What is the output of the code below?

         .. code-block:: cpp

            struct cube {
              int edge_length;
              int volume;
              int mass;
            };

            int calculate_density (cube c) {
              return c.mass / c.volume;
            }

            int main() {
              cube c = { 2, 8, 4 };
              int density = calculate_density (c);
              cout << density;
            }

         - [x] 0

           + Because of integer division, ``density`` is 0 and thus the output is 0.

         - [ ] 2

           - Density is mass divided by volume.

         - [ ] 0.5

           - Take a closer look at what kind of division we are doing. 

         - [ ] 1

           - Integer division truncates the extra digits.

   .. tb-tab:: Q6

      .. tb-choice::
         :name: mce_8_6

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

         - [ ] true

           - Take a closer look at the function definition of ``pour_coffee``. 

         - [x] false

           + Since we pass a ``student`` object by value to ``pour_coffee``, the function makes a copy of the object and does not modify the original. If you wanted the original value to change, pass it by reference!

         - [ ] 1

           - The type of coffe_cup_full is ``bool``.

         - [ ] 0

           - The type of coffe_cup_full is ``bool``.

   .. tb-tab:: Q7

      .. tb-choice::
         :name: mce_8_7

         What is the value of ``r.battery_level_percentage`` when the code is done running?

         .. code-block:: cpp

            struct robot {
              string name;
              int battery_level_percentage;
              bool is_fully_charged;
            };

            void charge_robot (robot& r) {
              if (r.battery_level_percentage + 50 > 100) {
                r.battery_level_percentage = 100;
                r.is_fully_charged = true;
              }
              else {
                r.battery_level_percentage = r.battery_level_percentage + 50;
              }
            }

            int main() {
              robot r = { "Rob", 60, false };
              charge_robot (r);
            }

         - [x] 100

           + The ``robot`` object is passed by reference to ``charge_robot``, which caps the ``battery_level_percentage`` at 100.

         - [ ] 110

           - Take a closer look at the ``charge_robot`` function.

         - [ ] 60

           - Is the ``robot`` object passed by value or by reference to ``charge_robot``?

         - [ ] 1

           - That is the final value of ``r.is_fully_charged``. 

   .. tb-tab:: Q8

      .. tb-choice::
         :name: mce_8_8

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

         - [ ] 4, 7

           - Take a closer look at ``func`` and its parameters. Are they passed by value, passed by reference, or both?

         - [x] 4, 10

           + Since ``bar`` doesn't pass either parameter by reference, neither ``bar`` nor ``foo`` affect the values of ``x`` and ``y``.

         - [ ] 7, 7

           - Check the order of the arguments passed into ``func``.

         - [ ] 35, 8

           - Take a closer look at the three functions. Are they all passed by reference?

   .. tb-tab:: Q9

      .. tb-choice::
         :name: mce_8_9

         If the user inputted the string "R2-D2", what is the output of the code below?

         .. code-block:: cpp

            int main() {
              string name;
              cin >> name;
              cout << "Hello, " << name << '!';
            }

         - [ ] R2-D2

           - Take another look at the ``cout`` statement.

         - [ ] Hello name!

           - ``name`` is not in quotes so the value stored in ``name`` will be printed.

         - [x] Hello, R2-D2!

           + "R2-D2" is stored in ``name`` and is then outputted in the ``cout`` statement.

         - [ ] name

           - ``cin`` reads input from the user.

   .. tb-tab:: Q10

      .. tb-choice::
         :name: mce_8_10

         If the user inputted the string "C-3PO", what is the output of the code below?

         .. code-block:: cpp

            int main() {
              char name;
              cin >> name;
              cout << "Hello, " << name << '!';
            }

         - [ ] Hello, CPO!

           - ``cin`` reads the first ``char`` in from user input.

         - [x] Hello, C!

           + Since 'C' is the first ``char`` in the input, this is the correct output. The program will ignore everything that comes after the first ``char``.

         - [ ] Hello, C-3PO!

           - Check the data type of ``name``.

         - [ ] Error, we cannot read a character from user input.

           - We can read characters from user input.


