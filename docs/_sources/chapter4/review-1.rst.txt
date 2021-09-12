Multiple Choice Exercises
-------------------------

Answer the following **Multiple Choice** questions to
assess what you have learned in this chapter.

.. tabbed:: self-check

   .. tab:: Q1

      .. mchoice:: cond_rec_mc1

          Say you run the following code.  What is the value of ``mod``?

          ::

              int x = 4;
              int y = 7;
              int mod = y % x;

          -   0

              -   There *is* a remainder.

          -   1

              -   Incorrect!

          -   2

              -   Incorrect!

          -   3

              +   The remainder of ``7 / 4`` is 3.

          -   4

              -   We can't have a remainder of 4, since 4 is the divisor.

   .. tab:: Q2

      .. mchoice:: cond_rec_mc2

          What is printed when the following code executes?

          ::

              int x = 8;

              if (x % 3 == 2) {
                  cout << "hey!" << endl;
              } else if (x != 7) {
                  cout << "hi!" << endl;
              } else if (x % 2 == 0) {
                  cout << "hello!" << endl;
              } else {
                  cout << "bye!" << endl;
              }

          -   :: none

                  hey!

              +   Since the first conditon is met, the rest of the chained
                  conditional does not execute.

          -   :: none

                  hi!

              -   It's true that ``8 != 7``, but "hi!" is not printed here.

          -   :: none

                  hi!

              -   It's true that ``8 % 2 == 0``, but "hello!" is not printed!

          -   :: none

                  hey!
                  hi!
                  hello!

              -   All of these conditons are met, but only one expression is
                  printed!

          -   :: none

                  bye!

              -   At least one of the conditons is met, so the ``else`` will not
                  execute!


   .. tab:: Q3

      .. mchoice:: cond_rec_mc3

          What is printed when the following code executes?

          ::

              int x = 34;

              if (32 < x) {
                  cout << "It's Freezing!";
              }
              if (x < 40) {
                  cout << "It's Cold!";
              }
              if (x > 65) {
                  cout << "It's Warm!";
              } else {
                  cout << "It's Hot!";
              }

          -   :: none

                  It's Freezing!

              -   Take a closer look at the conditions and the way they
                  are written in the program.

          -   :: none

                  It's Cold!

              -   Take a closer look at the conditions and the way they
                  are written in the program.

          -   :: none

                  It's Freezing!
                  It's Cold!

              -   You've identified some of the conditons that are met!
                  Take another look at the *chain* of conditionals at the
                  end!

          -   :: none

                  It's Freezing!
                  It's Cold!
                  It's Hot!

              +   These statements are quite contradicting, but that's exactly
                  what the output would be if we ran this code.

          -   :: none

                  It's Hot!

              -   Take a closer look at the conditions and the way they
                  are written in the program.


   .. tab:: Q4

      .. mchoice:: cond_rec_mc4

          Suppose you have defined the following function:

          ::

              void practicingReturns (int a, int b) {
                  if (a < b) {
                      a += 2;
                  }
                  if (a > b) {
                      return;
                  }
                  cout << a + b;
              }
          
          What is printed when we run the following code?

          ::

              int x = practicingReturns(2, 3);
          
          -   5

              -   This is what ``a + b`` would be before the first conditonal.

          -   7

              -   This is the value of ``a + b`` after the first conditional, but it
                  doesn't print.

          -   23

              -   This is not the value of ``a + b``.

          -   Nothing.

              +   The function exits with a return before anything is printed.


   .. tab:: Q5

      .. mchoice:: cond_rec_mc5

          Suppose you have defined the following function:

          ::

              void fortuneCookie (int a, bool b, char c) {
                  if (c < 'm') {
                      if (a % 2 == 0) {
                          cout << "An alien of some sort will be appearing to you shortly.";
                      } else {
                          cout << "The fortune you seek is in another cookie.";
                      }
                  } else if (c < 'r') {
                      if (b) {
                          cout << "He who laughs at himself never runs out of things to laugh at.";
                      } else {
                          cout << "You will be hungry again in one hour.";
                      }
                  } else {
                      cout << "Fortune not found? Abort, retry, ignore.";
                  }
              }

          What will be your fortune if you run the following code?

          ::

              fortuneCookie(14, false, 'm');

          -   ``An alien of some sort will be appearing to you shortly.``

              -   ``'m'`` is NOT less than ``'m'``, so you don't even enter the ``if`` block.

          -   ``The fortune you seek is in another cookie.``

              -   ``'m'`` is NOT less than ``'m'``, so you don't even enter the ``if`` block.

          -   ``He who laughs at himself never runs out of things to laugh at.``

              -   ``if (b)`` really means ``if (b == true)``.

          -   ``You will be hungry again in one hour.``

              +   ``'m' < 'r'`` is true and ``b == false``, so this is the fortune that will print.

          -   ``Fortune not found? Abort, retry, ignore.``

              -   ``'m'`` is less than ``'r'`` so you would enter the ``else if`` block, not the ``else``.


   .. tab:: Q6

      .. mchoice:: cond_rec_mc6

          Suppose you have defined the following function:

          ::

              void fortuneCookie (int a, bool b, char c) {
                  if (c < 'm') {
                      if (a % 2 == 0) {
                          cout << "An alien of some sort will be appearing to you shortly.";
                      } else {
                          cout << "The fortune you seek is in another cookie.";
                      }
                  } else if (c < 'r') {
                      if (b) {
                          cout << "He who laughs at himself never runs out of things to laugh at.";
                      } else {
                          cout << "You will be hungry again in one hour.";
                      }
                  } else {
                      cout << "Fortune not found? Abort, retry, ignore.";
                  }
              }

          What will be your fortune if you run the following code?

          ::

              fortuneCookie(22, true, 'b');

          -   ``An alien of some sort will be appearing to you shortly.``

              +   ``'b' < 'm'`` and ``22 % 2 == 0``, so this is the fortune that will print.

          -   ``The fortune you seek is in another cookie.``

              -   ``22 % 2 == 0``, so you enter the ``if`` block, not the else.

          -   ``He who laughs at himself never runs out of things to laugh at.``

              -   ``'b'`` is less than ``'m'``, so you would enter the ``if`` block, not the ``else if``.

          -   ``You will be hungry again in one hour.``

              -   ``'b'`` is less than ``'m'``, so you would enter the ``if`` block, not the ``else if``.

          -   ``Fortune not found? Abort, retry, ignore.``

              -   ``'b'`` is less than ``'m'``, so you would enter the ``if`` block, not the ``else``.


   .. tab:: Q7

      .. mchoice:: cond_rec_mc7

          Suppose you have defined the following function:

          ::

              void theThing (int m, int n, bool b) {
                  if (b) {
                      if (m % 4 == 0) {
                          cout << m;
                          return;
                      }
                      if ((m + n) > 10) {
                          cout << m + n;
                          return;
                      }
                  } else if ((m > n) == b) {
                      cout << m - n;
                      return;
                  } else {
                      if (n % 3 == 0) {
                          cout << n;
                          return;
                      }
                  }
                  cout << -1;
              }

          What is printed when we run the following code?

          ::

              theThing (5, 10, false);

          -   5

              -   The outer ``if`` condition is not met, the block does not execute.

          -   15

              -   The outer ``if`` condition is not met, the block does not execute.

          -   -5

              +   ``m > n`` evaluates to false, so the ``else if`` block executes.

          -   10

              -   The condition for ``else if`` is met, so the function never enters the ``else``.
          
          -   -1

              -   The function has returned.

   .. tab:: Q8

      .. mchoice:: cond_rec_mc8

          Suppose you have defined the following function:

          ::

              void theThing (int m, int n, bool b) {
                  if (b) {
                      if (m % 4 == 0) {
                          cout << m;
                          return;
                      }
                      if ((m + n) > 10) {
                          cout << m + n;
                          return;
                      }
                  } else if ((m > n) == b) {
                      cout << m - n;
                      return;
                  } else {
                      if (n % 3 == 0) {
                          cout << n;
                          return;
                      }
                  }
                  cout << -1;
              }

          What is printed when we run the following code?

          ::

              theThing (6, 4, true);

          -   6

              -   ``5 % 4 != 0`` in the ``if`` block, so the function doesn't print 6.

          -   10

              -   ``m + n !> 10`` in the ``if`` block, so the function doesn't print 10.

          -   2

              -   The condition for ``if`` is met, so the function never enters the ``else if``.

          -   4

              -   The condition for ``if`` is met, so the function never enters the ``else``.

          -   -1

              +   None of the conditions were met, so we reach the default cout -1.


   .. tab:: Q9

      .. mchoice:: cond_rec_mc9

          Suppose you have defined the following function:

          ::

              void moo (int m, int n) {
                  if (m != n) {
                      m += 2;
                      cout << "Moo!";
                      moo (m, n);
                  } else {
                      cout << "Got Milk?";
                  }
              }

          How many times does "Moo!" print when we run the following?

          ::

              moo (4, 8);

          -   0

              -   When we call the function ``4 != 8``, so "Moo!" is printed at least
                  once.

          -   1

              -   The function calls itself inside of the ``if`` loop, so "Moo!" is printed
                  more than once.

          -   2

              +   ``m`` is incremented by two each with each function call, so after two
                  ``m == n`` and the recursion stops.

          -   3

              -   Take a look at how ``m`` is incremented with each function call.

          -   infinite recursion

              -   The function stops printing "Moo!" when ``m == n``.


   .. tab:: Q10

      .. mchoice:: cond_rec_mc10

          Suppose you have defined the following function:

          ::

              void moo (int m, int n) {
                  if (m != n) {
                      m += 2;
                      cout << "Moo!";
                      moo (m, n);
                  } else {
                      cout << "Got Milk?";
                  }
              }

          How many times does "Moo!" print when we run the following?

          ::

              moo (5, 10);

          -   0

              -   When we call the function ``5 != 10``, so "Moo!" is printed at least
                  once.

          -   1

              -   The function calls itself inside of the ``if`` loop, so "Moo!" is printed
                  more than once.

          -   2

              -   After two function calls, ``m == 9`` and ``n == 10``.  The function is not
                  done printing.

          -   3

              -   After three function calls, ``m == 11`` and ``n == 10``.  The function is not
                  done printing

          -   infinite recursion

              +   The function stops printing "Moo!" when ``m == n``, but since ``m`` is odd
                  and ``n`` is even, they will never be equal as long as we increment by two.


