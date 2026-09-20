.. _variables-types-multiple-choice-exercises:

Multiple Choice Exercises
-------------------------

Answer the following **Multiple Choice** questions to assess what you have learned in this chapter.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: VARS_mc1

         Take a look at the following program.  How many lines of output will be produced?

         ::

             int main() {
               int hour = 7;
               int min = 50;
               cout << "The current time is: " << '\n';
               cout << hour;
               cout << ':';  cout << minute;
               cout << '\n';
               cout << "I'm going to be late for my 8am!";
             }

         - [ ] 6

           -   There *are* 6 ``cout`` statements, but that doesn't mean there are 6 lines of output!

         - [ ] 5

           -   There *are* 5 lines of ``cout`` statments, but that doesn't mean there are 5 lines of output!

         - [x] 3

           +   Even though there are 6 ``cout`` staments written on 5 lines, there are only 3 lines of output in the terminal.

         - [ ] 2

           -   There *are* 2 ``endl`` statements.  But what happens when you have more output after the ``endl``?

         - [ ] 0! There is an error!

           -   Everything is syntacticly legal! You can have ``cout`` statements on *multiple lines of code* that have *one* line of output... or you can have multiple ``cout`` statements on *one* line of code that have *multiple* lines of output!


   .. tb-tab:: Q2

      .. tb-choice::
         :name: VARS_mc2

         What is the type of x?

         ::

             x = "3";

         - [ ] integer

           -   ``1`` is an integer.

         - [ ] double

           -   ``1.0`` is a double.

         - [ ] character

           -   ``'1'`` is a character.

         - [x] string

           +   Anything in double quotes is a string.


   .. tb-tab:: Q3

      .. tb-choice::
         :name: VARS_mc3

         What is the value of ``x``?

         ::

             x = 2 + (13 - 5) * 2 + 6 /3;

         - [ ] 7

           -   ``13 - 5`` is computed first because it is in parentheses.

         - [x] 20

           +   C++ follows the order of operations.

         - [ ] 23.333

           -   ``2 + 6`` is not grouped together like ``13 - 5``.

         - [ ] 34

           -   ``2 + 6 / 3`` is not computed first.


   .. tb-tab:: Q4

      .. tb-choice::
         :name: VARS_mc4

         What is printed when the following code is run?

         ::

             int main() {
               int x;
               int y = 2;
               int z = 4;
               x = z;
               z = 6;
               y = x + z;
               cout << y + z;
             }

         - [ ] ``6``

           -   The variables ``y`` and ``z`` have been re-assigned.

         - [ ] ``10``

           -   This would be correct if we had written ``cout << x + z``.

         - [x] ``16``

           +   Walking through each line of code and keeping track of variables, like you just did, is called **tracing**.

         - [ ] ``yz``

           -   If y and z were characters ``'y'`` and ``'z'``, it would be legal to add them together.  But the result ``243`` might surprise you!


   .. tb-tab:: Q5

      .. tb-choice::
         :name: VARS_mc5

         **Multiple Response** What could be changed so that the output of the following program is ``34``?

         .. code-block:: 
            :linenos:

            int main() {
              char c;
              int d;
              c = "3";
              d = 4;
              cout << c; cout << d;
            }

         - [ ] ``c`` should be declared as an int.

           -   This will still result in an error.

         - [x] ``c`` should be declared as a string.

           +   This clears up the type mismatch on line 4.

         - [ ] ``d`` should be declared as a char.

           -   Although the code will still run, it won't give correct output.

         - [ ] Line 4 should be replaced with ``c = 3``

           -   Although the code will still run, it won't give correct output.

         - [x] Line 4 should be replaced with ``c = '3'``

           +   This clears up the type mismatch on line 4.


   .. tb-tab:: Q6

      .. tb-choice::
         :name: VARS_mc6

         What is the output of the following code block?

         ::

            int main() {
              string apples;
              apples = "bananas";
              string pineapple;
              string mango = "mango";
              pineapple = apples;         
              cout << "My favorite fruit is ";
              cout << pineapple << '\n';
              pineapple = mango;
            }

         - [ ] ``My favorite fruit is pineapple``

           -   ``pineapple`` is the name of the variable, but it's not necessarily
               the value of that variable.

         - [x] ``My favorite fruit is bananas``

           +   ``pineapple = apples``, and ``apples = "bananas"``.

         - [ ] ``My favorite fruit is apples``

           -   ``pineapple = apples``, but what does ``apples`` equal?

         - [ ] ``My favorite fruit is mango``

           -   ``"mango"`` is the value of the variable ``pineapple`` at the end of
               ``main``, but not at the line of the ``cout``.

         - [ ] Compile error.

           -   There are no syntax errors that will cause an issue compiling.


   .. tb-tab:: Q7

      .. tb-choice::
         :name: VARS_mc7

         What line does the first error occur in the following program? If there is no error, what is the output?

         .. code-block:: 
            :linenos:

            int main() {
              string tom = "Tom";
              string friend = "Jerry";
              cout << tom;
              cout << "is friends with"; cout << friend;
            }

         - [ ] line 2, a variable cannot have the same name as its value

           -   A variable can have any value... as long as the types are the same.

         - [x] line 3, you cannot have a variable named friend

           +   ``friend`` is a reserved keyword in C++ and can't be used as a variable name.  What a shame, since Tom and Jerry are the best of friends!

         - [ ] line 5, you cannot have two statements on the same line

           -   You can have as many statements as you want on one line, as long as you terminate each one with a semicolon.

         - [ ] No error, ``Tom is friends with Jerry``

           -   If the code runs, C++ doesn't automatically add spaces between consecutive strings.

         - [ ] No error, ``Tomis friends with_jerry``

           -   If the error was corrected, this would be the output. Unfortunately, there is an error that prevents this line from executing.


   .. tb-tab:: Q8

      .. tb-choice::
         :name: VARS_mc8

         Your math teacher just gave an exam that had all of the students panicking.  Four students decide to share their scores to see who did the best.  At the end of the program's execution, who has the highest score on the exam?

         ::

            int main() {
              int Regina = 6 * (3 + 2) / 100;
              int Gretchen = (3 + 5) * 6 / 100;
              int Karen =  6 * 3 + 2 / 100;
              int Cady = (3 * 5) * 6 / 100;
            }

         - [ ] Regina

           -   Using the order of operations we have Regina scoring 30 / 100.

         - [ ] Gretchen

           -   Using the order of operations we have Gretchen scoring 48 / 100.

         - [x] Karen

           +   ``6 * 3 = 18``, and ``18 + 2 / 100 = 18`` due to integer division. Believe it or not, due to the order of operations and integer division, Karen ended up with the highest "score" at the end of the program's execution.

         - [ ] Cady

           -   Using the order of operations we have Mathlete Cady scoring 90 / 100. this would be the highest score... if it weren't for integer division.

         - [ ] They all got 0's.

           -   Integer division rounds the quotient down to the nearest integer. Take a closer look at what is being divided on each line, because not everyone recieved a zero!


   .. tb-tab:: Q9

      .. tb-choice::
         :name: VARS_mc9

         What line does the first error occur in the following program? If there is no error, what is the output?

         .. code-block:: 
            :linenos:

            int main() {
              char r = 'r';
              int x = 3;
              r = r + x;
              cout << r;
            }

         - [ ] line 2, a variable cannot have the same name as its value

           -   A variable can have any value... as long as the types are the same.

         - [ ] line 4, you cannot add an integer to a character

           -   Actually, C++ supports character operations!  This is legal.

         - [ ] No error, ``rx``

           -   ``x`` is an integer, so what we really have is ``r = r + 3``.

         - [ ] No error, ``r``

           -   ``'r'`` isn't necessarily the value of ``r``.  Take a look at line 4.

         - [x] No error, ``u``

           +   'u' is three letters after 'r', so on line 4, the value of ``u`` becomes the value of ``r``.



   .. tb-tab:: Q10

      .. tb-choice::
         :name: VARS_mc10

         Say you run the following code.  What is the value of ``mod``?

         ::

             int x = 4;
             int y = 7;
             int mod = y % x;

         - [ ] 0

           -   There *is* a remainder.

         - [ ] 1

           -   Incorrect!

         - [ ] 2

           -   Incorrect!

         - [x] 3

           +   The remainder of ``7 / 4`` is 3.

         - [ ] 4

           -   We can't have a remainder of 4, since 4 is the divisor.

   .. tb-tab:: Q11

      .. tb-choice::
         :name: VARS_mc11

         Suppose you want to find the volume of a cone.
         For reference, the formula is :math:`V = \frac{1}{3}\pi \cdot r^2 \cdot h`.
         For the sake of this question, we will use :math:`\pi = 3.14`.
         What is wrong with the following code?

         ::

            double r = 4.5;
            double h = 12;
            double volume = 1/3 * 3.14 * r * r * h;

         - [x] semantic error

           +   With integer division, ``1 / 3`` becomes 0.  Multiplying 0 by the rest of the expression will always return 0, which is not what you want your program to do!

         - [ ] syntax error

           -   There is nothing wrong with the structure of your program.

         - [ ] run-time error

           -   There are no errors that will surface at run-time.

         - [ ] You can't calculate and return on the same line!

           -   You actually can, this is called composition.

         - [ ] Nothing!  There is not an error.

           -   This formula will return a volume, but is it correct?

