Mixed-Up Code Exercises
-----------------------

Answer the following **Mixed-Up Code** questions to assess what you have learned in this chapter.

.. tabbed:: tab_check

   .. tab:: Q1

      .. parsonsprob:: VARS_p1
         :numbered: left
         :adaptive:
         :noindent:

         Construct a block of code that prints: "Lions &" one the first line, "Tigers & Bears!" on the second line, and "Oh my!" on the FOURTH line.

         -----
         int main() {
         =====
          cout << "Lions &" << endl;
         =====
          cout << "Lions &"; #paired
         =====
          cout << "Tigers &";
         =====
          cout << "Tigers &" << endl; #paired
         =====
          cout << " Bears!" << endl;
         =====
          cout << "Bears!" << endl; #paired
         =====
          cout << endl;
         =====
          cout << "Oh my!";
         =====
         }


   .. tab:: Q2

      .. parsonsprob:: VARS_p2
         :numbered: left
         :adaptive:
         :noindent:

         Construct a block of code that swaps the value of integers x and y, which have values 3 and 6, respectively.

         -----
         int main() {
         =====
          int x;
          int y;
         =====
          x = 3;
          y = 6;
         =====
          int x = 3 #distractor
          int y = 6
         =====
          int temp = x;
         =====
          x = y;
          y = temp;
         =====
          x = y; #distractor
          y = x;
         =====
         }


   .. tab:: Q3

      .. parsonsprob:: VARS_p3
         :numbered: left
         :adaptive:
         :noindent:

         Dan Humphrey is a 3.98 student at Constance High School.  His crush's first initial is S.  Construct a program that assigns the variables name, GPA, and crush, in that order.

         -----
         int main() {
         =====
          string name = "Dan Humphrey";
         =====
          string name;  #paired
          name = Dan Humphrey;
         =====
          double GPA;
          GPA = 3.98;
         =====
          int GPA = 3.98; #paired
         =====
          char crush = 'S';
         =====
          char crush = "S"; #paired
         =====
         }


   .. tab:: Q4

      .. parsonsprob:: VARS_p4
         :numbered: left
         :adaptive:

         You decide to make homemade Mac 'n' Cheese for you and your roomates.  Whoever wrote the recipe wanted to make things hard for you by stating that it calls for 1% of a gallon of milk.  Construct a block of code that converts this to tablespoons.

         -----
         int main() {
         =====
          double gallons = 0.01;
         =====
          double gallons = 0.01 #paired
         =====
          double cups = 16 * gallons;
         =====
          double cups; #paired
          16 * gallons = cups;
         =====
          double tbsp;
          tbsp = 16 * cups;
         =====
          double tbsp = 16 * cups #paired
         =====
         }


   .. tab:: Q5

      .. parsonsprob:: VARS_p5
         :numbered: left
         :adaptive:

         Construct a block of code that takes the volume of the rectangular prism defined by length, width, and height and prints the result to the terminal.

         -----
         int main() {
         =====
          int length = 2;
          int width = 3;
          int height = 4;
         =====
          length = 2; #paired
          width = 3;
          height = 4;
         =====
          int volume;
         =====
          volume = height * width * length;
         =====
          int volume = length * width * height #distractor
         =====
          cout << volume;
         =====
          print (volume) #distractor
         =====
         }


   .. tab:: Q6

      .. parsonsprob:: VARS_p6
         :numbered: left
         :adaptive:

         Construct a block of code that changes the value of the variable a from the character 'a' to the character 'z'.

         -----
         int main() {
         =====
          char a = 'a';
         =====
          char a = "a"; #paired
         =====
          a = a + 25;
         =====
          a = a + 26; #paired
         =====
          a = a + 27; #paired
         =====
         }


   .. tab:: Q7

      .. parsonsprob:: VARS_p7
         :numbered: left
         :adaptive:

         Construct a block of code that outputs the volume of a cylinder with a radius of 3 and a height of 4.  There are many ways to do this using the choices below, but only the correct answer that uses the LEAST lines of code will be accepted.

         -----
         int main() {
         =====
          cout << 3.14 * 3 * 3 * 4;
         =====
          cout << 3.14 * 3 ^ 2 * 4; #distractor
         =====
          height = 4; #distractor
         =====
          base = 3.14 * 3 * 3; #distractor
         =====
          base = 3.14 * 3 ^ 2; #distractor
         =====
          cout << base * height; #distractor
         =====
          volume = base * height; #distractor
         =====
          cout << volume; #distractor
         =====
         }

   .. tab:: Q8

      .. parsonsprob:: VARS_p8
         :numbered: left
         :adaptive:

         Construct a block of code that prints "My favorite class is MATH" on the same line.

         -----
         int main() {
         =====
          string favorite = "MATH";
         =====
          string favorite = 'MATH'; #paired
         =====
          cout << "My favorite class is ";
          cout << favorite;
         =====
          cout << "My favorite class is " << endl; #paired
          cout << favorite;
         =====
          cout << "My favorite class is" << favorite; #paired
         =====
         }

   .. tab:: Q9

      .. parsonsprob:: VARS_p9
         :numbered: left
         :adaptive:

         It's Black Friday and the Nintendo Switch you've been saving up for
         is marked down to 60% of its original price!
         Construct a block of code that calculates how much money you'd
         be saving if the system originally cost $359.99?

         -----
         int main() {
         =====
          double game = 359.99;
         =====
          double game = $359.99; #paired
         =====
          double discount = game * 0.60;
         =====
          double discount = game - (0.60 * game); #paired
         =====
          double saved = game - discount;
         =====
          double saved = discount; #paired
         =====
          double saved = game + discount; #paired
         =====
         }


   .. tab:: Q10

      .. parsonsprob:: VARS_p10
         :numbered: left
         :adaptive:

         Your family just bought a dog and everyone has been 
         fighting over what to name it.
         It went from Champ to Copper to Higgins,
         and after a few days of being Higgins, everyone agreed on Buddy.
         Construct a block of code that illustrates this concept.

         -----
         int main() {
         =====
          string name = "Champ";
         =====
          string name = 'Champ'; #paired
         =====
          name = "Copper";
         =====
          string name = "Copper"; #paired
         =====
          string new_name = "Higgins";
          name = new_name;
         =====
          string name = "Higgins"; #paired
         =====
          name = "Buddy";
         =====
          name = "Buddy" #paired
         =====
         }

   .. tab:: Q11

      .. parsonsprob:: VARS_p11
         :numbered: left
         :adaptive:

         Construct a block of code that prints the remainder of 18 when
         divided by 13.
         -----
         int main () {
         =====
          int x = 18;
          int y = 13; 
         =====
          cout << x % y;
         =====
          cout << y % x; #paired
         =====
          cout << y / x; #paired
         =====
         }
