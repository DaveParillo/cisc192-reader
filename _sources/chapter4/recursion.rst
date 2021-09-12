Recursion
---------

I mentioned in the last chapter that it is legal for one function to
call another, and we have seen several examples of that. I neglected to
mention that it is also legal for a function to call itself. It may not
be obvious why that is a good thing, but it turns out to be one of the
most magical and interesting things a program can do.

.. index::
   single: recursion
   single: recursive function

.. note::
   The process of a function calling itself is called **recursion**, and
   such functions are said to be **recursive**.

For example, look at the following function:

::

    void countdown (int n) {
      if (n == 0) {
        cout << "Blastoff!\n";
      } else {
        cout << n << endl;
        countdown (n - 1);
      }
    }

The name of the function is ``countdown`` and it takes a single integer as a
parameter. If the parameter is zero, it outputs the word “Blastoff.”
Otherwise, it outputs the parameter and then calls a function named
``countdown`` —itself— passing ``n - 1`` as an argument.

Watch how the countdown function works when we start with a value
of 3.

.. codelens:: recursion_codelens_1
   :language: cpp
   :caption: Recursion

   #include <iostream>
   using std::cout;
   
   void countdown (int n) {
       if (n == 0) {
           cout << "Blastoff!\n";
       } else {
           cout << n << '\n';
           countdown (n-1);
       }
   }

   int main () {
       countdown (3);
       return 0;
   }

What happens if we call ``countdown`` function like this:

  The execution of ``countdown`` begins with ``n = 3``, and since n is not zero, it
  outputs the value 3, and then calls itself...

      The execution of ``countdown`` begins with ``n = 2``, and since n is not zero,
      it outputs the value 2, and then calls itself...

          The execution of ``countdown`` begins with ``n = 1``, and since n is not
          zero, it outputs the value 1, and then calls itself...

              The execution of ``countdown`` begins with ``n = 0``, and since n is
              zero, it outputs the word “Blastoff!” and then returns.

          The ``countdown`` that got ``n = 1`` returns.

      The ``countdown`` that got ``n = 2`` returns.

  The ``countdown`` that got ``n = 3`` returns.

And then you’re back in ``main`` (what a trip). So the total output looks
like:

::

    3
    2
    1
    Blastoff!

As a second example, let’s look again at the functions ``new_line`` and
``three_line``.

::

    void new_line () {
      cout << endl;
    }

    void three_line () {
      new_line ();  new_line ();  new_line ();
    }

Although these work, they would not be much help if I wanted to output 2
newlines, or 106. A better alternative would be

::

    void repeat_lines (int n) {
      if (n > 0) {
        cout << endl;
        repeat_lines (n - 1);
      }
    }

This program is similar to countdown; as long as n is greater than zero,
it outputs one newline, and then calls itself to output ``n-1`` additional
newlines. Thus, the total number of newlines is ``1 + (n - 1)``, which usually
comes out to roughly n.

.. index:: random

.. activecode:: recursion_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-Wextra', '-pedantic', '-std=c++11']
   :nocodelens:
   :caption: Guessing Game.

   You can have a little bit of fun with recursion.  Try this guessing game below!
   ~~~~
   #include <iostream>
   #include <random>

   void guess_number(int num) {
       using std::cin;
       using std::cout;
       cout << "Enter your guess: ";
       int guess;
       cin >> guess;
       if (guess == num) {
           cout << "That's it!";
       }
       else if (guess > num) {
           cout << "Too high! ";
           guess_number(num);
       }
       else {
           cout << "Too low! ";
           guess_number(num);
       }
   }

   int main() {
       // make a random number generator
       std::random_device r;
       std::default_random_engine eng(r());

       int randomNumber = std::uniform_int_distribution<int> {1, 100} (eng);
       guess_number(randomNumber);
   }


.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: recursion_1
         :answer_a: !
         :answer_b: !!
         :answer_c: !!!
         :answer_d: !!!!
         :correct: c
         :feedback_a: The function keeps executing while n is greater than 0.
         :feedback_b: The function keeps executing while n is greater than 0.
         :feedback_c: Correct! First, the program enters the if statement within exclamationPoint because n is greater than 0. Then the function prints a "!" and calls itself again, but with n-1, which is 2. This repeats until n is 0, which is when the program exits the function.
         :feedback_d: The function keeps executing while n is greater than 0. Therefore, when n is 0, it will not print a "!"

         What will print?

         ::

             #include <iostream>
             using namespace std;

             void exclamationPoint(int n) {
               if (n > 0) {
                 cout << "!";
                 exclamationPoint (n-1);
               }
             }

             int main () {
               exclamationPoint(3);
             }

   .. tab:: Q2

      .. mchoice:: recursion_2
         :answer_a: !!
         :answer_b: !
         :answer_c: 0
         :answer_d: Nothing prints.
         :correct: d
         :feedback_a: If we start at zero, will the function ever call itself?
         :feedback_b: If we start at zero, will the function ever call itself?
         :feedback_c: The only output statement in this program prints a "!", therefore "0" would never print.
         :feedback_d: Correct! The program never enters the "if" statement within the function because n is never greater than 0.
         
         What will print?

         ::

             #include <iostream>
             using namespace std;

             void exclamationPoint(int n) {
               if (n > 0) {
                 cout << "!";
                 exclamationPoint (n-1);
               }
             }

             int main () {
               exclamationPoint(0);
             }


   .. tab:: Q3

      .. fillintheblank:: recursion_3

          A function that calls itself is said to be |blank|.

          - :[Rr][Ee][Cc][Uu][Rr][Ss][Ii][Vv][Ee]: And the process by which a function calls itself is called recursion.
            :.*: Try again!

