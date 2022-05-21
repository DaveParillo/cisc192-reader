Structures as parameters
------------------------

You can pass structures as parameters in the usual way. For example,

::

   void print_point (point p) {
     cout << "(" << p.x << ", " << p.y << ")" << endl;
   }

``print_point`` takes a point as an argument and outputs it in the
standard format. If you call ``print_point (blank)``, it will output
``(3, 4)``.

.. activecode:: structures_parameters_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:

   The active code below uses the ``print_point`` function. Run the code to 
   see the output!
   ~~~~
   #include <iostream>
   using namespace std;
 
   struct point {
       double x, y;
   };
 
   void print_point (point p) {
       cout << "(" << p.x << ", " << p.y << ")" << endl;
   }
 
   int main() {
       point blank = { 3.0, 4.0 };
       print_point (blank);
   }

As a second example, we can rewrite the ``distance`` function from
Section `[distance] <#distance>`__ so that it takes two ``point``\ s as
parameters instead of four ``double``\ s.

::

   double distance (point p1, point p2) {
     double dx = p2.x - p1.x;
     double dy = p2.y - p1.y;
     return sqrt (dx*dx + dy*dy);
   }
   
.. tabbed:: self_check

   .. tab:: Q1

      .. activecode:: structures_parameters_AC_2
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:

         The active code below uses the updated version of the ``distance`` function.
         Feel free to modify the code!
         ~~~~
         #include <iostream>
         #include <cmath>
         using namespace std;
 
         struct point {
             double x, y;
         };
 
         double distance (point p1, point p2) {
             double dx = p2.x - p1.x;
             double dy = p2.y - p1.y;
             return sqrt (dx*dx + dy*dy);
         }
 
         int main() {
             point origin = { 0.0, 0.0 };
             point point = { 3.0, 4.0 };
             cout << "The distance from the point to the origin is " << distance (origin, point) << endl;
         }

   .. tab:: Q2

      .. mchoice:: structures_parameters_1
         :practice: T
         :answer_a: (-2.0, -7.0)
         :answer_b: (2.0, 7.0)
         :answer_c: (-7.0, -2.0)
         :answer_d: (7.0, 2.0)
         :correct: c
         :feedback_a: Take a close look at the print_opposite_coordinate function.
         :feedback_b: Take a close look at the print_opposite_coordinate function.
         :feedback_c: Yes, this is the correct output.
         :feedback_d: Take a close look at the print_opposite_coordinate function.

         What will print?

         .. code-block:: cpp

            struct coordinate {
              double x, y;
            };

            void print_opposite_coordinate (point p) {
              cout << "(" << -p.y << ", " << -p.x << ")" << endl;
            }

            int main() {
              coordinate coord = { 2.0, 7.0 };
              print_opposite_coordinate (coord);
            }

   .. tab:: Q3

      .. parsonsprob:: structures_parameters_2
         :numbered: left
         :adaptive:

         Construct a function that takes in three point structures and prints the average of the x coordinates and the average of the y coordinates as a coordinate. Find the x average before the y average.
         -----
         void print_average_point(point p1, point p2, point p3) {
         =====
          double avg_x = (p1.x + p2.x + p3.x)/3;
         =====
          double avg_y = (p1.y + p2.y + p3.y)/3;
         =====
          double avg_y = (y.p1 + y.p2 + y.p3)/3; #distractor
         =====
          cout << "(" << avg_x << "," << avg_y << ")";
         =====
          cout << "(" << "avg_x" << "," << "avg_y" << ")"; #distractor
         =====
         }

