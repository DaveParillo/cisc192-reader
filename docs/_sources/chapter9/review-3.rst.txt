Coding Practice
---------------
.. tabbed:: self_check

   .. tab:: Q1

      .. tabbed:: cp_9_1

          .. tab:: Question

              Write the ``Cake`` structure, which has instance variables name, color, diameter, and has_icing.

              .. activecode:: cp_9_AC_1q
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :practice: T

                 #include <iostream>
                 using namespace std;

                 // Write your code for the struct Cake here.

                 int main() {
                     Cake c = { "Mary", "blue", 3.5, false };
                 } 


          .. tab:: Answer

              Below is one way to implement the program. We declare the ``Cake`` struct and list the instance 
              variables in order.

              .. activecode:: cp_9_AC_1a
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :optional:

                 #include <iostream>
                 using namespace std;

                 struct Cake {
                     string name;
                     string color;
                     double diameter;
                     bool has_icing;
                 };

                 int main() {
                     Cake c = { "Mary", "blue", 3.5, false };
                 } 

   .. tab:: Q2

      .. activecode:: cp_9_AC_2q
          :language: cpp
          :compileargs: ['-Wall', '-std=c++11']
          :nocodelens:

          Write the function ``printCakeInfo``, which prints the cake's information in the format
          "This is a ``color``, ``diameter`` inch diameter cake with/without icing." If ``name`` does not
          have the value "n/a", ``printCakeInfo`` prints out "Happy birthdday ``name``! Your cake is ``color``,
          has a ``diameter`` inch diameter, and comes with/without icing."
          ~~~~
          #include <iostream>
          using namespace std;

          struct Cake {
              string name;
              string color;
              double diameter;
              bool has_icing;
          };

          // Write your code for the printCakeInfo function here.

          int main() {
              Cake c1 = { "n/a", "red", 12.5, true };
              printCakeInfo (c1);
              Cake c2 = { "Tom", "white", 10, false };
              printCakeInfo (c2);
          }

   .. tab:: Q3

      .. tabbed:: cp_9_3

          .. tab:: Question

              Write the ``makeCake`` function, which prompts the user for a name,
              color, diameter, and whether or not they want icing. The function then
              returns the cake.

              .. activecode:: cp_9_AC_3q
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :stdin: test

                 #include <iostream>
                 using namespace std;

                 struct Cake {
                     string name;
                     string color;
                     double diameter;
                     bool has_icing;
                 };

                 void printCakeInfo (Cake c);

                 // Write your code for the makeCake function here.

                 int main() {
                     Cake input = makeCake ();
                     printCakeInfo (input);
                 }
                 ====
                 void printCakeInfo (Cake c) {
                     if (c.name == "n/a") {
                         if (c.has_icing) { 
                             cout << "This is a " << c.color << "," << c.diameter << " inch diameter cake with icing." << endl;
                         } 
                         else {
                             cout << "This is a " << c.color << "," << c.diameter << " inch diameter cake without icing." << endl;
                         }
                     } 
                     else {
                         if (c.has_icing) { 
                             cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes with icing." << endl;
                         } 
                         else {
                             cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes without icing." << endl;
                         }
                     } 
                 }


          .. tab:: Answer

              Below is one way to implement the program. We create a ``Cake`` for the user, read in the user's input using cin, and return the ``Cake``.

              .. activecode:: cp_9_AC_3a
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :optional:
                 :stdin: test

                 #include <iostream>
                 using namespace std;

                 struct Cake {
                     string name;
                     string color;
                     double diameter;
                     bool has_icing;
                 };

                 void printCakeInfo (Cake c);

                 Cake makeCake () {
                     Cake input;
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
                     Cake input = makeCake ();
                     printCakeInfo (input);
                 }
                 ====
                 void printCakeInfo (Cake c) {
                     if (c.name == "n/a") {
                         if (c.has_icing) { 
                             cout << "This is a " << c.color << "," << c.diameter << " inch diameter cake with icing." << endl;
                         } 
                         else {
                             cout << "This is a " << c.color << "," << c.diameter << " inch diameter cake without icing." << endl;
                         }
                     } 
                     else {
                         if (c.has_icing) { 
                             cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes with icing." << endl;
                         } 
                         else {
                             cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes without icing." << endl;
                         }
                     } 
                 }

   .. tab:: Q4

      .. activecode:: cp_9_AC_4q
          :language: cpp
          :compileargs: ['-Wall', '-std=c++11']
          :nocodelens:

          Write the function ``changeCakeDiameter``, which takes a ``Cake`` and a ``double`` as a parameter. 
          ``changeCakeDiameter`` then multiplies the original diameter by the double and modifies the cake
          to have this new diameter.
          ~~~~
          #include <iostream>
          using namespace std;

          struct Cake {
              string name;
              string color;
              double diameter;
              bool has_icing;
          };

          void printCakeInfo (Cake c);
          Cake makeCake ();

          // Write your code for the changeCakeDiameter function here.

          int main() {
              Cake original = { "John", "green", 8.5, true };
              changeCakeDiameter (original, 2);
              printCakeInfo (original);
          }
          ====
          void printCakeInfo (Cake c) {
              if (c.name == "n/a") {
                  if (c.has_icing) { 
                      cout << "This is a " << c.color << "," << c.diameter << " inch diameter cake with icing." << endl;
                  } 
                  else {
                      cout << "This is a " << c.color << "," << c.diameter << " inch diameter cake without icing." << endl;
                  }
              } 
              else {
                  if (c.has_icing) { 
                      cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes with icing." << endl;
                  } 
                  else {
                      cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes without icing." << endl;
                  }
              } 
          }

          Cake makeCake () {
              Cake input;
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

   .. tab:: Q5

      .. tabbed:: cp_9_5

          .. tab:: Question

              Write the ``editCake`` function, which prompts the user for a new name,
              color, diameter, and whether or not they want icing. The function modifies 
              the original cake that is passed in as a parameter. Use the makeCake function 
              in your implementation to avoid duplicate code!

              .. activecode:: cp_9_AC_5q
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :stdin: test

                 #include <iostream>
                 using namespace std;

                 struct Cake {
                     string name;
                     string color;
                     double diameter;
                     bool has_icing;
                 };

                 void printCakeInfo (Cake c);
                 Cake makeCake ();

                 // Write your code for the editCake function here.

                 int main() {
                     Cake original = { "Oops", "orange", 185, true };
                     editCake (original);
                     printCakeInfo (original);
                 }
                 ====
                  void printCakeInfo (Cake c) {
                      if (c.name == "n/a") {
                          if (c.has_icing) { 
                              cout << "This is a " << c.color << "," << c.diameter << " inch diameter cake with icing." << endl;
                          } 
                          else {
                              cout << "This is a " << c.color << "," << c.diameter << " inch diameter cake without icing." << endl;
                          }
                      } 
                      else {
                          if (c.has_icing) { 
                              cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes with icing." << endl;
                          } 
                          else {
                              cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes without icing." << endl;
                          }
                      } 
                  }

                  Cake makeCake () {
                      Cake input;
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


          .. tab:: Answer

              Below is one way to implement the program. We call ``makeCake`` in ``editCake`` and then set the original cake
              equal to the new one.

              .. activecode:: cp_9_AC_5a
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :optional:
                 :stdin: test

                 #include <iostream>
                 using namespace std;

                 struct Cake {
                     string name;
                     string color;
                     double diameter;
                     bool has_icing;
                 };

                 void printCakeInfo (Cake c);
                 Cake makeCake ();

                 void editCake (Cake& c) {
                     Cake newCake = makeCake ();
                     c = newCake;
                 }

                 int main() {
                     Cake original = { "Oops", "orange", 185, true };
                     editCake (original);
                     printCakeInfo (original);
                 }
                 ====
                  void printCakeInfo (Cake c) {
                      if (c.name == "n/a") {
                          if (c.has_icing) { 
                              cout << "This is a " << c.color << "," << c.diameter << " inch diameter cake with icing." << endl;
                          } 
                          else {
                              cout << "This is a " << c.color << "," << c.diameter << " inch diameter cake without icing." << endl;
                          }
                      } 
                      else {
                          if (c.has_icing) { 
                              cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes with icing." << endl;
                          } 
                          else {
                              cout << "Happy birthday " << c.name << "! Your cake is " << c.color << ", has a " << c.diameter << " inch diameter, and comes without icing." << endl;
                          }
                      } 
                  }

                  Cake makeCake () {
                      Cake input;
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

   .. tab:: Q6

      .. activecode:: cp_9_AC_6q
          :language: cpp
          :compileargs: ['-Wall', '-std=c++11']
          :nocodelens:

          Write the struct ``Shirt``, which has the instance variables color and size.
          ~~~~
          #include <iostream>
          using namespace std;

          // Write your code for the struct Shirt here.

          int main () {
              Shirt t = { "blue", 'L' };
          }

   .. tab:: Q7

      .. tabbed:: cp_9_7

          .. tab:: Question

              Write the ``Pants`` structure, which has instance variables size and material.

              .. activecode:: cp_9_AC_7q
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :practice: T

                 #include <iostream>
                 using namespace std;

                 // Write your code for the struct Pants here.

                 int main() {
                     Pants p = { 'S', "denim" };
                 } 


          .. tab:: Answer

              Below is one way to implement the program. We declare the ``Pants`` struct and list the instance 
              variables in order.

              .. activecode:: cp_9_AC_7a
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :optional:

                 #include <iostream>
                 using namespace std;

                 struct Pants {
                     char size;
                     string material;
                 };

                 int main() {
                     Pants p = { 'S', "denim" };
                 } 

   .. tab:: Q8

      .. activecode:: cp_9_AC_8q
          :language: cpp
          :compileargs: ['-Wall', '-std=c++11']
          :nocodelens:

          Write the struct ``Outfit``, which is a nested structure that has a ``Shirt``, ``Pants``, and has_hat.
          ~~~~
          #include <iostream>
          using namespace std;

          // Write your code for the struct Outfit here.

          int main () {
              Shirt t = { "blue", 'L' };
              Pants p = { 'S', "denim" };
              Outfit o = { t, p, true };
          }

   .. tab:: Q9

      .. tabbed:: cp_9_AC_9q

          .. tab:: Question

              Write the ``printOutfit`` function, which prints out details of the outfit.
              The output below should be "Shirt: blue and L; Pants: S and denim; has hat".

              .. activecode:: cp_9_AC_9q
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :practice: T

                 #include <iostream>
                 using namespace std;

                 struct Shirt {
                     string color;
                     char size;
                 };

                 struct Pants {
                     char size;
                     string material;
                 };

                 struct Outfit {
                     Shirt s;
                     Pants p;
                     bool has_hat;
                 };

                 // Write your code for the printOutfit function here.

                 int main() {
                     Shirt t = { "blue", 'L' };
                     Pants p = { 'S', "denim" };
                     Outfit o = { t, p, true };
                     printOutfit (o);
                 } 


          .. tab:: Answer

              Below is one way to implement the program. 

              .. activecode:: cp_9_AC_9a
                 :language: cpp
                 :compileargs: ['-Wall', '-std=c++11']
                 :nocodelens:
                 :optional:

                 #include <iostream>
                 using namespace std;

                 struct Shirt {
                     string color;
                     char size;
                 };

                 struct Pants {
                     char size;
                     string material;
                 };

                 struct Outfit {
                     Shirt s;
                     Pants p;
                     bool has_hat;
                 };

                 void printOutfit (Outfit o) {
                 // "Shirt: blue and L; Pants: S and denim; has hat"
                     cout << "Shirt: " << o.s.color << " and " << o.s.size << "; Pants:" << o.p.size << " and " << o.p.material << "; ";
                     if (o.has_hat) {
                         cout << "has hat" << endl;
                     }
                     else {
                         cout << "does not have hat" << endl;
                     }
                 }

                 int main() {
                     Shirt t = { "blue", 'L' };
                     Pants p = { 'S', "denim" };
                     Outfit o = { t, p, true };
                     printOutfit (o);
                 } 

   .. tab:: Q10

      .. activecode:: cp_9_AC_10q
          :language: cpp
          :compileargs: ['-Wall', '-std=c++11']
          :nocodelens:

          Write the ``changeShirts`` and ``changePants`` functions, 
          which both take an ``Outfit`` as a parameter. 
          ``changeShirts`` also takes a ``Shirt`` as a parameter and 
          ``changePants`` also takes a ``Pants`` as a parameter. 
          Each function modifies the ``Outfit``
          and changes the shirt or pants to the new input.

          If you did Q9, then feel free to copy the ``printOutfit`` function
          from there into this program.
          ~~~~
          #include <iostream>
          using namespace std;

          struct Shirt {
              string color;
              char size;
          };

          struct Pants {
              char size;
              string material;
          };

          struct Outfit {
              Shirt s;
              Pants p;
              bool has_hat;
          };

          // Write your code for the changeShirts function here.

          // Write your code for the changePants function here.

          int main() {
              Shirt t = { "blue", 'L' };
              Pants p = { 'S', "denim" };
              Outfit o = { t, p, true };
              printOutfit (o);
              Shirt newShirt = { "red", 'M' };
              Pants newPants = { 'M', "khakis" };
              changeShirts (o, newShirt);
              changePants (o, newPants);
              printOutfit (o);
          } 

