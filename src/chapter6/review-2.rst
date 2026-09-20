Mixed-Up Code Exercises
-----------------------

Answer the following **Mixed-Up Code** questions to
assess what you have learned in this chapter.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: cond_recc_p2

         Construct a function that prints whether a number
         is true.

         .. code-block:: cpp

            {{group}}
            void is_true (int number) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            bool is_true (int number) {
            {{endgroup}}
            {{group}}
             if (number % 2 == 0) {
            {{endgroup}}
            {{group}}
              cout << true;
             }
            {{endgroup}}
            {{group}}
             else {
            {{endgroup}}
            {{group}}
              cout << false;
             }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: cond_recc_p3

         Construct a function that prints the difference of a and b if the result
         would result in a positive number.  Otherwise, prints -1.

         .. code-block:: cpp

            {{group}}
            void difference (int a, int b) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            int difference (int a, int b) {
            {{endgroup}}
            {{group}}
             if (a - b > 0) {
            {{endgroup}}
            {{distractor}}
            {{group}}
             if (a - b < 0) {
            {{endgroup}}
            {{group}}
              cout << a - b;
             }
            {{endgroup}}
            {{group}}
             else {
            {{endgroup}}
            {{group}}
              cout << -1;
             }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q4

      .. tb-parsons::
         :name: cond_recc_p4

         Construct a block of code that prints "automatic" if x is
         an odd number, "systematic" if x is greater than y, AND
         "hydromatic" if y is not equal to x.  Check all 3 conditions.

         .. code-block:: cpp

            {{group}}
            if (x % 2 == 1) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            if (x % 2 == 0) {
            {{endgroup}}
            {{group}}
             cout << "automatic"; }
            {{endgroup}}
            {{group}}
            if (x > y) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            else if (x > y) {
            {{endgroup}}
            {{group}}
             cout << "systematic"; }
            {{endgroup}}
            {{group}}
            if (y != x) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            else {
            {{endgroup}}
            {{group}}
             cout << "hydromatic"; }
            {{endgroup}}

   .. tb-tab:: Q5

      .. tb-parsons::
         :name: cond_recc_p5

         Construct a block of code that prints "Pick me!" if x is
         equal to y, "Choose me!" if x is less than y, OR "Love me!" 
         if x + y is even.

         .. code-block:: cpp

            {{group}}
            if (x == y) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            if (x = y) {
            {{endgroup}}
            {{group}}
             cout << "Pick me!"; }
            {{endgroup}}
            {{group}}
            else if (y > x) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            if (x < y) {
            {{endgroup}}
            {{group}}
             cout << "Choose me!"; }
            {{endgroup}}
            {{group}}
            else if ((x + y) % 2 == 0) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            else (x + y % 2 == 0) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            else if (x + y % 2 == 0) {
            {{endgroup}}
            {{group}}
             cout << "Love me!"; }
            {{endgroup}}

   .. tb-tab:: Q6

      .. tb-parsons::
         :name: cond_recc_p6

         Construct a function that prints your letter grade according to this scheme.
         [0, 70) = F, [70, 80) = C, [80, 90) = B, and [90, 100] = A.

         .. code-block:: cpp

            {{group}}
            void print_letter_grade (double grade) {
            {{endgroup}}
            {{group}}
             if (grade < 70) {
            {{endgroup}}
            {{group}}
              cout << 'F'; }
            {{endgroup}}
            {{group}}
             else if (grade < 80) {
            {{endgroup}}
            {{distractor}}
            {{group}}
             if (grade < 80) {
            {{endgroup}}
            {{group}}
              cout << 'C'; }
            {{endgroup}}
            {{group}}
             else if (grade < 90) {
            {{endgroup}}
            {{distractor}}
            {{group}}
             if (grade < 90) {
            {{endgroup}}
            {{group}}
              cout << 'B'; }
            {{endgroup}}
            {{group}}
             else {
            {{endgroup}}
            {{distractor}}
            {{group}}
             else if (grade < 100) {
            {{endgroup}}
            {{distractor}}
            {{group}}
             if (grade < 100) {
            {{endgroup}}
            {{group}}
              cout << 'A'; }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q7

      .. tb-parsons::
         :name: cond_recc_p7

         According to a logic game, a knight is someone who cannot tell a lie,
         and a knave is someone who cannot tell the truth.  Construct a function
         that takes two booleans: the truth value of the story, and the truth value
         told by the person.  The function should print whether the person was a
         knight or a knave.

         .. code-block:: cpp

            {{group}}
            void knight_knave (bool truth, bool told) {
            {{endgroup}}
            {{group}}
             if (truth == true) {
            {{endgroup}}
            {{group}}
              if (told == true) {
               cout << "Knight";
              }
            {{endgroup}}
            {{group}}
              else {
               cout << "Knave";
              } }
            {{endgroup}}
            {{group}}
             else {
            {{endgroup}}
            {{group}}
              if (told == true) {
               cout << "Knave";
              }
            {{endgroup}}
            {{group}}
              else {
               cout << "Knive";
              } }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q8

      .. tb-parsons::
         :name: cond_recc_p8

         If a cat is in a good mood, it purrs; when it's in a bad mood, it
         meows.  If a doog is in a good mood, it barks; when it's in a bad
         mood it woofs.  Construct a function that accomplishes this.

         .. code-block:: cpp

            {{group}}
            void make_vocals (string animal, string mood) {
            {{endgroup}}
            {{group}}
             if (mood == "bad") {
            {{endgroup}}
            {{group}}
              if (animal == "dog") {
               cout << "Woof!";
              }
            {{endgroup}}
            {{group}}
              else {
               cout << "Meow!";
              }
            {{endgroup}}
            {{group}}
             else {
            {{endgroup}}
            {{group}}
              if (animal == "dog") {
               cout << "Bark!";
              }
            {{endgroup}}
            {{group}}
              else {
               cout << "Purr!";
              }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q9

      .. tb-parsons::
         :name: cond_recc_p9

         Construct a recursive function that tells the user to enter a positive
         number.  It should then output that number to the terminal.  If the user
         enters a negative number or zero, prompt the user again.

         .. code-block:: cpp

            {{group}}
            void take_sum () {
            {{endgroup}}
            {{group}}
             cout << "Input a positive number!";
            {{endgroup}}
            {{group}}
             int num;
             cin >> num;
            {{endgroup}}
            {{group}}
             if (num < 0) {
            {{endgroup}}
            {{group}}
              takesum ();
            {{endgroup}}
            {{group}}
             } // END "if"
            {{endgroup}}
            {{group}}
             cout << num;
            {{endgroup}}
            {{group}}
            } // END function
            {{endgroup}}

   .. tb-tab:: Q10

      .. tb-parsons::
         :name: cond_recc_p10

         In the table of ASCII characters, the lowercase alphabet consists
         of characters 97-122.  The uppercase alphabet consists of characters
         65-90, which is a 32 character shift back from the lowercase.  Construct
         a recursive function that asks the user to input a LOWERCASE character,
         converts that character to UPPERCASE character and prints it.  If the user
         enters a character outside of the range of the LOWERCASE alphabet, prompt
         the user again.  Hint:  "||" means "or" when used between two conditional
         statements.

         .. code-block:: cpp

            {{group}}
            void capitalize () {
            {{endgroup}}
            {{group}}
             cout << "Input a lowercase character!";
            {{endgroup}}
            {{group}}
             char let;
             cin >> let;
            {{endgroup}}
            {{group}}
             if (int(let) < 97 || int(let) > 122) {
            {{endgroup}}
            {{group}}
              capitalize (); }
            {{endgroup}}
            {{group}}
             let = let - 32;
            {{endgroup}}
            {{group}}
             cout << char(let);
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

