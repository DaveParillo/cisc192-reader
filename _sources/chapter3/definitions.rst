Definitions and Uses
--------------------

Pulling together all the code fragments from the previous section, the
whole program looks like this:

::

    #include <iostream>
    using std::cout;
    using std::endl;

    void new_line () {
      cout << endl;
    }

    void three_line () {
      new_line ();  new_line ();  new_line ();
    }

    int main () {
      cout << "First Line." << endl;
      three_line ();
      cout << "Second Line." << endl;
      return 0;
    }

This program contains three function definitions: ``new_line``, ``three_line``,
and ``main``.

Inside the definition of ``main``, there is a statement that uses or calls
``three_line``. Similarly, ``three_line`` calls ``new_line`` three times. Notice that
the definition of each function appears above the place where it is
used.

This is necessary in C++; the definition of a function must appear
before (above) the first use of the function. 


.. admonition:: Try This!

   You should try compiling this program with the functions in 
   a different order and see what error messages you get.


.. tabbed:: tab_check

   .. tab:: Q1

      .. fillintheblank:: defns_uses_1

         The function definition must be written |blank| the first use of the function.
          
         - :([Bb][Ee][Ff][Oo][Rr][Ee])|([Aa][Bb][Oo][Vv][Ee]): Correct!
           :.*: Try again!


   .. tab:: Q2

      .. mchoice::  defns_uses_2

          Which of the following is a correct function header (first line of 
          a function definition)?

          -   ``void printName()``

              -   This function header is missing a ``{``, which is needed to begin defining the function.

          -   ``totalCostAfterTax () {``

              -   This function header is missing a return type.

          -   ``void todaysWeather () {``

              +   Correct!

          -   ``void finalGrade {``

              -   This function header is missing parentheses. Even if a function does not take in any parameters, empty parentheses should be used.


   .. tab:: Q3

      .. parsonsprob:: defns_uses_3
         :adaptive:

         Construct a block of code that correctly defines a the addTwo function.
         -----
         int addTwo(int x) {

         int addTwo(int x); #distractor

         int addTwo(int x) #distractor

          int new = x + 2;

          return new;

          return x; #distractor

         }
