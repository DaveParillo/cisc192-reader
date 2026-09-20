Returning from main
-------------------

Now that we have functions that return values, I can let you in on a
secret. main should have a return statement too. It’s supposed
to return an integer:

::

    int main () {
      return 0;
    }

The usual return value from main is 0, which indicates that the program
succeeded at whatever it was supposed to do. If something goes wrong, it
is common to return -1, or some other value that indicates what kind of
error occurred.

The main function is special in a few ways.
One of them is that it is the only function where the compiler will add
``return 0;`` if main does not already have a return statement.

Of course, you might wonder who this value gets returned to, since we
never call main ourselves. It turns out that when the system executes a
program, it starts by calling main in pretty much the same way it calls
all the other functions.

There are even some parameters that are passed to main by the system,
but we are not going to deal with them for a little while.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: alt_execution_1

         What will be printed after ``main`` is executed?

         ::

             #include <iostream>
             using namespace std;

             void weather(int temp) {
               if (temp < 52) {
                 cout << "It is cold!";
               }
               else {
                 cout << "It is warm!";
               }
             }

             int main() {
               int degrees = 52;
               weather(degrees);
             }


         - [ ] It is cold!

           That statement would print if degrees was less than 50.
         - [x] It is warm!

           Correct!
         - [ ] Nothing prints.

           One of the statements is satisfied, so something does print.
         - [ ] Error message.

           There is nothing in the code below that would generate an error.

   .. tb-tab:: Q2

      .. tb-blank::
         :name: return_main_2

         Usually, we return {{blank:blank1}} to exit main.  However, if there are
         any errors that we catch, we might return {{blank:blank2}}.

         .. tb-answer:: blank1
            :match: 0
            :feedback: Correct!

         .. tb-answer:: blank2
            :match: -1
            :incorrect: Try again!

   .. tb-tab:: Q3

      .. tb-choice::
         :name: chained_conditionals_1

         What will print after the following code is executed?

         ::

             #include <iostream>
             using namespace std;

             int main () {
               int x = 10;
               if (x > 8) {
                 cout << "One! ";
               }
               if (x > 6) {
                 cout << "Two! ";
               }
               if (x > 3) {
                 cout << "Three!" << endl;
               }
               return 0;
             }


         - [ ] Three!

           Make note of the use of "if" instead of "else if" or "else".
         - [ ] One!

           Make note of the use of "if" instead of "else if" or "else".
         - [ ] One! Two!

           Make note of the use of "if" instead of "else if" or "else".
         - [x] One! Two! Three!

           When we have "if" statments, but no "else if" or "else", every condition will be checked.

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Main function <main_function>`
