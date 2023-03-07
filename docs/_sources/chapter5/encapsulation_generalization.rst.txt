Encapsulation and generalization
--------------------------------
Encapsulation usually means taking a piece of code and wrapping it up in
a function, allowing you to take advantage of all the things functions
are good for. We have seen two examples of encapsulation, when we wrote
``print_parity`` in section :ref:`alternative` and
``is_digit`` in section :ref:`bool-functions`.

Generalization means taking something specific, like printing multiples
of 2, and making it more general, like printing the multiples of any
integer.

Here’s a function that encapsulates the loop from the previous section
and generalizes it to print multiples of ``n``.

::

   void print_multiples (int n) {
     int i = 1;
     while (i <= 6) {
       cout << n*i << "   ";
       i = i + 1;
     }
     cout << '\n';
   }

To encapsulate, all I had to do was add the first line, which declares
the name, parameter, and return type. To generalize, all I had to do was
replace the value 2 with the parameter ``n``.

If we call this function with the argument 2, we get the same output as
before. With argument 3, the output is:

::

   3   6   9   12   15   18

and with argument 4, the output is

::

   4   8   12   16   20   24

By now you can probably guess how we are going to print a multiplication
table: we’ll call ``print_multiples`` repeatedly with different
arguments. In fact, we are going to use another loop to iterate through
the rows.

::

   int i = 1;
   while (i <= 6) {
     print_multiples (i);
     i = i + 1;
   }

First of all, notice how similar this loop is to the one inside
``print_multiples``. All I did was replace the print statement with a
function call.


.. activecode:: encapsulation_generalization_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Two-dimensional tables

   Try running the active code below, which uses ``print_multiples``.
   ~~~~
   #include <iostream>
 
   void print_multiples (int n) {
     int i = 1;
     while (i <= 6) {
       std::cout << n*i << "   ";
       i = i + 1;
     }
     std::cout << '\n';
   }

   int main() {
     int i = 1;
     while (i <= 6) {
       print_multiples (i);
       i = i + 1;
     }
   }

Note the output is a (slightly sloppy) multiplication table.
If the sloppiness bothers you,
you can also use tab characters, like below.

.. activecode:: encapsulation_generalization_AC_2
   :language: cpp
   :caption: Two-dimensional tables

   The active code below uses tab characters to make the table neater.
   ~~~~
   #include <iostream>
 
   void print_multiples (int n) {
     int i = 1;
     while (i <= 6) {
       std::cout << n*i << '\t';
       i = i + 1;
     }
     std::cout << '\n';
   }

   int main() {
     int i = 1;
     while (i <= 6) {
       print_multiples (i);
       i = i + 1;
     }
   }

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: encapsulation_generalization_1
         :answer_a: Replacing integers with parameters.
         :answer_b: Using a parameter that exists in several different functions.
         :answer_c: Taking a very specific task and making it more applicable to other situations.
         :answer_d: Creating two functions with the same purpose but different names.
         :correct: c
         :feedback_a: This may be a possible way to generalize, but not the purpose.
         :feedback_b: This is not the purpose of generalization.
         :feedback_c: This makes your code more versatile.
         :feedback_d: This is not the purpose of generalization.

         What is the purpose of generalization?

   .. tab:: Q2

      .. parsonsprob:: encapsulation_generalization_2
         :numbered: left
         :adaptive:

         Create a function called ``powers_of_two`` which prints out a table
         with the powers of two up to :math:`2^{5}`.
         -----
         void powers_of_two () {
         =====
           int x = 1;
         =====
           while (x <= 5) {
         =====
             cout << x << "\t" << pow(2, x) << endl;
         =====
             cout << x << "\t" << pow(x, 2) << endl;  #paired
         =====
             x++;
           }
         }

   .. tab:: Q3

      .. parsonsprob:: encapsulation_generalization_3
         :numbered: left
         :adaptive:

         Now let's generalize the function to print out the powers of
         a parameter n up to :math:`n^{5}`.
         Create a function called ``powers_of_n``
         which takes an int n as a parameter.
         -----
         void powers_of_n (int n) {
         =====
         void powers_of_n (string n) {  #paired
         =====
           int x = 1;
         =====
           while (x <= 5) {
         =====
             cout << x << "\t" << pow(n, x) << endl;
         =====
             cout << x << "\t" << pow(5, x) << endl;  #paired
         =====
             x++;
           }
         }

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Function definitions <definition>` and
       :lang:`declarations`
     - :lang:`Functions <functions>`
     - :lang:`comparison operators <operator_comparison>`
