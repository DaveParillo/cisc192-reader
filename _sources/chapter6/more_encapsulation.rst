More encapsulation
------------------

To demonstrate encapsulation again, I’ll take the code from the previous
section and wrap it up in a function:

::

   void multiples_table () {
     int i = 1;
     while (i <= 6) {
       print_multiples (i);
       i = i + 1;
     }
   }

The process I am demonstrating is a common development plan. You develop
code gradually by adding lines to ``main`` or someplace else, and then
when you get it working, you extract it and wrap it up in a function.

The reason this is useful is that you sometimes don’t know when you
start writing exactly how to divide the program into functions. This
approach lets you design as you go along.

.. activecode:: more_encapsulation_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Two-dimensional tables

   The active code below uses the ``multiples_table`` function.
   Run the active code to see what happens!
   ~~~~
   #include <iostream>

   void print_multiples (int n) {
     using std::cout;
     int i = 1;
     while (i <= 6) {
       cout << n*i << '\t';
       i = i + 1;
     }
     cout << '\n';
   }

   void multiples_table() {
     int i = 1;
     while (i <= 6) {
       print_multiples (i);
       i = i + 1;
     }
   }

   int main() {
     multiples_table();
   }

