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
         void printInteger (double d) {
         =====
         printInteger (double d); #paired
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
         void newLine () {
         =====
          cout << endl;
         =====
         }  //newLine
         =====
         void divider () {
         =====
          void divider (newLine) { #paired
         =====
          newLine ();  //first call
         =====
          cout << newLine ();  //first call #paired
         =====
          cout << ". . . . . . . . . . . . " << endl;
         =====
          newline ();  //second call
         =====
          cout << newLine ();  //second call #paired
         =====
         }  //divider


   .. tab:: Q1

      .. parsonsprob:: functions_p1
         :numbered: left
         :adaptive:

         Construct a function that correctly calculates the volume of a cone with as much precision as possible and prints the value to the terminal.  Use 3.14 for pi.

         -----
         void volumeCone (double r, double h) {
         =====
         double volumeCone (double r, double h) { #paired
         =====
          double vol = 1/3.0 * 3.14 * r * r * h;
         =====
          double vol = 1/3 * 3.14 * r * r * h; #paired
         =====
          int vol = 1/3 * 3.14 * r * r * h; #paired
         =====
          int vol = 1/3.0 * 3.14 * r * r * h; #paired
         =====
          cout << vol;
         =====
         }


   .. tab:: Q4

      .. parsonsprob:: functions_p3
         :numbered: left
         :adaptive:

         Construct a function that prints the sin of an angle given in degrees. Use 3.14 for pi.
         -----
         #include &#60;cmath&#62;
         =====
         #include &#60;iostream&#62;
         using namespace std;
         =====
         void sineDegrees (double d) {
         =====
         void sineDegrees () { #paired
         =====
          double r = d * (2 * 3.14) / 360.0;
         =====
          double r = d * 360.0 / (2 * 3.14); #paired
         =====
          double sine = sin(r);
         =====
          double sine = sin(d); #paired
         =====
          cout << sine;
         =====
         }
         =====
          #include &#60;math&#62; #distractor


   .. tab:: Q5

      .. parsonsprob:: functions_p4_0
         :numbered: left
         :adaptive:

         Construct a function that prints the price (with 8% sales tax) of an item with after using a 30% off coupon.
         -----
         void finalPrice (double item) {
         =====
         void finalPrice (string item) { #paired
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

         Suppose you have already defined a function called sumOfSquares which returns the sum of the squares of two numbers and root which returns the square root of a number.  Construct a function that calculates the hypotenuse of the right triangle and prints the three sidelengths.
         -----
         int main () {
         =====
          double s1 = 4.8;
          double s2 = 3.8;
         =====
          int s1 = 4.8; #paired
          int s2 = 3.6;
         =====
          double sqSum = sumOfSquares(s2, s1);
         =====
          sqSum = sumOfSquares(s1, s2); #paired
         =====
          double hyp = root(sqSum);
         =====
          double hyp = root(s1, s2); #paired
         =====
          cout << "The sides of the triangle are: " << s1 << ", " << s2 << ", " << hyp;
         =====
          cout << "The sides of the triangle are: " << s1 << ", " << s2 << ", " << s3; #paired
         =====
         }


   .. tab:: Q7

      .. parsonsprob:: functions_p6
         :numbered: left
         :adaptive:

         The chickens from the previous chapter are infuriated.  Construct a function that prints "Eat" on the first line, "More" on the second line, and the name of the passed animal on the fourth line, followed by an exclamation point.  
         -----
         void eatMore (string animal) {
         =====
         void eatMore () { #paired
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

         Construct a function that takes a dollar amount and cent amount and prints the total amount of money that you have. Hint: the mod operator '%' returns the remainder of a division.
         -----
         void printAmount (int dollars, int cents) {
         =====
          int dollarTotal = dollars + cents / 100;
         ===== 
          double dollarTotal = dollars + cents / 100.0; #paired
         =====
          double centTotal = cents % 100;
         =====
          double centTotal = cents / 100; #paired
         =====
          cout << "$" << dollarTotal << "." << centTotal;
         =====
          cout << "$" << dollarTotal << centTotal; #paired
         =====
         }


   .. tab:: Q9

      .. parsonsprob:: functions_p8
         :numbered: left
         :adaptive:

         In Michigan, the probability that it snows on any given day in the winter is about 14%.  The probability of having a snow day on any given day in the winter is about 4%.  The probability that is snows and you have a snow day is 8%.  
         Construct and call a function that calculates the probability of a having a snow day, given the fact that it will snow tonight.  
         For reference, the formula for conditional probability is: P(A|B) = P(B and A) / P(B).
         -----
         void conditionalProb (double B, double both) {
         =====
         void conditionalProb (double B, both) { #paired
         =====
          double prob = both / B;
         =====
          double prob = B / both; #paired
         =====
          cout << prob;
         =====
         } //conditionalProb
         =====
         int main () {
         =====
          double pSnow = 0.14;
          double pSnowday = 0.04;
          double pBoth = 0.08;
         =====
          conditionalProb(pSnow, pBoth);
         =====
          conditionalProb(pSnowday, pBoth); #paired
         =====
          conditionalProb(pSnowday, pSnow); #paired
         =====
         } //main


   .. tab:: Q10

      .. parsonsprob:: functions_p2
         :numbered: left
         :adaptive:

         Your final grade is determined by a midterm component (each midterm is worth 20% of the grade) and a final component. In order to avoid any discrepancies with students who's grades are on the fence, your teacher follows this strict grading scale: 
         [0%,60%) = F, [60%, 70%) = D, [70%, 80%) = C, [80%, 90%) = B and [90%, 100%] = A. He does not round until the very end.  
         Construct a function that determines a student's final grade percentage according to this grading scheme and prints the result.
         -----
         void finalGrade (double m1, double m2, double f) {
         =====
         void finalGrade (double m1, m2, f) { #paired
         =====
          double m_comp = m1 * 0.2 + m2 * 0.2;
          double f_comp = f * 0.06;
         =====
          int m_comp = m1 * 0.2 + m2 * 0.2; #paired
          int f_comp = f * 0.06;
         =====
          double final_grade = m_comp + f_comp;
         =====
          cout << int(final_grade);
         =====
          cout << int(final_grade) + 1; #paired
         =====
          cout << final_grade; #paired
         =====
         }
