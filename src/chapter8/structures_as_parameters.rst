Structures as parameters
------------------------

You can pass structures as parameters in the usual way. For example,

::

   void print_point (point p) {
     cout << '(' << p.x << ", " << p.y << ')' << '\n';
   }

``print_point`` takes a point as an argument and outputs it in the
standard format. If you call ``print_point (blank)``, it will output
``(3, 4)``.

The active code below uses the ``print_point`` function. Run the code to 
see the output!

.. tb-code:: cpp
   :name: structures_parameters_AC_1
   :caption: Example structures_parameters_AC_1
   :compileargs: ['-Wall', '-std=c++20']

   #include <iostream>
   using namespace std;

   struct point {
       double x, y;
   };

   void print_point (point p) {
       cout << '(' << p.x << ", " << p.y << ')' << '\n';
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
   
.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      The active code below uses the updated version of the ``distance`` function.
      Feel free to modify the code!

      .. tb-code:: cpp
         :name: structures_parameters_AC_2
         :caption: Example structures_parameters_AC_2
         :compileargs: ['-Wall', '-std=c++20']

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
             cout << "The distance from the point to the origin is " << distance (origin, point) << '\n';
         }

   .. tb-tab:: Q2

      .. tb-choice::
         :name: structures_parameters_1

         What will print?

         .. code-block:: cpp

            struct coordinate {
              int x, y;
            };

            void print_opposite_coordinate (coordinate p) {
              cout << '(' << -p.y << ", " << -p.x << ')' << '\n';
            }

            int main() {
              coordinate coord = { 2, 7 };
              print_opposite_coordinate (coord);
            }

         - [ ] ``(-2, -7)``

           - Take a close look at the print_opposite_coordinate function.

         - [ ] ``(2.0, 7.0)``

           - Take a close look at the print_opposite_coordinate function.

         - [x] ``(-7, -2)``

           + Yes, this is the correct output.

         - [ ] ``(-7.0, -2.0)``

           - Take a close look at the coordinate struct.


   .. tb-tab:: Q3

      .. tb-parsons::
         :name: structures_parameters_2

         Construct a function that takes in three point structures and prints the average of the x coordinates and the average of the y coordinates as a coordinate. Find the x average before the y average.

         .. code-block:: cpp

            {{group}}
            void print_average_point(point p1, point p2, point p3) {
            {{endgroup}}
            {{group}}
             double avg_x = (p1.x + p2.x + p3.x)/3;
            {{endgroup}}
            {{group}}
             double avg_y = (p1.y + p2.y + p3.y)/3;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double avg_y = (y.p1 + y.p2 + y.p3)/3; #distractor
            {{endgroup}}
            {{group}}
             cout << '(' << avg_x << ',' << avg_y << ')';
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << '(' << "avg_x" << ',' << "avg_y" << ')'; #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

