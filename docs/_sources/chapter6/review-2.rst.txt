Mixed-Up Code Exercises
-----------------------

Answer the following **Mixed-Up Code** questions to
assess what you have learned in this chapter.

.. tabbed:: self_check

   .. tab:: Q2

      .. parsonsprob:: cond_recc_p2
         :numbered: left
         :adaptive:

         Construct a function that prints whether a number
         is true.
         -----
         void is_true (int number) {
         =====
         bool is_true (int number) { #paired
         =====
          if (number % 2 == 0) {
         =====
           cout << true;
          }
         =====
          else {
         =====
           cout << false;
          }
         =====
         }


   .. tab:: Q3

      .. parsonsprob:: cond_recc_p3
         :numbered: left
         :adaptive:

         Construct a function that prints the difference of a and b if the result
         would result in a positive number.  Otherwise, prints -1.
         -----
         void difference (int a, int b) {
         =====
         int difference (int a, int b) { #paired
         =====
          if (a - b > 0) {
         =====
          if (a - b < 0) { #paired
         =====
           cout << a - b;
          }
         =====
          else {
         =====
           cout << -1;
          }
         =====
         }


   .. tab:: Q4

      .. parsonsprob:: cond_recc_p4
         :numbered: left
         :adaptive:

         Construct a block of code that prints "automatic" if x is
         an odd number, "systematic" if x is greater than y, AND
         "hydromatic" if y is not equal to x.  Check all 3 conditions.
         -----
         if (x % 2 == 1) {
         =====
         if (x % 2 == 0) { #paired
         =====
          cout << "automatic"; }
         =====
         if (x > y) {
         =====
         else if (x > y) { #paired
         =====
          cout << "systematic"; }
         =====
         if (y != x) {
         =====
         else { #paired
         =====
          cout << "hydromatic"; }
         

   .. tab:: Q5

      .. parsonsprob:: cond_recc_p5
         :numbered: left
         :adaptive:

         Construct a block of code that prints "Pick me!" if x is
         equal to y, "Choose me!" if x is less than y, OR "Love me!" 
         if x + y is even.
         -----
         if (x == y) {
         =====
         if (x = y) { #paired
         =====
          cout << "Pick me!"; }
         =====
         else if (y > x) {
         =====
         if (x < y) { #paired
         =====
          cout << "Choose me!"; } 
         =====
         else if ((x + y) % 2 == 0) {
         =====
         else (x + y % 2 == 0) { #paired
         =====
         else if (x + y % 2 == 0) { #paired
         =====
          cout << "Love me!"; } 


   .. tab:: Q6

      .. parsonsprob:: cond_recc_p6
         :numbered: left
         :adaptive:

         Construct a function that prints your letter grade according to this scheme.
         [0, 70) = F, [70, 80) = C, [80, 90) = B, and [90, 100] = A.
         -----
         void printLetterGrade (double grade) {
         =====
          if (grade < 70) {
         =====
           cout << "F"; }
         =====
          else if (grade < 80) {
         =====
          if (grade < 80) { #paired
         =====
           cout << "C"; }
         =====
          else if (grade < 90) {
         =====
          if (grade < 90) { #paired
         =====
           cout << "B"; }
         =====
          else {
         =====
          else if (grade < 100) { #paired
         =====
          if (grade < 100) { #paired
         =====
           cout << "A"; }
         =====
         }


   .. tab:: Q7

      .. parsonsprob:: cond_recc_p7
         :numbered: left
         :adaptive:

         According to a logic game, a knight is someone who cannot tell a lie,
         and a knave is someone who cannot tell the truth.  Construct a function
         that takes two booleans: the truth value of the story, and the truth value
         told by the person.  The function should print whether the person was a
         knight or a knave.
         -----
         void knightKnave (bool truth, bool told) {
         =====
          if (truth == true) {
         =====
           if (told == true) {
            cout << "Knight";
           }
         =====
           else {
            cout << "Knave";
           } }
         =====
          else {
         =====
           if (told == true) {
            cout << "Knave";
           }
         =====
           else {
            cout << "Knive";
           } }
         =====
         }
         

   .. tab:: Q8

      .. parsonsprob:: cond_recc_p8
         :numbered: left
         :adaptive:

         If a cat is in a good mood, it purrs; when it's in a bad mood, it
         meows.  If a doog is in a good mood, it barks; when it's in a bad
         mood it woofs.  Construct a function that accomplishes this.
         -----
         void makeVocals (string animal, string mood) {
         =====
          if (mood == "bad") {
         =====
           if (animal == "dog") {
            cout << "Woof!";
           }
         =====
           else {
            cout << "Meow!";
           }
         =====
          else {
         =====
           if (animal == "dog") {
            cout << "Bark!";
           }
         =====
           else {
            cout << "Purr!";
           }
         =====
         }


   .. tab:: Q9

      .. parsonsprob:: cond_recc_p9
         :numbered: left
         :adaptive:

         Construct a recursive function that tells the user to enter a positive
         number.  It should then output that number to the terminal.  If the user
         enters a negative number or zero, prompt the user again.
         -----
         void takeSum () {
         =====
          cout << "Input a positive number!";
         =====
          int num;
          cin >> num;
         =====
          if (num < 0) {
         =====
           takesum ();
         =====
          } // END "if"
         =====
          cout << num;
         =====
         } // END function


   .. tab:: Q10

      .. parsonsprob:: cond_recc_p10
         :numbered: left
         :adaptive:

         In the table of ASCII characters, the lowercase alphabet consists
         of characters 97-122.  The uppercase alphabet consists of characters
         65-90, which is a 32 character shift back from the lowercase.  Construct
         a recursive function that asks the user to input a LOWERCASE character,
         converts that character to UPPERCASE character and prints it.  If the user
         enters a character outside of the range of the LOWERCASE alphabet, prompt
         the user again.  Hint:  "||" means "or" when used between two conditional
         statements.
         -----
         void capitalize () {
         =====
          cout << "Input a lowercase character!";
         =====
          char let;
          cin >> let;
         =====
          if (int(let) < 97 || int(let) > 122) {
         =====
           capitalize (); }
         =====
          let = let - 32;
         =====
          cout << char(let);
         =====
         }
