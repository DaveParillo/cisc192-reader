.. _functions-mixed-up-code-exercises:

Mixed-Up Code Exercises
-----------------------

Answer the following **Mixed-Up Code** questions to
assess what you have learned in this chapter.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: functions_p9

         Construct a function that correctly prints the integer conversion of the passed double.

         .. code-block:: cpp

            {{group}}
            void print_integer (double d) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            print_integer (double d);
            {{endgroup}}
            {{group}}
             d = int(d);
            {{endgroup}}
            {{distractor}}
            {{group}}
             d = integer(d);
            {{endgroup}}
            {{group}}
             cout << d;
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout d;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: functions_p0

         Construct a function called new_line that takes no arguments and prints a blank line.  Then construct another function called divider that prints two blank lines separated by a line of ". . . . . . . . . . . ."

         .. code-block:: cpp

            {{group}}
            void new_line () {
            {{endgroup}}
            {{group}}
             cout << '\n';
            {{endgroup}}
            {{group}}
            }  //new_line
            {{endgroup}}
            {{group}}
            void divider () {
            {{endgroup}}
            {{distractor}}
            {{group}}
             void divider (new_line) {
            {{endgroup}}
            {{group}}
             new_line ();  //first call
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << new_line ();  //first call
            {{endgroup}}
            {{group}}
             cout << ". . . . . . . . . . . . " << '\n';
            {{endgroup}}
            {{group}}
             new_line ();  //second call
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << new_line ();  //second call
            {{endgroup}}
            {{group}}
            }  //divider
            {{endgroup}}

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: functions_p1

         Construct a function that correctly calculates the volume of a cone with as much precision as possible and prints the value to the terminal.

         .. code-block:: cpp

            {{group}}
            void volume_cone (double r, double h) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            double volume_cone (double r, double h) {
            {{endgroup}}
            {{group}}
             constexpr double pi = 3.1415926;
            {{endgroup}}
            {{group}}
             double vol = 1/3.0 * pi * r * r * h;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double vol = 1/3 * pi * r * r * h;
            {{endgroup}}
            {{distractor}}
            {{group}}
             int vol = 1/3 * pi * r * r * h;
            {{endgroup}}
            {{distractor}}
            {{group}}
             int vol = 1/3.0 * pi * r * r * h;
            {{endgroup}}
            {{group}}
             cout << vol;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q4

      .. tb-parsons::
         :name: functions_p3

         Construct a function that prints the sin of an angle given in degrees.

         .. code-block:: cpp

            {{group}}
            #include &#60;cmath&#62;
            {{endgroup}}
            {{group}}
            #include &#60;iostream&#62;
            using namespace std;
            {{endgroup}}
            {{group}}
            void sine_degrees (double d) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void sine_degrees () {
            {{endgroup}}
            {{group}}
             constexpr double pi = 3.1415926;
            {{endgroup}}
            {{group}}
             double r = d * (2 * pi) / 360.0;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double r = d * 360.0 / (2 * pi);
            {{endgroup}}
            {{group}}
             cout <<  sin(r);
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout <<  sin(d);
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}
            {{distractor}}
            {{group}}
             #include &#60;math&#62; #distractor
            {{endgroup}}

   .. tb-tab:: Q5

      .. tb-parsons::
         :name: functions_p4_0

         Construct a function that prints the price (with 8% sales tax) of
         an item with after using a 30% off coupon.

         .. code-block:: cpp

            {{group}}
            void final_price (double item) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void final_price (string item) {
            {{endgroup}}
            {{group}}
             double discount = item * 0.30;
            {{endgroup}}
            {{group}}
             double final = (item - discount) * 1.08;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double final = (item - discount) * 0.08;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double final = item - discount * 0.08;
            {{endgroup}}
            {{group}}
             cout << final;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q6

      .. tb-parsons::
         :name: functions_p5

         Suppose you have already defined a function called ``sum_of_squares``
         which returns the sum of the squares of two numbers and ``sqrt`` which
         returns the square root of a number.
         Construct a function that calculates the hypotenuse of the right
         triangle and prints the three sidelengths.

         .. code-block:: cpp

            {{group}}
            int main () {
            {{endgroup}}
            {{group}}
             double s1 = 4.8;
             double s2 = 3.8;
            {{endgroup}}
            {{distractor}}
            {{group}}
             int s1 = 4.8;
             int s2 = 3.6;
            {{endgroup}}
            {{group}}
             double sum = sum_of_squares(s2, s1);
            {{endgroup}}
            {{distractor}}
            {{group}}
             sum = sum_of_squares(s1, s2);
            {{endgroup}}
            {{group}}
             double hypot = sqrt(sum);
            {{endgroup}}
            {{distractor}}
            {{group}}
             double hypot = sqrt(s1, s2);
            {{endgroup}}
            {{group}}
             cout << "The sides of the triangle are: " << s1 << ", " << s2 << ", " << hypot;
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << "The sides of the triangle are: " << s1 << ", " << s2 << ", " << s3;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q7

      .. tb-parsons::
         :name: functions_p6

         The chickens from the previous chapter are infuriated.
         Construct a function that prints "Eat" on the first line,
         "More" on the second line, and the name of the passed animal
         on the fourth line, followed by an exclamation point.  

         .. code-block:: cpp

            {{group}}
            void eat_more (string animal) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void eat_more () {
            {{endgroup}}
            {{group}}
             cout << "Eat";
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << "Eat" << '\n';
            {{endgroup}}
            {{group}}
             cout << '\n'; cout << "More" << '\n';
            {{endgroup}}
            {{group}}
             cout << '\n';
            {{endgroup}}
            {{group}}
             cout << animal << '!' << '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << animal << ! << '\n';
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q8

      .. tb-parsons::
         :name: functions_p7

         Construct a function that takes a dollar amount and cent amount and
         prints the total amount of money that you have.
         Hint: the mod operator (``%``) returns the remainder of a division.

         .. code-block:: cpp

            {{group}}
            void print (int dollars, int cents) {
            {{endgroup}}
            {{group}}
             int dollar_total = dollars + cents / 100;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double dollar_total = dollars + cents / 100.0;
            {{endgroup}}
            {{group}}
             double cent_total = cents % 100;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double cent_total = cents / 100;
            {{endgroup}}
            {{group}}
             cout << '$' << dollar_total << '.' << cent_total;
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << '$' << dollar_total << cent_total;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q9

      .. tb-parsons::
         :name: functions_p8

         In Michigan, the probability that it snows on any given day
         in the winter is about 14%.
         The probability of having a snow day on any given day
         in the winter is about 4%.
         The probability that is snows and you have a snow day is 8%.  
         Construct and call a function that calculates the probability of
         having a snow day, given the fact that it will snow tonight.  
         For reference, the formula for conditional probability is: 
         ``P(A|B) = P(B and A) / P(B)``.

         .. code-block:: cpp

            {{group}}
            void conditional_probability (double B, double both) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void conditional_probability (double B, both) {
            {{endgroup}}
            {{group}}
             double prob = both / B;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double prob = B / both;
            {{endgroup}}
            {{group}}
             cout << prob;
            {{endgroup}}
            {{group}}
            } //conditional_probability
            {{endgroup}}
            {{group}}
            int main () {
            {{endgroup}}
            {{group}}
             double p_snow = 0.14;
             double p_snowday = 0.04;
             double p_both = 0.08;
            {{endgroup}}
            {{group}}
             conditional_probability(p_snow, p_both);
            {{endgroup}}
            {{distractor}}
            {{group}}
             conditional_probability(p_snowday, p_both);
            {{endgroup}}
            {{distractor}}
            {{group}}
             conditional_probability(p_snowday, p_snow);
            {{endgroup}}
            {{group}}
            } //main
            {{endgroup}}

   .. tb-tab:: Q10

      .. tb-parsons::
         :name: functions_p2

         Your final grade is determined by a midterm component
         (each midterm is worth 20% of the grade) and a final component.
         In order to avoid any discrepancies with students who's grades are
         on the fence, your teacher follows this strict grading scale: 
         [0%,60%) = F, [60%, 70%) = D, [70%, 80%) = C,
         [80%, 90%) = B and [90%, 100%] = A.
         They do not truncate until the very end.  
         Construct a function that determines your final grade percentage
         according to this grading scheme and prints the result.

         .. code-block:: cpp

            {{group}}
            void final_grade (double m1, double m2, double f) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void final_grade (double m1, m2, f) {
            {{endgroup}}
            {{group}}
             double m_comp = m1 * 0.2 + m2 * 0.2;
             double f_comp = f * 0.06;
            {{endgroup}}
            {{distractor}}
            {{group}}
             int m_comp = m1 * 0.2 + m2 * 0.2;
             int f_comp = f * 0.06;
            {{endgroup}}
            {{group}}
             double grade = m_comp + f_comp;
            {{endgroup}}
            {{group}}
             cout << int(grade);
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << int(grade) + 1;
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << grade;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

