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
              using namespace std;

              int main() {
                double GPA = 3.52;
                int updatedGPA = int(GPA);
                cout << "GPA: " << updatedGPA;
              }

          -   ``3.0``

              -   Its correct to think that your GPA will be rounded down, but what 
                  else happens when you convert from ``int`` to ``double``?

          -   ``3``

              +   Converting to an ``int`` always rounds down to the nearest integer, so I do not 
                  recommend using type conversions to build your resume... especially if you're 
                  close to ``4.0``.

          -   ``4.0``

              -   Converting to an int *will* round your GPA, but not in the direction
                  that you were hoping for... what else happens when you convert from
                  ``int`` to ``double``?

          -   ``4``

              -   Converting to an int *will* round yor GPA, but not in the direction
                  that you were hoping for.

          -   Error!

              -   No errors here! Type conversions are perfectly legal in C++!

   .. tab:: Q2

      .. mchoice:: functions_mc2

          What is the value of x after the program executes?

          ::

              #include <iostream>
              using namespace std;

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

              #include <iostream>
              using namespace std;

              int main() {
                int a = 1.5;
                double b = a + 1.5;
                double c = 2.4;
                double d = 1/5;
                int e = c * c;
                double f = int(c);
              }

          -   ``a``

              -   C++ performs automatic type conversion to round 1.5 down to the 
                  nearest integer.

          -   ``b``

              +   Since ``a = 1``, we know that ``b = 2.5``, which is a non-zero decimal.

          -   ``c``

              +   ``c`` is a ``double`` and has a non-zero decimal.

          -   ``d``

              -   C++ performs integer division to round ``1/5`` down to the nearest
                  integer.  The value will be stored as ``0``, not ``0.2``.

          -   ``e``

              -   ``c`` squared may have a non-zero decimal, but automatic type conversion
                  will round it down to the nearest integer before storing the value in ``e``.
          
          -   ``f``

              -   ``int(c)`` rounds ``c`` down to the nearest integer before storing the 
                  value in ``f``. 

   .. tab:: Q4

      .. mchoice:: functions_mc4

          **Multiple Response** Which of the following would work as a function header
          (first line of a function).

          -   ``printHelloWorld () {``

              -   This function header is missing a type.

          -   ``string palindrome (word) {``

              -   The function's parameter is missing a type.

          -   ``int mult (int a, int b) {``

              +   Correct! The function header has a type, empty parentheses, and
                  a squiggly bracket.

          -   ``char shiftThree (char letter)``

              -   This function header is missing a squiggly bracket ``{``.

          -   ``void giveCompliment () {``

              +   Correct! The function header has a type, empty parentheses, and
                  a squiggly bracket.
          
          -   ``string friend (string name) {``

              -   ``friend`` is a reserved keyword in C++.


   .. tab:: Q5

      .. mchoice:: functions_mc5

          What is printed when the following code runs?  Are there any errors?

          ::

              #include <iostream>
              using namespace std;

              void giveCompliment () {
                  cout << "You are awesome!";
              }

              void giveInsult () {
                  insult = "You suck!";
              }

              int main () {
                  giveInsult ();
              }

          -   ``"You are awesome!"``

              -   The ``giveCompliment`` function is not called in ``main``.

          -   ``"You suck!"``

              -   The ``giveInsult`` function doesn't ``cout`` anything.

          -   Nothing is printed.

              +   Correct!  ``giveInsult`` doesn't ``cout`` anything.

          -   Error!

              -   There are no errors with this program!


   .. tab:: Q6

      .. mchoice:: functions_mc6

          Rachel and Monica are best friends.  They write a function
          called ``bestFriends`` so that they announce this fact to the 
          rest of their friends.  What is printed when they run the code 
          below? Are there any errors?

          ::

              #include <iostream>
              using namespace std;

              void bestFriends (string a, string b) {
                  cout << a << " is best friends with " << b;
              }

              int main () {
                  string a = "Rachel";
                  string b = "Monica";
                  bestFriends(b, a);
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
              using namespace std;

              void greeting (string name) {
                  cout << "hello, " << name << "!";
              }

              void goodbye (string name) {
                  greeting (name);
                  cout << "!!";
              }

              int main () {
                  string hannah = "Hannah";
                  string anna = "Anna";
                  string louise = hannah;
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
          calls of ``orderFood``?

          ::

              #include <iostream>
              using namespace std;

              void orderFood (string food, int quantity) {
                  cout << "I'll have " << quantity << " " << food;
              }

              int main () {
                  string a = "wings";
                  string b = "sliders";
                  int c = 3;
                  double d = 8.64;
                  char e = 'p';
              }

          -   ``orderFood(a, c);``

              +   Correct! ``a`` is a string and ``c`` is an int.

          -   ``orderFood(b, d);``

              +   Correct!  Automatic type conversion will convert d to
                  an ``int``.

          -   ``orderFood(e, c);``

              -   ``e`` has a character value, and this function takes a *string*.

          -   ``orderfood(a, d);``

              +   Correct! Automatic type conversion will convert d to
                  an ``int``.

          -   ``orderFood(c, a);``

              -   You have to input your arguments in the correct order.


   .. tab:: Q9

      .. mchoice:: functions_mc9

          What is printed when the following code runs?  Are there any errors?

          ::

              #include <iostream>
              using namespace std;

              void printWord (string w) {
                  cout << w << w;
              }

              int main () {
                  char a = 'a' + 5;
                  printWord (a);
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

              +   ``printWord`` takes a string, not a character, as an argument.


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
                  if(available==true){
                     party(21,"Big house"); party(22,"CCTC");
                  }

                  else{
                     cout<<"sorry I have to study for ENGR101!"<<endl;
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
