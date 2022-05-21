Mixed Up Code Practice
----------------------
.. tabbed:: self_check

   .. tab:: Q1

      .. parsonsprob:: mucp_9_1
         :numbered: left
         :adaptive:
         :noindent:
         :practice: T

         Let's write the code for the struct definition of Movie. 
         The Movie structure will have the instance variables title, 
         director, and releaseYear in that order. 
         Put the necessary blocks of code in the correct order.
         -----
         struct Movie {
         =====
         struct movie {  #distractor
         =====
         struct Movie (  #distractor
         =====
            string title;
         =====
            string director;
         =====
            int releaseYear;
         =====
            string releaseYear;  #distractor
         =====
            char title;  #distractor
         =====
         };
         =====
         } #distractor
         =====
         ) #distractor

   .. tab:: Q2

      .. parsonsprob:: mucp_9_2
         :numbered: left
         :adaptive:
         :noindent:

         Let's write the code for the printMovie function. 
         printMovie should print the information about a movie
         in the following format: "title" directed by director (releaseYear).
         Put the necessary blocks of code in the correct order.
         -----
         void printMovie (const Movie& m) {
         =====
         void printMovie (&Movie m const) {  #paired
         =====
         Movie printMovie (Movie m) {  #paired
         =====
            cout << "\"" << m.title << "\" directed by ";
         =====
            cout << m.director << " (" << m.releaseYear << ")" << endl;
         =====
            cout << title << director << releaseYear;  #distractor
         =====
            cout << "\"" << title << "\" directed by ";  #distractor
         =====
            cout << """ << m.title << "" directed by ";  #distractor
         =====
            cout << director << " (" << releaseYear << ")" << endl;  #distractor
         =====
         }

   .. tab:: Q3

      .. parsonsprob:: mucp_9_3
         :numbered: left
         :adaptive:
         :noindent:

         Let's write the code for the movieAge function. 
         movieAge should take a Movie and currentYear as a parameter and
         return how many years it has been since the releaseYear.
         Put the necessary blocks of code in the correct order.
         -----
         int movieAge (const Movie& m, int currentYear) {
         =====
         void movieAge (const Movie& m, int currentYear) {  #distractor
         =====
            return currentYear - m.releaseYear;
         =====
            return currentYear - releaseYear;  #distractor
         =====
            return m.releaseYear - currentYear;  #distractor;
         =====
         }

   .. tab:: Q4

      .. parsonsprob:: mucp_9_4
         :numbered: left
         :adaptive:
         :practice: T

         Let's write the code for the struct definition of Date. 
         The Date structure will have three integer instance variables: day, 
         month, and year in that order. 
         Put the necessary blocks of code in the correct order.
         -----
         struct Date {
         =====
         struct date {  #distractor
         =====
         struct Date (  #distractor
         =====
            int day;
         =====
            int month;
         =====
            int year;
         =====
            string day;  #distractor
         =====
            string month;  #distractor
         =====
            string year;  #distractor
         =====
         };
         =====
         } #distractor
         =====
         ) #distractor

   .. tab:: Q5

      .. parsonsprob:: mucp_9_5
         :numbered: left
         :adaptive:

         Let's write the code for the printDate function. 
         printDate should print the date in the following format: 
         month/date/year.
         Put the necessary blocks of code in the correct order.
         -----
         void printDate (const Date& d) {
         =====
         void printDate (&Date d) {  #paired
         =====
         Date printDate (Date d) {  #paired
         =====
            cout << d.month << "/" << d.day << "/" << d.year << endl;
         =====
            cout << month << "/" << day << "/" << year << endl;  #distractor
         =====
            cout << d.day << "/" << d.month << "/" << d.year << endl;  #distractor
         =====
         }

   .. tab:: Q6

      .. parsonsprob:: mucp_9_6
         :numbered: left
         :adaptive:

         Let's write the code for the nextMonth function. 
         nextMonth should change the date to one month later.
         For example, 3/4/2020 gets modified to 4/4/2020, and 12/3/2020
         gets modified to 1/3/2021.
         Put the necessary blocks of code in the correct order.
         -----
         void nextMonth (Date& d) {
         =====
         void nextMonth (const Date d) {  #paired
         =====
         Date nextMonth (Date& d) {  #paired
         =====
            if (d.month == 12) {
         =====
            if (d.month = 12) {  #distractor
         =====
            if (d.month == 1) {  #distractor
         =====
               d.month = 1;
         =====
               d.year++;
         =====
               d.year = 1;
         =====
            }
         =====
            else {
         =====
               d.month++;
         =====
            }
         =====
         }

   .. tab:: Q7

      .. parsonsprob:: mucp_9_7
         :numbered: left
         :adaptive:

         Let's write the code for the struct definition of Length. 
         Length should have the instance variables inches, feet, and yard.
         Put the necessary blocks of code in the correct order.
         -----
         struct Length {
         =====
         struct length {  #distractor
         =====
         struct Length (  #distractor
         =====
            double inches;
         =====
            double feet;
         =====
            double yards;
         =====
            int inches;  #distractor
         =====
            string feet;  #distractor
         =====
            int yards;  #distractor
         =====
         };
         =====
         } #distractor
         =====
         ) #distractor

   .. tab:: Q8

      .. parsonsprob:: mucp_9_8
         :numbered: left
         :adaptive:

         Let's write the code for the printLength function. 
         printLength should print the date in the following format: 
         yards yds, feet ft, inches in.
         Put the necessary blocks of code in the correct order.
         -----
         void printLength (const Length& l) {
         =====
         void printLength (length l) {  #paired
         =====
         string printLength (Length l) {  #paired
         =====
            cout << l.yards << " yds, " << l.feet << " feet, " << l.inches << " in" endl;
         =====
            cout << yards << " yds, " << feet << " feet, " << inches << " in" endl;  #distractor
         =====
            cout << l.inches << " in, " << l.feet << " feet, " << l.yards << " yds" endl;  #distractor
         =====
         }

   .. tab:: Q9

      .. parsonsprob:: mucp_9_9
         :numbered: left
         :adaptive:

         Let's write the code for the allInches function. 
         printLength should modify a Length object to convert all
         feet and yards to inches. For example, a Length with 1 yard, 2 feet, and 3
         inches is converted into a Length with 0 yards, 0 feet, and 63 inches.
         Put the necessary blocks of code in the correct order.
         -----
         void allInches (Length& l) {
         =====
         void allInches (const length l) {  #paired
         =====
         Length allInches (Length l const) {  #paired
         =====
            l.inches += 36 * l.yards + 12 * l.feet;
         =====
            l.inches = 36 * l.yards + 12 * l.feet;  #distractor
         =====
            int feetToInches = 12 * l.feet;  #distractor
         =====
            double yardToInches = 36 * yards;  #distractor
         =====
         }

   .. tab:: Q10

      .. parsonsprob:: mucp_9_10
         :numbered: left
         :adaptive:

         Let's write the code for the addLengths function. 
         addLengths should take three Lengths as parameters. 
         It should then add the first two Lengths and store the result
         in the third Length. If there is over 12 inches or over 3 feet,
         convert it to the proper amound of feet and yards (13 inches becomes 1 foot and 1 inch).
         Put the necessary blocks of code in the correct order.
         -----
         void addLengths (const Length& first, const Length& second, Length& total) {
         =====
         void addLengths (Length& first, Length& second, const Length& total) {  #paired
         =====
         void addLengths (Length first, Length second, Length total) {  #paired
         =====
         Length addLengths (Length& first, Length& second, Length& total) {  #paired
         =====
            total.inches = first.inches + second.inches;
         =====
            total.feet = first.feet + second.feet;
         =====
            total.yards = first.yards + second.yards;
         =====
            if (total.inches >= 12) {
         =====
               int addFeet = total.inches % 12;
         =====
               total.feet += addFeet;
         =====
               total.inches = total.inches - addFeet * 12;
         =====
            }
         =====
            if (total.feet >= 3) {
         =====
               int addYards = total.feet % 3;
         =====
               total.yards += addYards;
         =====
               total.feet = total.feet - addYards * 3;
         =====
            }
         }

