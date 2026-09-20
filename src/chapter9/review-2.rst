.. _more-structures-mixed-up-code-practice:

Mixed Up Code Practice
----------------------

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: mucp_9_1
         :no-indent:

         Let's write the code for the struct definition of movie. 
         The movie structure will have the instance variables title, 
         director, and release_year in that order. 
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            struct movie {
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct movie {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct movie (  #distractor
            {{endgroup}}
            {{group}}
               string title;
            {{endgroup}}
            {{group}}
               string director;
            {{endgroup}}
            {{group}}
               int release_year;
            {{endgroup}}
            {{distractor}}
            {{group}}
               string release_year;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               char title;  #distractor
            {{endgroup}}
            {{group}}
            };
            {{endgroup}}
            {{distractor}}
            {{group}}
            } #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            ) #distractor
            {{endgroup}}

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: mucp_9_2
         :no-indent:

         Let's write the code for the print_movie function. 
         print_movie should print the information about a movie
         in the following format: "title" directed by director (release_year).
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void print_movie (const movie& m) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void print_movie (&movie m const) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            movie print_movie (movie m) {
            {{endgroup}}
            {{group}}
               cout << '"' << m.title << "\" directed by ";
            {{endgroup}}
            {{group}}
               cout << m.director << " (" << m.release_year << ')' << '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << title << director << release_year;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << '"' << title << "\" directed by ";  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << """ << m.title << "" directed by ";  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << director << " (" << release_year << ')' << '\n';  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: mucp_9_3
         :no-indent:

         Let's write the code for the movie_age function. 
         movie_age should take a movie and current_year as a parameter and
         return how many years it has been since the release_year.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            int movie_age (const movie& m, int current_year) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void movie_age (const movie& m, int current_year) {  #distractor
            {{endgroup}}
            {{group}}
               return current_year - m.release_year;
            {{endgroup}}
            {{distractor}}
            {{group}}
               return current_year - release_year;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               return m.release_year - current_year;  #distractor;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q4

      .. tb-parsons::
         :name: mucp_9_4

         Let's write the code for the struct definition of date. 
         The date structure will have three integer instance variables: day, 
         month, and year in that order. 
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            struct date {
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct date {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct date (  #distractor
            {{endgroup}}
            {{group}}
               int day;
            {{endgroup}}
            {{group}}
               int month;
            {{endgroup}}
            {{group}}
               int year;
            {{endgroup}}
            {{distractor}}
            {{group}}
               string day;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               string month;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               string year;  #distractor
            {{endgroup}}
            {{group}}
            };
            {{endgroup}}
            {{distractor}}
            {{group}}
            } #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            ) #distractor
            {{endgroup}}

   .. tb-tab:: Q5

      .. tb-parsons::
         :name: mucp_9_5

         Let's write the code for the print_date function. 
         print_date should print the date in the following format: 
         month/date/year.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void print_date (const date& d) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void print_date (&date d) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            date print_date (date d) {
            {{endgroup}}
            {{group}}
               cout << d.month << '/' << d.day << '/' << d.year << '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << month << '/' << day << '/' << year << '\n';  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << d.day << '/' << d.month << '/' << d.year << '\n';  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q6

      .. tb-parsons::
         :name: mucp_9_6

         Let's write the code for the next_month function. 
         next_month should change the date to one month later.
         For example, 3/4/2020 gets modified to 4/4/2020, and 12/3/2020
         gets modified to 1/3/2021.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void next_month (date& d) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void next_month (const date d) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            date next_month (date& d) {
            {{endgroup}}
            {{group}}
               if (d.month == 12) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (d.month = 12) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (d.month == 1) {  #distractor
            {{endgroup}}
            {{group}}
                  d.month = 1;
            {{endgroup}}
            {{group}}
                  d.year++;
            {{endgroup}}
            {{group}}
                  d.year = 1;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else {
            {{endgroup}}
            {{group}}
                  d.month++;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q7

      .. tb-parsons::
         :name: mucp_9_7

         Let's write the code for the struct definition of length. 
         length should have the instance variables inches, feet, and yard.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            struct length {
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct length {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct length (  #distractor
            {{endgroup}}
            {{group}}
               double inches;
            {{endgroup}}
            {{group}}
               double feet;
            {{endgroup}}
            {{group}}
               double yards;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int inches;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               string feet;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               int yards;  #distractor
            {{endgroup}}
            {{group}}
            };
            {{endgroup}}
            {{distractor}}
            {{group}}
            } #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            ) #distractor
            {{endgroup}}

   .. tb-tab:: Q8

      .. tb-parsons::
         :name: mucp_9_8

         Let's write the code for the print_length function. 
         print_length should print the date in the following format: 
         yards yds, feet ft, inches in.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void print_length (const length& l) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void print_length (length l) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            string print_length (length l) {
            {{endgroup}}
            {{group}}
               cout << l.yards << " yds, " << l.feet << " feet, " << l.inches << " in" '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << yards << " yds, " << feet << " feet, " << inches << " in" '\n';  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << l.inches << " in, " << l.feet << " feet, " << l.yards << " yds" '\n';  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q9

      .. tb-parsons::
         :name: mucp_9_9

         Let's write the code for the all_inches function. 
         print_length should modify a length object to convert all
         feet and yards to inches. For example, a length with 1 yard, 2 feet, and 3
         inches is converted into a length with 0 yards, 0 feet, and 63 inches.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void all_inches (length& l) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void all_inches (const length l) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            length all_inches (length l const) {
            {{endgroup}}
            {{group}}
               l.inches += 36 * l.yards + 12 * l.feet;
            {{endgroup}}
            {{distractor}}
            {{group}}
               l.inches = 36 * l.yards + 12 * l.feet;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               int feet_to_inches = 12 * l.feet;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               double yard_to_inches = 36 * yards;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q10

      .. tb-parsons::
         :name: mucp_9_10

         Let's write the code for the add_lengths function. 
         add_lengths should take three Lengths as parameters. 
         It should then add the first two Lengths and store the result
         in the third length. If there is over 12 inches or over 3 feet,
         convert it to the proper amound of feet and yards (13 inches becomes 1 foot and 1 inch).
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void add_lengths (const length& first, const length& second, length& total) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void add_lengths (length& first, length& second, const length& total) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void add_lengths (length first, length second, length total) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            length add_lengths (length& first, length& second, length& total) {
            {{endgroup}}
            {{group}}
               total.inches = first.inches + second.inches;
            {{endgroup}}
            {{group}}
               total.feet = first.feet + second.feet;
            {{endgroup}}
            {{group}}
               total.yards = first.yards + second.yards;
            {{endgroup}}
            {{group}}
               if (total.inches >= 12) {
            {{endgroup}}
            {{group}}
                  int add_feet = total.inches % 12;
            {{endgroup}}
            {{group}}
                  total.feet += add_feet;
            {{endgroup}}
            {{group}}
                  total.inches = total.inches - add_feet * 12;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               if (total.feet >= 3) {
            {{endgroup}}
            {{group}}
                  int add_yards = total.feet % 3;
            {{endgroup}}
            {{group}}
                  total.yards += add_yards;
            {{endgroup}}
            {{group}}
                  total.feet = total.feet - add_yards * 3;
            {{endgroup}}
            {{group}}
               }
            }
            {{endgroup}}

