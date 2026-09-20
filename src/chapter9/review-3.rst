.. _more-structures-coding-practice:

Coding Practice
---------------

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-group::
         :name: cp_9_1

         .. tb-tab:: Question

            Write the ``cake`` structure, which has instance variables name, color, diameter, and has_icing.

            .. tb-code:: cpp
               :name: cp_9_AC_1q
               :caption: Example cp_9_AC_1q

               #include <iostream>
               using namespace std;

               // Write your code for the struct cake here.

               int main() {
                   cake c = { "Mary", "blue", 3.5, false };
               } 


         .. tb-tab:: Answer

            Below is one way to implement the program. We declare the ``cake`` struct and list the instance 
            variables in order.

            .. tb-code:: cpp
               :name: cp_9_AC_1a
               :caption: Example cp_9_AC_1a

               #include <iostream>
               using namespace std;

               struct cake {
                   string name;
                   string color;
                   double diameter;
                   bool has_icing;
               };

               int main() {
                   cake c = { "Mary", "blue", 3.5, false };
               } 

   .. tb-tab:: Q2

      Write the function ``print_cake_info``, which prints the cake's information in the format
      "This is a ``color``, ``diameter`` inch diameter cake with/without icing." If ``name`` does not
      have the value "n/a", ``print_cake_info`` prints out "Happy birthdday ``name``! Your cake is ``color``,
      has a ``diameter`` inch diameter, and comes with/without icing."

      .. tb-code:: cpp
         :name: cp_9_AC_2q
         :caption: Example cp_9_AC_2q

         #include <iostream>
         using namespace std;

         struct cake {
             string name;
             string color;
             double diameter;
             bool has_icing;
         };

         // Write your code for the print_cake_info function here.

         int main() {
             cake c1 = { "n/a", "red", 12.5, true };
             print_cake_info (c1);
             cake c2 = { "Tom", "white", 10, false };
             print_cake_info (c2);
         }

   .. tb-tab:: Q3

      .. tb-group::
         :name: cp_9_3

         .. tb-tab:: Question

            Write the ``make_cake`` function, which prompts the user for a name,
            color, diameter, and whether or not they want icing. The function then
            returns the cake.

            .. tb-code:: cpp
               :name: cp_9_AC_3q-support
               :hidden:
               :stdin: test

               void print_cake_info (cake c) {
                   if (c.name == "n/a") {
                       if (c.has_icing) { 
                           cout << "This is a " << c.color << ',' << c.diameter << " inch diameter cake with icing." << '\n';
                       } 
                       else {
                           cout << "This is a " << c.color << ',' << c.diameter << " inch diameter cake without icing." << '\n';
                       }
                   } 
                   else {
                       if (c.has_icing) { 
                           cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes with icing." << '\n';
                       } 
                       else {
                           cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes without icing." << '\n';
                       }
                   } 
               }



            .. tb-code:: cpp
               :name: cp_9_AC_3q
               :caption: Example cp_9_AC_3q
               :run-after: cp_9_AC_3q-support
               :stdin: test

               #include <iostream>
               using namespace std;

               struct cake {
                   string name;
                   string color;
                   double diameter;
                   bool has_icing;
               };

               void print_cake_info (cake c);

               // Write your code for the make_cake function here.

               int main() {
                   cake input = make_cake ();
                   print_cake_info (input);
               }

         .. tb-tab:: Answer

            Below is one way to implement the program. We create a ``cake`` for the user, read in the user's input using cin, and return the ``cake``.

            .. tb-code:: cpp
               :name: cp_9_AC_3a-support
               :hidden:
               :stdin: test

               void print_cake_info (cake c) {
                   if (c.name == "n/a") {
                       if (c.has_icing) { 
                           cout << "This is a " << c.color << ',' << c.diameter << " inch diameter cake with icing." << '\n';
                       } 
                       else {
                           cout << "This is a " << c.color << ',' << c.diameter << " inch diameter cake without icing." << '\n';
                       }
                   } 
                   else {
                       if (c.has_icing) { 
                           cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes with icing." << '\n';
                       } 
                       else {
                           cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes without icing." << '\n';
                       }
                   } 
               }


            .. tb-code:: cpp
               :name: cp_9_AC_3a
               :caption: Example cp_9_AC_3a
               :run-after: cp_9_AC_3a-support
               :stdin: test

               #include <iostream>
               using namespace std;

               struct cake {
                   string name;
                   string color;
                   double diameter;
                   bool has_icing;
               };

               void print_cake_info (cake c);

               cake make_cake () {
                   cake input;
                   string name, color;
                   double diameter;
                   char icing;
                   cout << "Name: ";
                   cin >> name;
                   input.name = name;
                   cout << "Color: ";
                   cin >> color;
                   input.color = color;
                   cout << "Diameter: ";
                   cin >> diameter;
                   input.diameter = diameter;
                   cout << "Icing? (y/n) ";
                   cin >> icing;
                   if (icing == 'y') {
                       input.has_icing = true;
                   }
                   else {
                       input.has_icing = false; 
                   } 
                   return input;
               }

               int main() {
                   cake input = make_cake ();
                   print_cake_info (input);
               }

   .. tb-tab:: Q4

      Write the function ``change_cake_diameter``, which takes a ``cake`` and a ``double`` as a parameter. 
      ``change_cake_diameter`` then multiplies the original diameter by the double and modifies the cake
      to have this new diameter.

      .. tb-code:: cpp
         :name: cp_9_AC_4q-support
         :hidden:

         void print_cake_info (cake c) {
             if (c.name == "n/a") {
                 if (c.has_icing) { 
                     cout << "This is a " << c.color << ',' << c.diameter << " inch diameter cake with icing." << '\n';
                 } 
                 else {
                     cout << "This is a " << c.color << ',' << c.diameter << " inch diameter cake without icing." << '\n';
                 }
             } 
             else {
                 if (c.has_icing) { 
                     cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes with icing." << '\n';
                 } 
                 else {
                     cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes without icing." << '\n';
                 }
             } 
         }

         cake make_cake () {
             cake input;
             string name, color;
             double diameter;
             char icing;
             cout << "Name: ";
             cin >> name;
             input.name = name;
             cout << "Color: ";
             cin >> color;
             input.color = color;
             cout << "Diameter: ";
             cin >> diameter;
             input.diameter = diameter;
             cout << "Icing? (y/n) ";
             cin >> icing;
             if (icing == 'y') {
                 input.has_icing = true;
             }
             else {
                 input.has_icing = false; 
             } 
             return input;
         }


      .. tb-code:: cpp
         :name: cp_9_AC_4q
         :caption: Example cp_9_AC_4q
         :run-after: cp_9_AC_4q-support

         #include <iostream>
         using namespace std;

         struct cake {
             string name;
             string color;
             double diameter;
             bool has_icing;
         };

         void print_cake_info (cake c);
         cake make_cake ();

         // Write your code for the change_cake_diameter function here.

         int main() {
             cake original = { "John", "green", 8.5, true };
             change_cake_diameter (original, 2);
             print_cake_info (original);
         }

   .. tb-tab:: Q5

      .. tb-group::
         :name: cp_9_5

         .. tb-tab:: Question

            Write the ``edit_cake`` function, which prompts the user for a new name,
            color, diameter, and whether or not they want icing. The function modifies 
            the original cake that is passed in as a parameter. Use the make_cake function 
            in your implementation to avoid duplicate code!

            .. tb-code:: cpp
               :name: cp_9_AC_5q-support
               :hidden:
               :stdin: test

                void print_cake_info (cake c) {
                    if (c.name == "n/a") {
                        if (c.has_icing) { 
                            cout << "This is a " << c.color << ',' << c.diameter << " inch diameter cake with icing." << '\n';
                        } 
                        else {
                            cout << "This is a " << c.color << ',' << c.diameter << " inch diameter cake without icing." << '\n';
                        }
                    } 
                    else {
                        if (c.has_icing) { 
                            cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes with icing." << '\n';
                        } 
                        else {
                            cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes without icing." << '\n';
                        }
                    } 
                }

                cake make_cake () {
                    cake input;
                    string name, color;
                    double diameter;
                    char icing;
                    cout << "Name: ";
                    cin >> name;
                    input.name = name;
                    cout << "Color: ";
                    cin >> color;
                    input.color = color;
                    cout << "Diameter: ";
                    cin >> diameter;
                    input.diameter = diameter;
                    cout << "Icing? (y/n) ";
                    cin >> icing;
                    if (icing == 'y') {
                        input.has_icing = true;
                    }
                    else {
                        input.has_icing = false; 
                    } 
                    return input;
                }



            .. tb-code:: cpp
               :name: cp_9_AC_5q
               :caption: Example cp_9_AC_5q
               :run-after: cp_9_AC_5q-support
               :stdin: test

               #include <iostream>
               using namespace std;

               struct cake {
                   string name;
                   string color;
                   double diameter;
                   bool has_icing;
               };

               void print_cake_info (cake c);
               cake make_cake ();

               // Write your code for the edit_cake function here.

               int main() {
                   cake original = { "Oops", "orange", 185, true };
                   edit_cake (original);
                   print_cake_info (original);
               }

         .. tb-tab:: Answer

            Below is one way to implement the program. We call ``make_cake`` in ``edit_cake`` and then set the original cake
            equal to the new one.

            .. tb-code:: cpp
               :name: cp_9_AC_5a-support
               :hidden:
               :stdin: test

                void print_cake_info (cake c) {
                    if (c.name == "n/a") {
                        if (c.has_icing) { 
                            cout << "This is a " << c.color << ',' << c.diameter << " inch diameter cake with icing." << '\n';
                        } 
                        else {
                            cout << "This is a " << c.color << ',' << c.diameter << " inch diameter cake without icing." << '\n';
                        }
                    } 
                    else {
                        if (c.has_icing) { 
                            cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes with icing." << '\n';
                        } 
                        else {
                            cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes without icing." << '\n';
                        }
                    } 
                }

                cake make_cake () {
                    cake input;
                    string name, color;
                    double diameter;
                    char icing;
                    cout << "Name: ";
                    cin >> name;
                    input.name = name;
                    cout << "Color: ";
                    cin >> color;
                    input.color = color;
                    cout << "Diameter: ";
                    cin >> diameter;
                    input.diameter = diameter;
                    cout << "Icing? (y/n) ";
                    cin >> icing;
                    if (icing == 'y') {
                        input.has_icing = true;
                    }
                    else {
                        input.has_icing = false; 
                    } 
                    return input;
                }


            .. tb-code:: cpp
               :name: cp_9_AC_5a
               :caption: Example cp_9_AC_5a
               :run-after: cp_9_AC_5a-support
               :stdin: test

               #include <iostream>
               using namespace std;

               struct cake {
                   string name;
                   string color;
                   double diameter;
                   bool has_icing;
               };

               void print_cake_info (cake c);
               cake make_cake ();

               void edit_cake (cake& c) {
                   cake new_cake = make_cake ();
                   c = new_cake;
               }

               int main() {
                   cake original = { "Oops", "orange", 185, true };
                   edit_cake (original);
                   print_cake_info (original);
               }

   .. tb-tab:: Q6

      Write the struct ``shirt``, which has the instance variables color and size.

      .. tb-code:: cpp
         :name: cp_9_AC_6q
         :caption: Example cp_9_AC_6q

         #include <iostream>
         using namespace std;

         // Write your code for the struct shirt here.

         int main () {
             shirt t = { "blue", 'L' };
         }

   .. tb-tab:: Q7

      .. tb-group::
         :name: cp_9_7

         .. tb-tab:: Question

            Write the ``pants`` structure, which has instance variables size and material.

            .. tb-code:: cpp
               :name: cp_9_AC_7q
               :caption: Example cp_9_AC_7q

               #include <iostream>
               using namespace std;

               // Write your code for the struct pants here.

               int main() {
                   pants p = { 'S', "denim" };
               } 


         .. tb-tab:: Answer

            Below is one way to implement the program. We declare the ``pants`` struct and list the instance 
            variables in order.

            .. tb-code:: cpp
               :name: cp_9_AC_7a
               :caption: Example cp_9_AC_7a

               #include <iostream>
               using namespace std;

               struct pants {
                   char size;
                   string material;
               };

               int main() {
                   pants p = { 'S', "denim" };
               } 

   .. tb-tab:: Q8

      Write the struct ``outfit``, which is a nested structure that has a ``shirt``, ``pants``, and has_hat.

      .. tb-code:: cpp
         :name: cp_9_AC_8q
         :caption: Example cp_9_AC_8q

         #include <iostream>
         using namespace std;

         // Write your code for the struct outfit here.

         int main () {
             shirt t = { "blue", 'L' };
             pants p = { 'S', "denim" };
             outfit o = { t, p, true };
         }

   .. tb-tab:: Q9

      .. tb-group::
         :name: cp_9_AC_9q_group

         .. tb-tab:: Question

            Write the ``print_outfit`` function, which prints out details of the outfit.
            The output below should be "shirt: blue and L; pants: S and denim; has hat".

            .. tb-code:: cpp
               :name: cp_9_AC_9q
               :caption: Example cp_9_AC_9q

               #include <iostream>
               using namespace std;

               struct shirt {
                   string color;
                   char size;
               };

               struct pants {
                   char size;
                   string material;
               };

               struct outfit {
                   shirt s;
                   pants p;
                   bool has_hat;
               };

               // Write your code for the print_outfit function here.

               int main() {
                   shirt t = { "blue", 'L' };
                   pants p = { 'S', "denim" };
                   outfit o = { t, p, true };
                   print_outfit (o);
               } 


         .. tb-tab:: Answer

            Below is one way to implement the program. 

            .. tb-code:: cpp
               :name: cp_9_AC_9a
               :caption: Example cp_9_AC_9a

               #include <iostream>
               using namespace std;

               struct shirt {
                   string color;
                   char size;
               };

               struct pants {
                   char size;
                   string material;
               };

               struct outfit {
                   shirt s;
                   pants p;
                   bool has_hat;
               };

               void print_outfit (outfit o) {
               // "shirt: blue and L; pants: S and denim; has hat"
                   cout << "shirt: " << o.s.color << " and " << o.s.size << "; pants:" << o.p.size << " and " << o.p.material << "; ";
                   if (o.has_hat) {
                       cout << "has hat" << '\n';
                   }
                   else {
                       cout << "does not have hat" << '\n';
                   }
               }

               int main() {
                   shirt t = { "blue", 'L' };
                   pants p = { 'S', "denim" };
                   outfit o = { t, p, true };
                   print_outfit (o);
               } 

   .. tb-tab:: Q10

      Write the ``change_shirts`` and ``change_pants`` functions, 
      which both take an ``outfit`` as a parameter. 
      ``change_shirts`` also takes a ``shirt`` as a parameter and 
      ``change_pants`` also takes a ``pants`` as a parameter. 
      Each function modifies the ``outfit``
      and changes the shirt or pants to the new input.

      If you did Q9, then feel free to copy the ``print_outfit`` function
      from there into this program.

      .. tb-code:: cpp
         :name: cp_9_AC_10q
         :caption: Example cp_9_AC_10q

         #include <iostream>
         using namespace std;

         struct shirt {
             string color;
             char size;
         };

         struct pants {
             char size;
             string material;
         };

         struct outfit {
             shirt s;
             pants p;
             bool has_hat;
         };

         // Write your code for the change_shirts function here.

         // Write your code for the change_pants function here.

         int main() {
             shirt t = { "blue", 'L' };
             pants p = { 'S', "denim" };
             outfit o = { t, p, true };
             print_outfit (o);
             shirt new_shirt = { "red", 'M' };
             pants new_pants = { 'M', "khakis" };
             change_shirts (o, new_shirt);
             change_pants (o, new_pants);
             print_outfit (o);
         } 
