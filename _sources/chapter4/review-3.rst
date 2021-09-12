Activecode Exercises
--------------------

Answer the following **Activecode** questions to
assess what you have learned in this chapter.

.. tabbed:: self_check

   .. tab:: Q1

      .. tabbed:: cond_rec_a1

         .. tab:: Question

            .. activecode:: cond_rec_a1q
               :language: cpp

               Fix the code below so that it prints "THE TEAM" "THE TEAM" 
               "THE TEAM" on three separate lines.
               ~~~~
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

         .. tab:: Answer

            .. activecode:: cond_rec_a1_a
               :language: cpp

               Below is one way to fix the program.  Since we want "THE TEAM"
               to print three times, we must check all three conditons.  this
               means changing the ``else if`` statements to ``if`` statements.
               ~~~~
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


   .. tab:: Q2

      .. activecode:: cond_rec_a2
          :language: cpp

          You are part of a class where everyone passes, but it's very hard
          to pass with an A.  Fix the function so it prints your letter grade 
          according to this scheme.  [0, 50) = C, [50, 85) = B, and [85, 100] = A.
          ~~~~
          #include <iostream>
          #include <string>

          std::string whichDoor (double grade) {
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


   .. tab:: Q3

      .. tabbed:: cond_rec_a3

         .. tab:: Question

            .. activecode:: cond_rec_a3q
               :language: cpp

               Fix the infinite recursion in the code below.  The function
               should not count any numbers after 10 (the highest numbers
               that should print are 9 or 10).  When it is done counting,
               the function should print that.
               ~~~~
               #include <iostream>
               using std::cout;

               void countBy2 (int num) {
                   if (num != 10) {
                       cout << num;
                       countBy2 (num + 2);
                   }
                   else {    
                       cout << num 
                            << "\nDone counting!";
                   }
               }

               int main () {
                   countBy2(6);
               }

         .. tab:: Answer

            .. activecode:: cond_rec_a3_a
               :language: cpp

               Below is one way to fix the program.  The infinite recursion
               happens when we use an odd number as an argument.  By checking
               that a number is less than 99, the highest numbers to recurse
               are 98 and 97.  ``98 + 2 == 100`` and ``97 + 2 == 99``, so we
               never count past 100.
               ~~~~
               #include <iostream>
               using std::cout;

               void countBy2 (int num) {
                   if (num < 9) {
                       cout << num;
                       countBy2 (num + 2);
                   }
                   else {    
                       cout << num 
                            << "\nDone counting!";
                   }
               }

               int main () {
                   countBy2(6);
               }


   .. tab:: Q4

      In the following question,
      ``std::boolalpha``  is an I/O manipulator that
      replaces 'falsy' values witht he word false and 'truthy'
      expressions witht he word true.

      .. activecode:: cond_rec_4
          :language: cpp

          Finish the code below so that it prints true if ``x`` is even
          and false if ``x`` is odd.
          ~~~~
          #include <iostream>

          void is_even (int num) {
              if (num % 2 == 0) {
                  std::cout << std::boolalpha << true;
              }
          }


   .. tab:: Q5

      .. tabbed:: cond_rec_a5

         .. tab:: Question

            .. activecode:: cond_rec_a5q
               :language: cpp

               Finish the code below so that the function will continue to
               ask for input until the user guesses the word correctly.
               ~~~~
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


         .. tab:: Answer

            .. activecode:: cond_rec_a5a
               :language: cpp

               Below is one way to complete the program.
               ~~~~
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


   .. tab:: Q6

      .. activecode:: cond_rec_a6
          :language: cpp

          Write the function ``greater`` that prints true
          if the first ``double`` argument is greater than the 
          second ``double`` argument.  Be sure to include any
          necessary headers.
          ~~~~
          void greater () {
              
          }

   .. tab:: Q7

      .. tabbed:: cond_rec_a7

         .. tab:: Question

            .. activecode:: cond_rec_a7q
               :language: cpp

               Write the function ``good_vibes`` that prints "I'm having a ``mood`` day!"
               depending on the value of ``mood``.  If ``mood`` is "bad", then the function
               should not do anything since it's good vibes only.  Be sure to
               include any necessary headers.
               ~~~~
               void good_vibes (string mood) {
              
               }

         .. tab:: Answer

            .. activecode:: cond_rec_a7a
               :language: cpp

               Below is one way to write the program.  The return allows the
               function to exit if there are bad vibes in the room.  Otherise,
               the function prints as directed.
               ~~~~
               void good_vibes (string mood) {
                   if (mood == "bad") {
                       return;
                   }
                   cout << "I'm having a " << mood << " day";
               }


   .. tab:: Q8

      .. activecode:: cond_rec_8
          :language: cpp

          Write the function ``exclusive_or`` that prints true If
          either ``a`` OR ``b`` is true, and prints false otherwise.
          Be sure to include any necessary headers.
          ~~~~
          void exclusive_or (bool a, bool b) {

          }


   .. tab:: Q9

      .. tabbed:: cond_rec_a9

         .. tab:: Question

            .. activecode:: cond_rec_a9q
               :language: cpp

               Write the function ``countdown`` that takes a positive integer
               and decrements it until eaching zero, printing the number at each 
               step of the way.  Once it reaches zero, it should print "Blastoff!"
               ~~~~
               void countdown (int num) {
              
               }

         .. tab:: Answer

            .. activecode:: cond_rec_a9a
               :language: cpp

               Below is one way to write the program.
               ~~~~
               void countdown (int num) {
                   if (num != 0){
                       cout << num << endl;
                       num -= 1;
                       countdown (num);
                   }
                   else {
                       cout << "Blastoff!";
                   }
               }


   .. tab:: Q10

      .. activecode:: cond_rec_a10
          :language: cpp

          Write the function ``print_negative`` that asks the user
          for a negative number.  If the user does not provide a negative
          number, it should contine asking until the user provides one.
          It should then print the negative number.
          ~~~~
          void print_negative () {
              
          }

