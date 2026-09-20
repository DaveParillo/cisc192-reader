Mixed-Up Code Exercises
-----------------------

Answer the following **Mixed-Up Code** questions to assess what you have learned in this chapter.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: VARS_p1
         :no-indent:

         Construct a block of code that prints: "Lions &" one the first line, "Tigers & Bears!" on the second line, and "Oh my!" on the FOURTH line.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
             cout << "Lions &" << '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << "Lions &";
            {{endgroup}}
            {{group}}
             cout << "Tigers &";
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << "Tigers &" << '\n';
            {{endgroup}}
            {{group}}
             cout << " Bears!" << '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << "Bears!" << '\n';
            {{endgroup}}
            {{group}}
             cout << '\n';
            {{endgroup}}
            {{group}}
             cout << "Oh my!";
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: VARS_p2
         :no-indent:

         Construct a block of code that swaps the value of integers x and y, which have values 3 and 6, respectively.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
             int x;
             int y;
            {{endgroup}}
            {{group}}
             x = 3;
             y = 6;
            {{endgroup}}
            {{distractor}}
            {{group}}
             int x = 3 #distractor
             int y = 6
            {{endgroup}}
            {{group}}
             int temp = x;
            {{endgroup}}
            {{group}}
             x = y;
             y = temp;
            {{endgroup}}
            {{distractor}}
            {{group}}
             x = y; #distractor
             y = x;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: VARS_p3
         :no-indent:

         Dan Humphrey is a 3.98 student at Constance High School.  His crush's first initial is S.  Construct a program that assigns the variables name, GPA, and crush, in that order.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
             string name = "Dan Humphrey";
            {{endgroup}}
            {{distractor}}
            {{group}}
             string name;
             name = Dan Humphrey;
            {{endgroup}}
            {{group}}
             double GPA;
             GPA = 3.98;
            {{endgroup}}
            {{distractor}}
            {{group}}
             int GPA = 3.98;
            {{endgroup}}
            {{group}}
             char crush = 'S';
            {{endgroup}}
            {{distractor}}
            {{group}}
             char crush = 'S';
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q4

      .. tb-parsons::
         :name: VARS_p4

         You decide to make homemade Mac 'n' Cheese for you and your roomates.  Whoever wrote the recipe wanted to make things hard for you by stating that it calls for 1% of a gallon of milk.  Construct a block of code that converts this to tablespoons.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
             double gallons = 0.01;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double gallons = 0.01
            {{endgroup}}
            {{group}}
             double cups = 16 * gallons;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double cups;
             16 * gallons = cups;
            {{endgroup}}
            {{group}}
             double tbsp;
             tbsp = 16 * cups;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double tbsp = 16 * cups
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q5

      .. tb-parsons::
         :name: VARS_p5

         Construct a block of code that takes the volume of the rectangular prism defined by length, width, and height and prints the result to the terminal.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
             int length = 2;
             int width = 3;
             int height = 4;
            {{endgroup}}
            {{distractor}}
            {{group}}
             length = 2;
             width = 3;
             height = 4;
            {{endgroup}}
            {{group}}
             int volume;
            {{endgroup}}
            {{group}}
             volume = height * width * length;
            {{endgroup}}
            {{distractor}}
            {{group}}
             int volume = length * width * height #distractor
            {{endgroup}}
            {{group}}
             cout << volume;
            {{endgroup}}
            {{distractor}}
            {{group}}
             print (volume) #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q6

      .. tb-parsons::
         :name: VARS_p6

         Construct a block of code that changes the value of the variable a from the character 'a' to the character 'z'.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
             char a = 'a';
            {{endgroup}}
            {{distractor}}
            {{group}}
             char a = 'a';
            {{endgroup}}
            {{group}}
             a = a + 25;
            {{endgroup}}
            {{distractor}}
            {{group}}
             a = a + 26;
            {{endgroup}}
            {{distractor}}
            {{group}}
             a = a + 27;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q7

      .. tb-parsons::
         :name: VARS_p7

         Construct a block of code that outputs the volume of a cylinder with a radius of 3 and a height of 4.  There are many ways to do this using the choices below, but only the correct answer that uses the LEAST lines of code will be accepted.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
             cout << 3.14 * 3 * 3 * 4;
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << 3.14 * 3 ^ 2 * 4; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             height = 4; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             base = 3.14 * 3 * 3; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             base = 3.14 * 3 ^ 2; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << base * height; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             volume = base * height; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << volume; #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q8

      .. tb-parsons::
         :name: VARS_p8

         Construct a block of code that prints "My favorite class is MATH" on the same line.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
             string favorite = "MATH";
            {{endgroup}}
            {{distractor}}
            {{group}}
             string favorite = 'MATH';
            {{endgroup}}
            {{group}}
             cout << "My favorite class is ";
             cout << favorite;
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << "My favorite class is " << '\n';
             cout << favorite;
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << "My favorite class is" << favorite;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q9

      .. tb-parsons::
         :name: VARS_p9

         It's Black Friday and the Nintendo Switch you've been saving up for
         is marked down to 60% of its original price!
         Construct a block of code that calculates how much money you'd
         be saving if the system originally cost $359.99?

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
             double game = 359.99;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double game = $359.99;
            {{endgroup}}
            {{group}}
             double discount = game * 0.60;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double discount = game - (0.60 * game);
            {{endgroup}}
            {{group}}
             double saved = game - discount;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double saved = discount;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double saved = game + discount;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q10

      .. tb-parsons::
         :name: VARS_p10

         Your family just bought a dog and everyone has been 
         fighting over what to name it.
         It went from Champ to Copper to Higgins,
         and after a few days of being Higgins, everyone agreed on Buddy.
         Construct a block of code that illustrates this concept.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
             string name = "Champ";
            {{endgroup}}
            {{distractor}}
            {{group}}
             string name = 'Champ';
            {{endgroup}}
            {{group}}
             name = "Copper";
            {{endgroup}}
            {{distractor}}
            {{group}}
             string name = "Copper";
            {{endgroup}}
            {{group}}
             string new_name = "Higgins";
             name = new_name;
            {{endgroup}}
            {{distractor}}
            {{group}}
             string name = "Higgins";
            {{endgroup}}
            {{group}}
             name = "Buddy";
            {{endgroup}}
            {{distractor}}
            {{group}}
             name = "Buddy"
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q11

      .. tb-parsons::
         :name: VARS_p11

         Construct a block of code that prints the remainder of 18 when
         divided by 13.

         .. code-block:: cpp

            {{group}}
            int main () {
            {{endgroup}}
            {{group}}
             int x = 18;
             int y = 13;
            {{endgroup}}
            {{group}}
             cout << x % y;
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << y % x;
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << y / x;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

