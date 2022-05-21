One more example
----------------

In the previous example I used temporary variables to spell out the
steps, and to make the code easier to debug, but I could have saved a
few lines:

.. activecode:: recursion_ex_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Factorial Recursion

   This program uses recursion to calculate the factorial of
   the passed argument.  It is the condensed version of the
   example on the previous page.
   ~~~~
   #include <iostream>

   int factorial (int n) {
       if (n == 0) {
           return 1;
       } 
       return n * factorial (n-1);
   }

   int main () {
       std::cout << factorial(3) << std::endl;
   }

From now on I will tend to use the more concise version, but I recommend
that you use the more explicit version while you are developing code.
When you have it working, you can tighten it up, if you are feeling
inspired.

After factorial, the classic example of a recursively-defined
mathematical function is fibonacci, which has the following definition:

.. math::

   \begin{aligned}
   && fibonacci(0) = 1 \\
   && fibonacci(1) = 1 \\
   && fibonacci(n) = fibonacci(n-1) + fibonacci(n-2);\end{aligned}

Translated into C++, this is:


.. activecode:: recursion_ex_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Fibonacci Recursion

   This program uses recursion to calculate the nth number in the
   fibonacci sequence.
   ~~~~
   #include <iostream>

   int fibonacci (int n) {
       if (n == 0 || n == 1) {
           return 1;
       } 
       return fibonacci (n-1) + fibonacci (n-2);
   }

   int main () {
       std::cout << fibonacci(3) << std::endl;
   }


If you try to follow the flow of execution here, even for fairly small
values of n, your head explodes. But according to the leap of faith, if
we assume that the two recursive calls (yes, you can make two recursive
calls) work correctly, then it is clear that we get the right result by
adding them together.

