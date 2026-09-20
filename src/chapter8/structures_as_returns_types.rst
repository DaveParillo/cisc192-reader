.. _structures-structures-as-return-types:

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

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      The active code below uses the ``find_center`` function. Run the code
      to see what the output is!

      .. tb-code:: cpp
         :name: structures_return_types_AC_1
         :caption: Example structures_return_types_AC_1

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

   .. tb-tab:: Q2

      .. tb-choice::
         :name: structures_return_types_1

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
              cout << '(' << p.x << ", " << p.y << ')' << '\n';
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
              cout << add_two (center) << '\n';
              print_point (center);
            }

         - [ ] ``add_two``, ``print_point``, ``find_center``

           - Look at the return type, found before the function name in its definition.
         - [ ] ``print_point``, ``find_center``

           - Look at the return type, found before the function name in its definition.

         - [x] ``add_two``, ``find_center``

           + Correct!

         - [ ] ``point``, ``rectangle``

           - These are structures, not functions.

