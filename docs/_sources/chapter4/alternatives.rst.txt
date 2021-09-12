.. _alternative:

Alternative Execution
---------------------

A second form of conditional execution is alternative execution, in
which there are two possibilities, and the condition determines which
one gets executed. The syntax looks like:

::

    if (x % 2 == 0)
    {
      cout << "x is even\n";
    } 
    else
    {
      cout << "x is odd\n";
    }

If the remainder when x is divided by 2 is zero, then we know that x is
even, and this code displays a message to that effect. If the condition
is false, the second set of statements is executed. Since the condition
must be true or false, exactly one of the alternatives will be executed.

As an aside, if you think you might want to check the parity (evenness
or oddness) of numbers often, you might want to "wrap" this code up in a
function, as follows:

::

    void print_parity (int x) {
      if (x % 2 == 0)
      {
        cout << "x is even\n";
      } 
      else
      {
        cout << "x is odd\n";
      }
    }

Now you have a function named ``print_parity`` that will display an
appropriate message for any integer you care to provide. In main you
would call this function as follows:

::

    print_parity (17);

Always remember that when you *call* a function, you do not have to
declare the types of the arguments you provide. C++ can figure out what
type they are. You should resist the temptation to write things like:

::

    int number = 17;
    print_parity (int number);         // WRONG!!!


.. activecode:: alt_execution_AC_1
   :language: cpp
   :caption: Even or Odd?

   This program shows you how the print parity function works.
   Feel free to modify the values of ``number`` and ``other`` to
   see how the output is changed.
   ~~~~
   #include <iostream>
   using std::cout;

   void print_parity (int x) {
       if (x % 2 == 0)
       {
           cout << "x is even\n";
       } 
       else
       {
           cout << "x is odd\n";
       }
   }

   int main () {
       int number = 17;
       print_parity(number);
       int other = 18;
       print_parity(other);
       return 0;
   }

.. tabbed:: self-check

   .. tab:: Q1

      .. mchoice:: alt_execution_1
         :answer_a: It is cold!
         :answer_b: It is warm!
         :answer_c: Nothing prints.
         :answer_d: Error message.
         :correct: b
         :feedback_a: That statement would print if degrees was less than 50.
         :feedback_b: Correct!
         :feedback_c: One of the statements is satisfied, so something does print.
         :feedback_d: There is nothing in the code below that would generate an error.

         What will be printed after the main is executed?

         ::

             void weather(int temp) {
               if temp < 52
               {
                 cout << "It is cold!";
               }
               else
               {
                 cout << "It is warm!";
               }
             }

             int main() {
               int degrees = 52;
               weather(degrees);
             }


   .. tab:: Q2

      .. parsonsprob:: alt_execution_2
         :adaptive:

         Construct a block of code that correctly goes through alternative
         execution for pricing of an entre at a nice restaurant.  If the
         price is more than $30.00, print "Expensive!".  If the price is
         less than $30.00, print "Inexpensive!"  You should by initializing
         the cost to $40.
         -----
         int cost = 40;

         if (cost > 30) {

         if (cost > 30) #distractor

          cout << "Expensive!";

         } //"if" bracket

         else {

         else if { #distractor

          cout << "Inexpensive!" #distractor

          cout << "Inexpensive!";

         } //"else" bracket

