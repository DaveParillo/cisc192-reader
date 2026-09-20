Infinite Recursion
------------------

.. index::
   single: base case

In the examples in the previous section, notice that each time the
functions get called recursively, the argument gets smaller by one, so
eventually it gets to zero. When the argument is zero, the function
returns immediately, *without making any recursive calls*. This
case—when the function completes without making a recursive call—is
called the **base case**.

.. index::
   single: infinite recursion

If a recursion never reaches a base case, it will go on making recursive
calls forever and the program will never terminate. This is known as
**infinite recursion**, and it is generally not considered a good idea.

In most programming environments, a program with an infinite recursion
will not really run forever. Eventually, something will break and the
program will report an error. 

.. warning::
   Infinite recursion is the first example we have seen of a run-time 
   error (an error that does not appear until you run the program).

You should write a small program that recurses forever and run it to see
what happens. Below is an example. The function adds to the number **n**
instead of subtracting, which means it is always larger than 0. Therefore,
the function executes "forever." Unfortunately, if there was a snip of live
code put in below, the ebook's page would extend down forever because a new
line is being created infinitely.

::

    #include <iostream>
    using namespace std;

    void print_lines(int n) {
      if (n > 0) {
        cout << endl;
        print_lines(n + 1);
      }
    }

    int main() {
      void print_lines(10);
    }

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-blank::
         :name: unbounded_recursion_1

         If a recursive function never reaches its {{blank:blank1}} {{blank:blank2}}, then the function
         will continue executing indefinitely.  This is called {{blank:blank3}} {{blank:blank4}}.

         .. tb-answer:: blank1
            :match: [Bb][Aa][Ss][Ee]
            :feedback: Correct!

         .. tb-answer:: blank2
            :match: [Cc][Aa][Ss][Ee]

         .. tb-answer:: blank3
            :match: [Ii][Nn][Ff][Ii][Nn][Ii][Tt][Ee]

         .. tb-answer:: blank4
            :match: [Rr][Ee][Cc][Uu][Rr][Ss][Ii][Oo][Nn]
            :incorrect: Try again!

   .. tb-tab:: Q2

      .. tb-choice::
         :name: unbounded_recursion_2

         Take a look at the code below.  What will happen if you were to run it on
         your machine?

         ::

             #include <iostream>
             using namespace std;

             void isNegative(int n) {
               if (n >= 0) {
                 cout << "Not Negative!";
                 isNegative(n - 1);
               }
               cout << "Negative!";
             }

             int main() {
               isNegative(-10);
             }


         - [ ] The function will print "Not Negative!"

           The function will never print "Not Negative!" since we start with a negative number!
         - [ ] The function will print "Not Negative!" more than once.  Then it will print "Negative!" and will stop executing.

           The function will never print "Not Negative!" since we start with a negative number!
         - [x] The function will print "Negative!"

           We start with a negative number, so the function will reach the base case.
         - [ ] The function will never stop executing, there will be infinite recursion.

           We start with a negative number, so the function will reach the base case.

   .. tb-tab:: Q3

      .. tb-choice::
         :name: unbounded_recursion_3

         ``isNegative`` is defined exactly as it was above, but we have changed the
         call to it in ``main``.
         What will happen if we run the code with this input?

         ::

             #include <iostream>
             using namespace std;

             void isNegative(int n) {
               if (n >= 0) {
                 cout << "Not Negative!";
                 isNegative(n - 1);
               }
               cout << "Negative!";
             }

             int main() {
               isNegative(10);
             }


         - [ ] The function will print "Not Negative!"

           The function will print "Not Negative!", but it won't stop there!
         - [x] The function will print "Not Negative!" more than once.  Then it will print "Negative!" and will stop executing.

           The function will print "Not Negative!" until it reaches a negative number.
         - [ ] The function will print "Negative!"

           The function will eventually print "Not Negative!", but that's not all!
         - [ ] The function will never stop executing, there will be infinite recursion.

           Since we decrement each time, the base case will be reached.

   .. tb-tab:: Q4

      .. tb-choice::
         :name: unbounded_recursion_4

         The ``isNegative`` function has been **edited** as shown below.  What will 
         happen now when we run the code?

         ::

             #include <iostream>
             using namespace std;

             void isNegative(int n) {
               if (n >= 0) {
                 cout << "Not Negative!";
                 isNegative(n + 1);
               }
               cout << "Negative!";
             }

             int main() {
               isNegative(10);
             }

         - [ ] The function will print "Not Negative!"

           The function will print "Not Negative!" but it won't stop there!
         - [ ] The function will print "Not Negative!" more than once.  Then it will print "Negative!" and will stop executing.

           The function will print "Not Negative!" more than once.  But will it print "Negative"?
         - [ ] The function will print "Negative!"

           We start with a positive number, so the function simply won't print "Not Negative!"
         - [x] The function will never stop executing, there will be infinite recursion.

           Our input is incremented with every recursive call, so if we start with a positive number, we will never reach the base case.
