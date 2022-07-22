Mixed-Up Code Exercises
-----------------------

Answer the following **Mixed-Up Code** questions to
assess what you have learned in this chapter.

.. tabbed:: tab_check

   .. tab:: Q1

      .. parsonsprob:: functions_p9
         :numbered: left
         :adaptive:

         Construct a function that correctly prints the integer conversion of the passed double.
        
         -----
         void print_integer (double d) {
         =====
         print_integer (double d); #paired
         =====
          d = int(d);
         =====
          d = integer(d); #paired
         =====
          cout << d;
         =====
          cout d; #paired
         =====
         }


   .. tab:: Q2

      .. parsonsprob:: functions_p0
         :numbered: left
         :adaptive:

         Construct a function called newLine that takes no arguments and prints a blank line.  Then construct another function called divider that prints two blank lines separated by a line of ". . . . . . . . . . . ."
         -----
         void new_line () {
         =====
          cout << endl;
         =====
         }  //new_line
         =====
         void divider () {
         =====
          void divider (newLine) { #paired
         =====
          new_line ();  //first call
         =====
          cout << new_line ();  //first call #paired
         =====
          cout << ". . . . . . . . . . . . " << endl;
         =====
          new_line ();  //second call
         =====
          cout << new_line ();  //second call #paired
         =====
         }  //divider


   .. tab:: Q1

      .. parsonsprob:: functions_p1
         :numbered: left
         :adaptive:

         Construct a function that correctly calculates the volume of a cone with as much precision as possible and prints the value to the terminal.

         -----
         void volume_cone (double r, double h) {
         =====
         double volume_cone (double r, double h) { #paired
         =====
          constexpr double pi = 3.1415926;
         =====
          double vol = 1/3.0 * pi * r * r * h;
         =====
          double vol = 1/3 * pi * r * r * h; #paired
         =====
          int vol = 1/3 * pi * r * r * h; #paired
         =====
          int vol = 1/3.0 * pi * r * r * h; #paired
         =====
          cout << vol;
         =====
         }


   .. tab:: Q4

      .. parsonsprob:: functions_p3
         :numbered: left
         :adaptive:

         Construct a function that prints the sin of an angle given in degrees.
         -----
         #include &#60;cmath&#62;
         =====
         #include &#60;iostream&#62;
         using namespace std;
         =====
         void sine_degrees (double d) {
         =====
         void sine_degrees () { #paired
         =====
          constexpr double pi = 3.1415926;
         =====
          double r = d * (2 * pi) / 360.0;
         =====
          double r = d * 360.0 / (2 * pi); #paired
         =====
          cout <<  sin(r);
         =====
          cout <<  sin(d); #paired
         =====
         }
         =====
          #include &#60;math&#62; #distractor


   .. tab:: Q5

      .. parsonsprob:: functions_p4_0
         :numbered: left
         :adaptive:

         Construct a function that prints the price (with 8% sales tax) of
         an item with after using a 30% off coupon.
         -----
         void final_price (double item) {
         =====
         void final_price (string item) { #paired
         =====
          double discount = item * 0.30;
         =====
          double final = (item - discount) * 1.08;
         =====
          double final = (item - discount) * 0.08; #paired
         =====
          double final = item - discount * 0.08; #paired
         =====
          cout << final;
         =====
         }


   .. tab:: Q6

      .. parsonsprob:: functions_p5
         :numbered: left
         :adaptive:

         Suppose you have already defined a function called ``sum_of_squares``
         which returns the sum of the squares of two numbers and ``sqrt`` which
         returns the square root of a number.
         Construct a function that calculates the hypotenuse of the right
         triangle and prints the three sidelengths.
         -----
         int main () {
         =====
          double s1 = 4.8;
          double s2 = 3.8;
         =====
          int s1 = 4.8; #paired
          int s2 = 3.6;
         =====
          double sum = sum_of_squares(s2, s1);
         =====
          sum = sum_of_squares(s1, s2); #paired
         =====
          double hypot = sqrt(sum);
         =====
          double hypot = sqrt(s1, s2); #paired
         =====
          cout << "The sides of the triangle are: " << s1 << ", " << s2 << ", " << hypot;
         =====
          cout << "The sides of the triangle are: " << s1 << ", " << s2 << ", " << s3; #paired
         =====
         }


   .. tab:: Q7

      .. parsonsprob:: functions_p6
         :numbered: left
         :adaptive:

         The chickens from the previous chapter are infuriated.
         Construct a function that prints "Eat" on the first line,
         "More" on the second line, and the name of the passed animal
         on the fourth line, followed by an exclamation point.  
         -----
         void eat_more (string animal) {
         =====
         void eat_more () { #paired
         =====
          cout << "Eat";
         =====
          cout << "Eat" << endl; #paired
         =====
          cout << endl; cout << "More" << endl;
         =====
          cout << endl;
         =====
          cout << animal << "!" << endl;
         =====
          cout << animal << ! << endl; #paired
         =====
         }


   .. tab:: Q8

      .. parsonsprob:: functions_p7
         :numbered: left
         :adaptive:

         Construct a function that takes a dollar amount and cent amount and
         prints the total amount of money that you have.
         Hint: the mod operator (``%``) returns the remainder of a division.
         -----
         void print (int dollars, int cents) {
         =====
          int dollar_total = dollars + cents / 100;
         ===== 
          double dollar_total = dollars + cents / 100.0; #paired
         =====
          double cent_total = cents % 100;
         =====
          double cent_total = cents / 100; #paired
         =====
          cout << '$' << dollarTotal << '.' << centTotal;
         =====
          cout << '$' << dollarTotal << centTotal; #paired
         =====
         }


   .. tab:: Q9

      .. parsonsprob:: functions_p8
         :numbered: left
         :adaptive:

         In Michigan, the probability that it snows on any given day
         in the winter is about 14%.
         The probability of having a snow day on any given day
         in the winter is about 4%.
         The probability that is snows and you have a snow day is 8%.  
         Construct and call a function that calculates the probability of
         having a snow day, given the fact that it will snow tonight.  
         For reference, the formula for conditional probability is: 
         ``P(A|B) = P(B and A) / P(B)``.
         -----
         void conditional_probability (double B, double both) {
         =====
         void conditional_probability (double B, both) { #paired
         =====
          double prob = both / B;
         =====
          double prob = B / both; #paired
         =====
          cout << prob;
         =====
         } //conditional_probability
         =====
         int main () {
         =====
          double pSnow = 0.14;
          double pSnowday = 0.04;
          double pBoth = 0.08;
         =====
          conditional_probability(pSnow, pBoth);
         =====
          conditional_probability(pSnowday, pBoth); #paired
         =====
          conditional_probability(pSnowday, pSnow); #paired
         =====
         } //main


   .. tab:: Q10

      .. parsonsprob:: functions_p2
         :numbered: left
         :adaptive:

         Your final grade is determined by a midterm component
         (each midterm is worth 20% of the grade) and a final component.
         In order to avoid any discrepancies with students who's grades are
         on the fence, your teacher follows this strict grading scale: 
         [0%,60%) = F, [60%, 70%) = D, [70%, 80%) = C,
         [80%, 90%) = B and [90%, 100%] = A.
         They do not truncate until the very end.  
         Construct a function that determines your final grade percentage
         according to this grading scheme and prints the result.
         -----
         void final_grade (double m1, double m2, double f) {
         =====
         void final_grade (double m1, m2, f) { #paired
         =====
          double m_comp = m1 * 0.2 + m2 * 0.2;
          double f_comp = f * 0.06;
         =====
          int m_comp = m1 * 0.2 + m2 * 0.2; #paired
          int f_comp = f * 0.06;
         =====
          double grade = m_comp + f_comp;
         =====
          cout << int(grade);
         =====
          cout << int(grade) + 1; #paired
         =====
          cout << grade; #paired
         =====
         }
