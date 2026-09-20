Activecode Exercises
--------------------

Answer the following **Activecode** questions to
assess what you have learned in this chapter.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-group::
         :name: cond_rec_a1

         .. tb-tab:: Question

            Fix the code below so that it prints "THE TEAM" "THE TEAM" 
            "THE TEAM" on three separate lines.

            .. tb-code:: cpp
               :name: cond_rec_a1q
               :caption: Example cond_rec_a1q
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>

               x = 8;
               y = 8;

               if (x % 2 == 0) {
                   std::cout << "THE TEAM";
               } else if (x >= y) {
                   std::cout << "THE TEAM";
               } else if (y >= x) {
                   std::cout << "THE TEAM";
               }

         .. tb-tab:: Answer

            Below is one way to fix the program.  Since we want "THE TEAM"
            to print three times, we must check all three conditons.  this
            means changing the ``else if`` statements to ``if`` statements.

            .. tb-code:: cpp
               :name: cond_rec_a1_a
               :caption: Example cond_rec_a1_a
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>

               x = 8;
               y = 8;

               if (x % 2 == 0) {
                   std::cout << "THE TEAM\n";
               }
               if (x >= y) {
                   std::cout << "THE TEAM\n";
               }
               if (y >= x) {
                   std::cout << "THE TEAM\n";
               }


   .. tb-tab:: Q2

      You are part of a class where everyone passes, but it's very hard
      to pass with an A.  Fix the function so it prints your letter grade 
      according to this scheme.  [0, 50) = C, [50, 85) = B, and [85, 100] = A.

      .. tb-code:: cpp
         :name: cond_rec_a2
         :caption: Example cond_rec_a2
         :compileargs: ['-Wall', '-std=c++11']

         #include <iostream>
         #include <string>

         std::string which_door (double grade) {
             s = "";
             if (grade < 50) {
                 s = "C";
             }
             if (grade < 85) {
                 s = "B";
             }
             if (grade >= 85) {
                 s = "A";
             }
             std::cout << s;
         }


   .. tb-tab:: Q3

      .. tb-group::
         :name: cond_rec_a3

         .. tb-tab:: Question

            Fix the infinite recursion in the code below.  The function
            should not count any numbers after 10 (the highest numbers
            that should print are 9 or 10).  When it is done counting,
            the function should print that.

            .. tb-code:: cpp
               :name: cond_rec_a3q
               :caption: Example cond_rec_a3q
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>
               using std::cout;

               void count_by_2 (int num) {
                   if (num != 10) {
                       cout << num;
                       count_by_2 (num + 2);
                   }
                   else {    
                       cout << num 
                            << "\n_done counting!";
                   }
               }

               int main () {
                   count_by_2(6);
               }

         .. tb-tab:: Answer

            Below is one way to fix the program.  The infinite recursion
            happens when we use an odd number as an argument.  By checking
            that a number is less than 99, the highest numbers to recurse
            are 98 and 97.  ``98 + 2 == 100`` and ``97 + 2 == 99``, so we
            never count past 100.

            .. tb-code:: cpp
               :name: cond_rec_a3_a
               :caption: Example cond_rec_a3_a
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>
               using std::cout;

               void count_by_2 (int num) {
                   if (num < 9) {
                       cout << num;
                       count_by_2 (num + 2);
                   }
                   else {    
                       cout << num 
                            << "\n_done counting!";
                   }
               }

               int main () {
                   count_by_2(6);
               }


   .. tb-tab:: Q4

      In the following question,
      ``std::boolalpha``  is an I/O manipulator that
      replaces 'falsy' values witht he word false and 'truthy'
      expressions witht he word true.

      Finish the code below so that it prints true if ``x`` is even
      and false if ``x`` is odd.

      .. tb-code:: cpp
         :name: cond_rec_4
         :caption: Example cond_rec_4
         :compileargs: ['-Wall', '-std=c++11']

         #include <iostream>

         void is_even (int num) {
             if (num % 2 == 0) {
                 std::cout << std::boolalpha << true;
             }
         }


   .. tb-tab:: Q5

      .. tb-group::
         :name: cond_rec_a5

         .. tb-tab:: Question

            Finish the code below so that the function will continue to
            ask for input until the user guesses the word correctly.

            .. tb-code:: cpp
               :name: cond_rec_a5q
               :caption: Example cond_rec_a5q
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>
               #include <string>
               using namespace std;

               bool guess_word (string correct) {
                   cout << "Guess the word!";
                   string guess;
                   cin >> guess;
                   if (guess == correct) {
                       cout << "That's it!";
                   }
               }


         .. tb-tab:: Answer

            Below is one way to complete the program.

            .. tb-code:: cpp
               :name: cond_rec_a5a
               :caption: Example cond_rec_a5a
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>
               #include <string>
               using namespace std;

               bool guess_word (string correct) {
                   cout << "Guess the word!";
                   string guess;
                   cin >> guess;
                   if (guess == correct) {
                       cout << "That's it!";
                   }
                   else {
                       guess_word(correct);
                   }
               }


   .. tb-tab:: Q6

      Write the function ``greater`` that prints true
      if the first ``double`` argument is greater than the 
      second ``double`` argument.  Be sure to include any
      necessary headers.

      .. tb-code:: cpp
         :name: cond_rec_a6
         :caption: Example cond_rec_a6
         :compileargs: ['-Wall', '-std=c++11']

         void greater () {

         }

   .. tb-tab:: Q7

      .. tb-group::
         :name: cond_rec_a7

         .. tb-tab:: Question

            Write the function ``good_vibes`` that prints "I'm having a ``mood`` day!"
            depending on the value of ``mood``.  If ``mood`` is "bad", then the function
            should not do anything since it's good vibes only.  Be sure to
            include any necessary headers.

            .. tb-code:: cpp
               :name: cond_rec_a7q
               :caption: Example cond_rec_a7q
               :compileargs: ['-Wall', '-std=c++11']

               void good_vibes (string mood) {

               }

         .. tb-tab:: Answer

            Below is one way to write the program.  The return allows the
            function to exit if there are bad vibes in the room.  Otherise,
            the function prints as directed.

            .. tb-code:: cpp
               :name: cond_rec_a7a
               :caption: Example cond_rec_a7a
               :compileargs: ['-Wall', '-std=c++11']

               void good_vibes (string mood) {
                   if (mood == "bad") {
                       return;
                   }
                   cout << "I'm having a " << mood << " day";
               }


   .. tb-tab:: Q8

      Write the function ``exclusive_or`` that prints true If
      either ``a`` OR ``b`` is true, and prints false otherwise.
      Be sure to include any necessary headers.

      .. tb-code:: cpp
         :name: cond_rec_8
         :caption: Example cond_rec_8
         :compileargs: ['-Wall', '-std=c++11']

         void exclusive_or (bool a, bool b) {

         }


   .. tb-tab:: Q9

      .. tb-group::
         :name: cond_rec_a9

         .. tb-tab:: Question

            Write the function ``countdown`` that takes a positive integer
            and decrements it until eaching zero, printing the number at each 
            step of the way.  Once it reaches zero, it should print "Blastoff!"

            .. tb-code:: cpp
               :name: cond_rec_a9q
               :caption: Example cond_rec_a9q
               :compileargs: ['-Wall', '-std=c++11']

               void countdown (int num) {

               }

         .. tb-tab:: Answer

            Below is one way to write the program.

            .. tb-code:: cpp
               :name: cond_rec_a9a
               :caption: Example cond_rec_a9a
               :compileargs: ['-Wall', '-std=c++11']

               void countdown (int num) {
                   if (num != 0){
                       cout << num << '\n';
                       num -= 1;
                       countdown (num);
                   }
                   else {
                       cout << "Blastoff!";
                   }
               }


   .. tb-tab:: Q10

      Write the function ``print_negative`` that asks the user
      for a negative number.  If the user does not provide a negative
      number, it should contine asking until the user provides one.
      It should then print the negative number.

      .. tb-code:: cpp
         :name: cond_rec_a10
         :caption: Example cond_rec_a10
         :compileargs: ['-Wall', '-std=c++11']

         void print_negative () {

         }

