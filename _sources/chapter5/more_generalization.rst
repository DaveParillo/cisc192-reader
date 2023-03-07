More generalization
-------------------

As another example of generalization, imagine you wanted a program that
would print a multiplication table of any size, not just the 6x6 table.
You could add a parameter to ``multiples_table``:

::

   void multiples_table (int table_size) {
     int i = 1;
     while (i <= table_size) {
       print_multiples (i);
       i = i + 1;
     }
   }

I replaced the value 6 with the parameter ``table_size``. If I call
``multiples_table`` with the argument 7, I get

::

   1   2   3   4   5   6
   2   4   6   8   10   12
   3   6   9   12   15   18
   4   8   12   16   20   24
   5   10   15   20   25   30
   6   12   18   24   30   36
   7   14   21   28   35   42

which is fine, except that I probably want the table to be square (same
number of rows and columns), which means I have to add another parameter
to ``print_multiples``, to specify how many columns the table should
have.

Just to be annoying, I will also call this parameter ``table_size``,
demonstrating that different functions can have parameters with the same
name (just like local variables):

::

   void print_multiples (int n, int table_size) {
     int i = 1;
     while (i <= table_size) {
       cout << n*i << "   ";
       i = i + 1;
     }
     cout << endl;
   }

   void multiples_table (int table_size) {
     int i = 1;
     while (i <= table_size) {
       print_multiples (i, table_size);
       i = i + 1;
     }
   }

Notice that when I added a new parameter, I had to change the first line
of the function (the interface or prototype), and I also had to change
the place where the function is called in ``multiples_table``. As
expected, this program generates a square 7x7 table:

::

   1   2   3   4   5   6   7
   2   4   6   8   10   12   14
   3   6   9   12   15   18   21
   4   8   12   16   20   24   28
   5   10   15   20   25   30   35
   6   12   18   24   30   36   42
   7   14   21   28   35   42   49

.. activecode:: more_generalization_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Two-dimensional tables

   The active code below uses the updated ``multiples_table`` function.
   Notice that with generalization, we can create multiplication tables of
   multiple sizes by simply changing the parameter passed into ``multiples_table``.
   Run the active code to see what happens!
   ~~~~
   #include <iostream>

   void print_multiples (int n, int table_size) {
     using std::cout;
     int i = 1;
     while (i <= table_size) {
       cout << n*i << '\t';
       i = i + 1;
     }
     cout << '\n';
   }

   void multiples_table (int table_size) {
     int i = 1;
     while (i <= table_size) {
       print_multiples (i, table_size);
       i = i + 1;
     }
   }

   int main() {
     multiples_table(7);
   }

When you generalize a function appropriately, you often find that the
resulting program has capabilities you did not intend. For example, you
might notice that the multiplication table is symmetric, because
:math:`ab = ba`, so all the entries in the table appear twice. You could
save ink by printing only half the table. To do that, you only have to
change one line of ``multiples_table``. Change

::

         print_multiples (i, table_size);

to

::

         print_multiples (i, i);

and you get

::

   1
   2   4
   3   6   9
   4   8   12   16
   5   10   15   20   25
   6   12   18   24   30   36
   7   14   21   28   35   42   49

I’ll leave it up to you to figure out how it works.

We can generalize it a bit further by not hard-coding the table size.
We change the parameter to a **default parameter**:

.. activecode:: more_generalization_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-Wextra', '-Wpedantic', '-std=c++11']
   :nocodelens:
   :caption: Table with default parameters

   Notice the new parameter passed to the ``multiples_table`` function.
   It includes ``= 6`` after the parameter name.
   This indicates a **default value** for ``table_size``.
   This means that if a value is not passed to the function,
   then the default value is used.

   ~~~~
   #include <iostream>

   void print_multiples (int n, int table_size) {
     using std::cout;
     int i = 1;
     while (i <= table_size) {
       cout << n*i << '\t';
       i = i + 1;
     }
     cout << '\n';
   }

   void multiples_table (int table_size = 6) {
     int i = 1;
     while (i <= table_size) {
       print_multiples (i, table_size);
       i = i + 1;
     }
   }

   int main() {
     multiples_table();
   }

Other than providing a bit more flexibility in how ``multiple_tables``
is called, we have not changed this program.
We **do** have a bit more to be careful about though.
What values might be passed that would cause our program to behave
unexpectedly?

Also be aware that a default parameter also means that

::

   void multiples_table(int table_size = 6);

implicitly defines a function with this signature:

::

   void multiples_table();

with the value of ``table_size`` set to ``6``.
Trying to define both of these functions is a compile error.
This makes perfect sense if you consider what the compiler needs to do.
You have two functions:

::

   void multiples_table(int table_size = 6);
   void multiples_table();

Which of these two functions is being referred to in main:

::

   int main() {
     multiples_table();
   }

Is is the version that takes no parameters,
or the function that defaults to ``6``?
There is no way to know simply by looking at the code.
The compiler can't know either, so it will report an error.


.. tabbed:: self_check

   .. tab:: Q1

      .. activecode:: more_generalization_AC_3
         :language: cpp
         :compileargs: ['-Wall', '-Wextra', '-Wpedantic', '-std=c++11']
         :nocodelens:
         :caption: Two-dimensional tables

         Modify the previous program so that it only prints
         half the multiplication table.

         Run the active code to see how you did!
         ~~~~
         #include <iostream>
         using std::cout;

         void print_multiples (int n, int table_size) {
           int i = 1;
           while (i <= table_size) {
             cout << n*i << '\t';
             i = i + 1;
           }
           cout << '\n';
         }

         void multiples_table (int table_size) {
           int i = 1;
           while (i <= table_size) {
             print_multiples (i, table_size);
             i = i + 1;
           }
         }

         int main() {
           multiples_table(7);
         }

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Function definitions <definition>` and
       :lang:`declarations`
     - :lang:`Functions <functions>`
     - :lang:`Overload resolution <overload_resolution>`

