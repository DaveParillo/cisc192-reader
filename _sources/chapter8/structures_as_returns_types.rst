Structures as return types
--------------------------

You can write functions that return structures. For example,
``find_center`` takes a ``rectangle`` as an argument and returns a
``point`` that contains the coordinates of the center of the
``rectangle``:

::

   point find_center (rectangle& box) {
     double x = box.corner.x + box.width/2;
     double y = box.corner.y + box.height/2;
     point result = {x, y};
     return result;
   }

To call this function, we have to pass a box as an argument (notice that
it is being passed by reference), and assign the return value to a
``point`` variable:

::

     rectangle box = { {0.0, 0.0}, 100, 200 };
     point center = find_center (box);
     print_point (center);

.. tabbed:: self_check

   .. tab:: Q1

      .. activecode:: structures_return_types_AC_1
         :language: cpp

         The active code below uses the ``find_center`` function. Run the code
         to see what the output is!
         ~~~~
         #include <iostream>

         struct point {
             double x, y;
         };

         struct rectangle {
             point corner;
             double width, height;
         };

         void print_point (point p) {
             std::cout << '(' << p.x << ", " << p.y << ")\n";
         }

         point find_center (rectangle& box) {
             double x = box.corner.x + box.width/2;
             double y = box.corner.y + box.height/2;
             point result = {x, y};
             return result;
         }

         int main() {
             rectangle box = { {0.0, 0.0}, 100, 200 };
             point center = find_center (box);
             print_point (center);
         }

      The output of this program is ``(50, 100)``.

   .. tab:: Q2

      .. mchoice:: structures_return_types_1
         :practice: T
         :answer_a: add_two, print_point, find_center
         :answer_b: print_point, find_center
         :answer_c: add_two, find_center
         :answer_d: point, rectangle
         :correct: c
         :feedback_a: Look at the return type, found before the function name in its definition.
         :feedback_b: Look at the return type, found before the function name in its definition.
         :feedback_c: Correct!
         :feedback_d: These are structures, not functions.

         Which functions will return a structure?

         .. code-block:: cpp

            struct point {
              double x, y;
            };

            struct rectangle {
              point corner;
              double width, height;
            };

            rectangle add_two (point& p) {
              double x = p.x + 2;
              double y = p.y + 2;
              point result = {x, y};
              return result;
            }

            void print_point (point p) {
              cout << "(" << p.x << ", " << p.y << ")" << endl;
            }

            point find_center (rectangle& box) {
              double x = box.corner.x + box.width/2;
              double y = box.corner.y + box.height/2;
              point result = {x, y};
              return result;
            }

            int main() {
              rectangle box = { {0.0, 0.0}, 100, 200 };
              point center = find_center (box);
              cout << add_two (center) << endl;
              print_point (center);
            }

