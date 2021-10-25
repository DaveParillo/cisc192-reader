Multiple assignment
-------------------
I haven’t said much about it, but it is legal in C++ to assign to
the same variable more than once. The effect of the second assignment
is to replace the old value of the variable with a new value.

.. activecode:: multiple_assignment_AC_1
  :language: cpp
  :caption: Multiple assignment

  The code below reassigns ``fred`` from 5 to 7 and prints both values out.
  ~~~~
  #include <iostream>

  int main () {
      int fred = 5;
      std::cout << fred;
      fred = 7;
      std::cout << fred;
      return 0;
  }

The output of this program is ``57``, because the first time we print
``fred`` his value is 5, and the second time his value is 7.

.. activecode:: multiple_assignment_AC_2
  :language: cpp
  :caption: Multiple assignment

  The active code below reassigns ``fred`` from 5 to 7 without printing out the initial
  value.
  ~~~~
  #include <iostream>

  int main () {
      int fred = 5;
      fred = 7;
      std::cout << fred;
      return 0;
  }

However, if we do not print ``fred`` the first time, the output is only 7 because
the value of ``fred`` is just 7 when it is printed.

.. index::
   single: multiple assignment

This kind of **multiple assignment** is the reason I described variables
as a *container* for values. When you assign a value to a variable, you
change the contents of the existing storage location,
as shown in the codelens below.
Step through the code one line at a time and notice how the value
assigned to fred changes even when no output is created.

.. codelens:: multiple_assignment_CL
   :caption: Reassigning values to fred
   :language: cpp

   #include <iostream>
 
   int main () {
       int fred = 5;
       std::cout << fred << '\n';
       fred = 8;
       fred = 13;
       fred = 21;
       fred = 34;
       std::cout << fred << '\n';
       return 0;
   }


When there are multiple assignments to a variable, it is especially
important to distinguish between an assignment statement and a statement
of equality. Because C++ uses the ``=`` symbol for assignment, it is
tempting to interpret a statement like ``a = b`` as a statement of
equality. It is not!

.. warning::
   An assignment statement uses a single ``=`` symbol. For example, ``x = 3``
   assigns the value of 3 to the variable ``x``. On the other hand, an equality
   statement uses two ``=`` symbols. For example, ``x == 3`` is a boolean that evaluates
   to true if ``x`` is equal to 3 and evaluates to false otherwise.

   This is a common source of error.

First of all, equality is commutative, and assignment is not. For
example, in mathematics if :math:`a = 7` then :math:`7 = a`. But in C++
the statement ``a = 7;`` is legal, and ``7 = a;`` is not.

Furthermore, in mathematics, a statement of equality is true for all
time. If :math:`a = b` now, then :math:`a` will always equal :math:`b`.
In C++, an assignment statement can make two variables equal, but they
don’t have to stay that way!

::

     int a = 5;
     int b = a;     // a and b are now equal
     a = 3;         // a and b are no longer equal

The third line changes the value of ``a`` but it does not change the
value of ``b``, and so they are no longer equal. In many programming
languages an alternate symbol is used for assignment, such as ``<-`` or
``:=``, in order to avoid confusion.

Although multiple assignment is frequently useful, you should use it
with caution. If the values of variables are changing constantly in
different parts of the program, it can make the code difficult to read
and debug.

.. tabbed:: self_check

   .. tab:: Q1

      .. dragndrop:: multiple_assignment_1
          :feedback: Try again!
          :match_1:  4=a|||Illegal
          :match_2: a==b|||Checking if a is equal to b
          :match_3: a=b|||Assigning a to the value of b
          :match_4: a=4|||Setting the value of a to 4

          Match the expression to the statement that best describes it.

   .. tab:: Q2

      .. mchoice:: multiple_assignment_2
         :answer_a: 10!1!
         :answer_b: 10 ! 1 !
         :answer_c: 10 ! 10 !
         :answer_d: 1!1!
         :correct: a
         :feedback_a: There are no spaces between the numbers.
         :feedback_b: Remember, in C++ spaces must be printed.
         :feedback_c: Carefully look at the values being assigned.
         :feedback_d: Carefully look at the values being assigned.

         What will print?

         .. code-block:: cpp

          #include <iostream>

          int main () {
            int x = 10;
            std::cout << x << "!";
            x = 1;
            std::cout << x << "!";
            return 0;
          }

   .. tab:: Q3

      .. mchoice:: multiple_assignment_3
         :answer_a: True
         :answer_b: False
         :answer_c: 0
         :answer_d: 1
         :correct: d
         :feedback_a: Remember that printing a boolean results in either 0 or 1.
         :feedback_b: Remember that printing a boolean results in either 0 or 1.
         :feedback_c: Is x equal to y?
         :feedback_d: x is equal to y, so the output is 1.

         What is the correct output?

         .. code-block:: cpp

          #include <iostream>
          using std::cout;

          int main () {
            int x = 0;
            x = 5;
            int y = x;
            y = 5;
            bool z = x == y;
            cout << z;
          }

