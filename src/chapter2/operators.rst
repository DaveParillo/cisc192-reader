.. _variables-types-operators:

Operators
---------

.. index::
   single: operator

**Operators** are special symbols that are used to represent simple
computations like addition and multiplication. Most of the operators in
C++ do exactly what you would expect them to do, because they are common
mathematical symbols. For example, the operator for adding two integers
is ``+``.

The following are all legal C++ expressions whose meaning is more or
less obvious:

::

    1 + 1
    hour - 1
    hour * 60 + minute
    minute / 60

.. index::
   single: expression

**Expressions** can contain both variables names and integer values. In each
case the name of the variable is replaced with its value before the
computation is performed.

Addition, subtraction and multiplication all do what you expect, but you
might be surprised by division. For example, compile the following program around
observe the output.

This program is supposed to print the fraction of the hour that has
passed since midnight.  You'll notice that the result isn't quite what
you expect.  Read on to find out why!

.. tb-code:: cpp
   :name: operators_AC_1
   :caption: Integer Division

   #include <iostream>
   using std::cout;

   int main () {
       int int hour = 12;
       minute = 59;
       cout << "Number of minutes since midnight: ";
       cout << hour * 60 + minute << '\n';
       cout << "Fraction of the hour that has passed: ";
       cout << minute / 60 << '\n';
   }

.. index::
   single: integer division

The first line is what we expected, but the second line is odd. The
value of the variable minute is 59, and 59 divided by 60 is 0.98333, not
0. The reason for the discrepancy is that C++ is performing **integer
division**.

.. index::
   single: operand

When both of the **operands** are integers (operands are the things
operators operate on), the result must also be an integer, and by
definition integer division always **truncates** the result, even in cases like
this where the next integer is so close.
A floating point result cannot be stored in an integer, so the fractional
part must be discarded and only the integer part is returned and displayed.

A possible alternative in this case is to calculate a percentage rather
than a fraction:

::

    cout << "Percentage of the hour that has passed: ";
    cout << minute * 100 / 60 << '\n';

The result is:

::

    Percentage of the hour that has passed: 98

Again the result is truncated, but at least now the answer is
approximately correct. In order to get an even more accurate answer, we
could use a different type of variable, called floating-point, that is
capable of storing fractional values. 

.. index::
   single: floating-point
   single: double

.. note::
   In C++, **floating-points** are declared as type ``double``. We’ll get 
   to that in the next chapter.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-match::
         :name: operators_1

         Match the statement to the result, given that x = 10.


         x*10
            100
         x-10
            0
         100/x
            10
         (x+x+x+x+x)*20
            1000

   .. tb-tab:: Q2

      .. tb-blank::
         :name: operators_3

         Integer division always {{blank}}.

         .. tb-answer::
            :match: truncates
            :feedback: Correct!
            :hint: x; Try again!

   .. tb-tab:: Q3

      .. tb-blank::
         :name: operators_3_1

         ::

            int num1 = 12;
            int num2 = 5;
            cout << num1 / num2;

         What is printed to the terminal?

         {{blank}}

         .. tb-answer::
            :match: 2
            :feedback: Correct!
            :hint: 2.4; Remember, this is an integer division!
            :incorrect: Try again!

   .. tb-tab:: Q4

      .. tb-blank::
         :name: operators_3_2

         ::

            int num1 = 10;
            int num2 = 48;
            cout << num2 / num1;

         What is printed to the terminal?

         {{blank}}

         .. tb-answer::
            :match: 4
            :feedback: Correct!
            :hint: 4.8; Remember, this is an integer division!
            :incorrect: Try again!

   .. tb-tab:: Q5

      .. tb-blank::
         :name: operators_3_3

         ::

            int num1 = 7;
            int num2 = 8;
            cout << "Decimal:" << num1 / num2;

         What is printed after ``Decimal:``?

         {{blank}}

         .. tb-answer::
            :match: 0
            :feedback: Correct!
            :hint: 0.875; Remember, this is an integer division!
            :incorrect: Try again!

   .. tb-tab:: Q6

      .. tb-parsons::
         :name: operators_4

         Construct a code block that prints the total cost of your meal, 
         including the 6.0% sales tax, after you purchase two orders of fries,
         three burgers, and a milkshake.
         Start by initializing the value of sales tax,
         then the prices of the food.
         Once you have initialized the variables,
         you can perform your calculations and save the result
         in the price variable.
         At the very end, you will print out the total price.

         .. code-block:: cpp

            {{group}}
            int main () {
            {{endgroup}}
            {{group}}
             double tax = 0.06;
            {{endgroup}}
            {{group}}
             double fries, milkshake, burger;
            {{endgroup}}
            {{distractor}}
            {{group}}
             string fries, milkshake, burger;
            {{endgroup}}
            {{group}}
             fries = 2.50;
             milkshake = 3.75;
             burger = 3.00;
            {{endgroup}}
            {{group}}
             double price = 2 * fries + 3 * burger + milkshake;
            {{endgroup}}
            {{group}}
             double price_with_tax = price + price * tax;
            {{endgroup}}
            {{distractor}}
            {{group}}
             double price_with_tax = price * tax;
            {{endgroup}}
            {{group}}
             cout << "The total cost of your meal is $";
             cout << price_with_tax << ".\n";
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << "The total cost of your meal is $";
             cout << price << ".\n";
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Arithmetic operators <operator_arithmetic>`
     - :lang:`Assignment operators <operator_assignment>`

