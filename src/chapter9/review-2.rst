Mixed Up Code Practice
----------------------

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: mucp_9_1
         :no-indent:

         Let's write the code for the struct definition of Movie. 
         The Movie structure will have the instance variables title, 
         director, and releaseYear in that order. 
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            struct Movie {
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct movie {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct Movie (  #distractor
            {{endgroup}}
            {{group}}
               string title;
            {{endgroup}}
            {{group}}
               string director;
            {{endgroup}}
            {{group}}
               int releaseYear;
            {{endgroup}}
            {{distractor}}
            {{group}}
               string releaseYear;  #distractor
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

         Let's write the code for the printMovie function. 
         printMovie should print the information about a movie
         in the following format: "title" directed by director (releaseYear).
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void printMovie (const Movie& m) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void printMovie (&Movie m const) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            Movie printMovie (Movie m) {
            {{endgroup}}
            {{group}}
               cout << "\"" << m.title << "\" directed by ";
            {{endgroup}}
            {{group}}
               cout << m.director << " (" << m.releaseYear << ")" << endl;
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << title << director << releaseYear;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << "\"" << title << "\" directed by ";  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << """ << m.title << "" directed by ";  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << director << " (" << releaseYear << ")" << endl;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: mucp_9_3
         :no-indent:

         Let's write the code for the movieAge function. 
         movieAge should take a Movie and currentYear as a parameter and
         return how many years it has been since the releaseYear.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            int movieAge (const Movie& m, int currentYear) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void movieAge (const Movie& m, int currentYear) {  #distractor
            {{endgroup}}
            {{group}}
               return currentYear - m.releaseYear;
            {{endgroup}}
            {{distractor}}
            {{group}}
               return currentYear - releaseYear;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               return m.releaseYear - currentYear;  #distractor;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q4

      .. tb-parsons::
         :name: mucp_9_4

         Let's write the code for the struct definition of Date. 
         The Date structure will have three integer instance variables: day, 
         month, and year in that order. 
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            struct Date {
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct date {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct Date (  #distractor
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

         Let's write the code for the printDate function. 
         printDate should print the date in the following format: 
         month/date/year.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void printDate (const Date& d) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void printDate (&Date d) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            Date printDate (Date d) {
            {{endgroup}}
            {{group}}
               cout << d.month << "/" << d.day << "/" << d.year << endl;
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << month << "/" << day << "/" << year << endl;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << d.day << "/" << d.month << "/" << d.year << endl;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q6

      .. tb-parsons::
         :name: mucp_9_6

         Let's write the code for the nextMonth function. 
         nextMonth should change the date to one month later.
         For example, 3/4/2020 gets modified to 4/4/2020, and 12/3/2020
         gets modified to 1/3/2021.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void nextMonth (Date& d) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void nextMonth (const Date d) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            Date nextMonth (Date& d) {
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

         Let's write the code for the struct definition of Length. 
         Length should have the instance variables inches, feet, and yard.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            struct Length {
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct length {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct Length (  #distractor
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

         Let's write the code for the printLength function. 
         printLength should print the date in the following format: 
         yards yds, feet ft, inches in.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void printLength (const Length& l) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void printLength (length l) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            string printLength (Length l) {
            {{endgroup}}
            {{group}}
               cout << l.yards << " yds, " << l.feet << " feet, " << l.inches << " in" endl;
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << yards << " yds, " << feet << " feet, " << inches << " in" endl;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << l.inches << " in, " << l.feet << " feet, " << l.yards << " yds" endl;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q9

      .. tb-parsons::
         :name: mucp_9_9

         Let's write the code for the allInches function. 
         printLength should modify a Length object to convert all
         feet and yards to inches. For example, a Length with 1 yard, 2 feet, and 3
         inches is converted into a Length with 0 yards, 0 feet, and 63 inches.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void allInches (Length& l) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void allInches (const length l) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            Length allInches (Length l const) {
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
               int feetToInches = 12 * l.feet;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               double yardToInches = 36 * yards;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q10

      .. tb-parsons::
         :name: mucp_9_10

         Let's write the code for the addLengths function. 
         addLengths should take three Lengths as parameters. 
         It should then add the first two Lengths and store the result
         in the third Length. If there is over 12 inches or over 3 feet,
         convert it to the proper amound of feet and yards (13 inches becomes 1 foot and 1 inch).
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void addLengths (const Length& first, const Length& second, Length& total) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void addLengths (Length& first, Length& second, const Length& total) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void addLengths (Length first, Length second, Length total) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            Length addLengths (Length& first, Length& second, Length& total) {
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
                  int addFeet = total.inches % 12;
            {{endgroup}}
            {{group}}
                  total.feet += addFeet;
            {{endgroup}}
            {{group}}
                  total.inches = total.inches - addFeet * 12;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               if (total.feet >= 3) {
            {{endgroup}}
            {{group}}
                  int addYards = total.feet % 3;
            {{endgroup}}
            {{group}}
                  total.yards += addYards;
            {{endgroup}}
            {{group}}
                  total.feet = total.feet - addYards * 3;
            {{endgroup}}
            {{group}}
               }
            }
            {{endgroup}}

