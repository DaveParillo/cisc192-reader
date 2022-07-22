Multiple Choice Exercises
-------------------------

Answer the following **Multiple Choice** questions to
assess what you have learned in this chapter.

.. tabbed:: tab_check

   .. tab:: Q1

      .. mchoice:: functions_mc1

          You want to spice up your resume before the career fair, so you decide to
          update your GPA using the program below. What is the GPA that you will 
          have on display for future employers?

          ::

              #include <iostream>

              int main() {
                double gpa = 3.52;
                int updated_gpa = int(gpa);
                std::cout << "GPA: " << updated_gpa;
              }

          -   ``3.0``

              -   Its correct to think that your GPA will be truncated, but what 
                  else happens when you convert from ``int`` to ``double``?

          -   ``3``

              +   Converting to an ``int`` always truncates, so I do not 
                  recommend using type conversions to build your resume... especially if you're 
                  close to ``4.0``.

          -   ``4.0``

              -   Converting to an int *will* change your GPA, but not in the direction
                  that you were hoping for... what else happens when you convert from
                  ``int`` to ``double``?

          -   ``4``

              -   Converting to an int *will* change yor GPA, but not in the direction
                  that you were hoping for.

          -   Error!

              -   No errors here! Type conversions are perfectly legal in C++!

   .. tab:: Q2

      .. mchoice:: functions_mc2

          What is the value of x after the program executes?

          ::

              #include <iostream>

              int main() {
                int x = acos(-1);
              }

          -   3.14159265358979323846

              -   If ``x`` were a double, C++ would automatically round the value
                  of pi to **15** decimal places.

          -   3.142

              -   If ``x`` were a double, C++ would automatically round the value
                  of pi to **15** decimal places.

          -   3.0

              -   Automatic type conversion will round the value of pi down to the
                  nearest integer, but what else happens when we convert a ``double``
                  to an ``int``?

          -   3

              -   The value of x *should* be 3, since automatic type conversion will
                  round the value of pi down to the nearest integer.

          -   Error!

              +   Whenever we use math functions, we must include the ``<cmath>`` header file.

   .. tab:: Q3

      .. mchoice:: functions_mc3

          **Multiple Response** Select all variables that have a *non-zero* value after the decimal place.
          (3.1 has a *non-zero* value, while 3.0 does not)

          ::

              int main() {
                int a = 1.5;
                double b = a + 1.5;
                double c = 2.4;
                double d = 1/5;
                int e = c * c;
                double f = int(c);
              }

          -   ``a``

              -   C++ performs automatic type conversion to truncate 1.5 to 1. 

          -   ``b``

              +   Since ``a = 1``, we know that ``b = 2.5``, which is a non-zero decimal.

          -   ``c``

              +   ``c`` is a ``double`` and has a non-zero decimal.

          -   ``d``

              -   C++ performs integer division which truncates ``1/5``.
                  The value will be stored as ``0``, not ``0.2``.

          -   ``e``

              -   ``c`` squared may have a non-zero decimal,
                  but automatic type conversion will truncate it before
                  storing the value in ``e``.
          
          -   ``f``

              -   ``int(c)`` truncates ``c`` before storing the value in ``f``.

   .. tab:: Q4

      .. mchoice:: functions_mc4

          **Multiple Response** Which of the following would work as the
          first line of a function definition?

          -   ``print_hellow_world () {``

              -   This declaration is missing a type.

          -   ``string palindrome (word) {``

              -   The function's parameter is missing a type.

          -   ``int mult (int a, int b) {``

              +   Correct! The declaration has a type, empty parentheses, and
                  an open curly brace.

          -   ``char shift_three (char letter)``

              -   This declaration is missing an open curly brace ``{``.

          -   ``void give_compliment () {``

              +   Correct! The declaration has a type, empty parentheses, and
                  an open curly brace.
          
          -   ``string friend (string name) {``

              -   ``friend`` is a reserved keyword in C++.


   .. tab:: Q5

      .. mchoice:: functions_mc5

          What is printed when the following code runs?  Are there any errors?

          ::

              #include <iostream>
              using namespace std;

              void give_compliment () {
                  cout << "You are awesome!";
              }

              void give_insult () {
                  insult = "You suck!";
              }

              int main () {
                  give_insult ();
              }

          -   ``"You are awesome!"``

              -   The ``give_compliment`` function is not called in ``main``.

          -   ``"You suck!"``

              -   The ``give_insult`` function doesn't ``cout`` anything.

          -   Nothing is printed.

              +   Correct!  ``give_insult`` doesn't ``cout`` anything.

          -   Error!

              -   There are no errors with this program!


   .. tab:: Q6

      .. mchoice:: functions_mc6

          Rachel and Monica are best friends.  They write a function
          called ``best_friends`` so that they announce this fact to the 
          rest of their friends.  What is printed when they run the code 
          below? Are there any errors?

          ::

              #include <iostream>
              #include <string>

              void best_friends (string a, string b) {
                  std::cout << a << " is best friends with " << b;
              }

              int main () {
                  std::string a = "Rachel";
                  std::string b = "Monica";
                  best_friends(b, a);
              }

          -   ``"Monica is best friends with Rachel"``

              +   Correct!  Although the function definition has ``a << " is best 
                  friends with " << b``, we call the function with variable ``b``
                  as argument ``a`` and variable ``a`` as argument ``b``.

          -   ``"Rachel is best friends with Monica"``

              -   You seem to be confusing your arguments and parameters!

          -   ``a is best friends with b``

              -   The function ``couts`` the *values* of the variables, not their
                  names!

          -   ``b is best friends with a``

              -   The function ``couts`` the *values* of the variables, not their
                  names!

          -   Error!

              -   There are no errors with this program!


   .. tab:: Q7

      .. mchoice:: functions_mc7

          What is printed when the following code runs?  Are there any errors?

          ::

              #include <iostream>
              #include <string>

              void greeting (string name) {
                  std::cout << "hello, " << name << "!";
              }

              void goodbye (string name) {
                  greeting (name);
                  std::cout << "!!";
              }

              int main () {
                  std::string hannah = "Hannah";
                  std::string anna = "Anna";
                  std::string louise = hannah;
                  hannah = anna;
                  anna = louise;
                  goodbye (anna);
              }

          -   ``hello, Hannah!!!``

              +   Correct!  The string "Hannah" is assigned to the variable ``louise``,
                  then the value of ``louise`` is assigned to the variable ``anna``.  When
                  ``goodbye (anna)`` runs, ``anna`` has the value "Hannah".

          -   ``hello, anna!!!``

              -   The function ``couts`` the *value* of the variable ``anna`` not
                  the variable name!

          -   ``hello, Anna!!!``

              -   Is ``"Anna"`` still the value of ``anna``?

          -   ``hello, Louise!``

              -   The ``goodbye`` function adds extra exclamation points.

          -   ``hello, Louise!!!``

              -   We assigned the value of ``louise`` to ``anna``.  Is ``"Louise"``
                  the value of ``louise``?

          -   Error!

              -   There are no errors with this program!


   .. tab:: Q8

      .. mchoice:: functions_mc8

          **Multiple Response** Which of the following are legal function
          calls of ``order_food``?

          ::

              #include <iostream>
              #include <string>
              using namespace std;

              void order_food (string food, int quantity) {
                  cout << "I'll have " << quantity << " " << food;
              }

              int main () {
                  string a = "wings";
                  string b = "sliders";
                  int c = 3;
                  double d = 8.64;
                  char e = 'p';
              }

          -   ``order_food(a, c);``

              +   Correct! ``a`` is a string and ``c`` is an int.

          -   ``order_food(b, d);``

              +   Correct!  Automatic type conversion will convert d to
                  an ``int``.

          -   ``order_food(e, c);``

              -   ``e`` has a character value, and this function takes a *string*.

          -   ``order_food(a, d);``

              +   Correct! Automatic type conversion will convert d to
                  an ``int``.

          -   ``order_food(c, a);``

              -   You have to input your arguments in the correct order.


   .. tab:: Q9

      .. mchoice:: functions_mc9

          What is printed when the following code runs?  Are there any errors?

          ::

              #include <iostream>
              #include <string>
              using namespace std;

              void print (string w) {
                  cout << w << w;
              }

              int main () {
                  char a = 'a' + 5;
                  print (a);
              }

          -   ``a``

              -   ``'a'`` is no longer the value of ``a``, and the function would
                  print it more than once.  Hint: think about the *type* of ``a``.

          -   ``f``

              -   ``'f'`` is the value of a, but the function would print it more than once.  
                  Hint: think about the *type* of ``a``.

          -   ``aa``

              -   ``'a'`` is no longer the value of ``a``.  Hint: think about the *type* of ``a``.

          -   ``ff``

              -   Hint: think about the *type* of ``a``.


          -   Error!

              +   ``print`` takes a string, not a character, as an argument.


   .. tab:: Q10

      .. mchoice:: functions_mc10

          How many local variables and parameters does ``mult`` have?

          ::

              void mult (int a, int b, int c) {
                  int d = 7;
                  cout << a * b * c * d;
              }

          -   1 parameter, 3 local variables

              -   Remember, the parameters are declared in the function definition,
                  and the local variables are declared *inside* of the function.

          -   2 parameters, 4 local variables

              -   You can declare multiple variables at once!  Also, remember that
                  local variables are declared *inside* of the function.

          -   2 parameters, 1 local variables

              -   You can declare multiple variables at once!

          -   3 parameters, 1 local variable

              +   ``a``, ``b``, and ``c`` are parameters declared in the function
                  definition. ``d`` is a local variable declared inside of the function.

          -   3 parameters, 4 local variables

              -   Remember that local variables are declared *inside* of the function.

   .. tab:: Q11

      .. mchoice:: functions_mc11

          How many calls are made to ``party`` during the entire program?

          ::

              void party (int day_of_month, string address) {
                  cout <<"party on "<<day_of_month<<" at "<<address<<endl;
              }

              void weekend(bool available){
                  if(available) {
                     party(21,"Big house"); party(22,"CCTC");
                  } else {
                     cout<<"sorry I have to study for ENGR101!\n";
                  }
              }

              int main(){
                  bool im_free=false;
                  party(25,"North campus");
                  weekend(im_free);

                  im_free=true;
                  party(25,"Central campus");
                  weekend(im_free);
                  return 0;
              }
              
          -   6 calls

              -   Take into account that ``weekend`` only calls ``party`` if a conditional is true!

          -   2 calls

              -   ``weekend`` can also call the function ``party``

          -   4 calls

              +  Correct! two calls by ``main`` and two calls by ``weekend``

          -   3 calls

              -  One invocation of ``weekend`` calls ``party`` twice.
