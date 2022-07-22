.. index::
   single: narrowing conversion
   single: widening conversion
   single: truncate

Converting from ``double`` to ``int``
----------------------------------------
As I mentioned, C++ converts ``int`` to ``double`` automatically if necessary,
because no information is lost in the translation. 
This is called a **widening conversion**.

On the other hand,
going from a ``double`` to an ``int`` **truncates** the result.
When a floating point value is *truncated*, all of the information
after the decimal place is lost -- as if it never existed.
The number is **not** rounded up, even if the fractional part is ``.9``.
C++ (usually) warns, but does not prevent this loss of information.
This loss is called a **narrowing conversion**.
Does this mean that once you have an ``double``, it can never be assigned
to a ``int``?

Of course not.

You can explicitly perform these kinds of assignments by using a *typecast*.

.. index::
   single: cast
   single: typecast

The simplest way to convert a floating-point value to an integer is to
use a **typecast**. Typecasting is so called because it allows you to
take a value that belongs to one type and "cast" it into another type
(in the sense of molding or reforming, not throwing).

There are 2 general forms for a cast in C++.

The first syntax for typecasting is like the syntax for a function call.
For example:

::

    constexpr double pi = 3.14159;
    int x = int (pi);

The int function returns an integer, so x gets the value 3. Converting
to an integer always truncates, even if the fraction part is
0.99999999.

The second syntax, called a *named cast* is a bit more verbose.
For example:

::

    constexpr double pi = 3.14159;
    int x = static_cast<int> (pi);

Other than the syntax that appears more like a vector than a function call,
the behavior is identical to the functional form.
One advantage of the named cast is that the entire type name is a parameter,
so:

::

   long long x = static_cast<long long> (pi);   // this works
   long long x = long long (pi);                // this does not: error!


For every built-in type in C++, there is a corresponding function that casts
its argument to the appropriate type.

.. caution::
   With great power comes great responibility.

   Casts are commonly misused.
   Use them with caution, or even better -- not at all.

C++ also inherits from C an older C-style cast syntax.
Unfortunately, this type of cast is even more willing to bypass
narrowing conversions. The C-style syntax places the ``()`` around the type
rather than the value:

::

   constexpr double pi = 3.14159;
   int x = (int) pi;


Casts like this can result in unexpected or implementation defined behavior.
For example:

.. activecode:: convert_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Bad type conversion

   What does this program produce?
   ~~~~
   #include <iostream>

   int main () {
     double d = 2;
     auto p = (long*)&d;
     std::cout << d << ' ' << *p << '\n';  //*

        *p = 666;
        std::cout << d << ' ' << *p << '\n';  //*
      }

Unfortunately, a simple internet search will commonly find C++ code
that still uses the old C-style cast syntax.

Although the language allows us to write this kind of code, you almost never should.

As a general rule, you should avoid casting if possible.
Often a cast is performed when initializing a new variable from an old one.
This is exactly the place where errors can creep in.

If you know that you do not want to allow any narrowing conversions,
then there is a simple remedy, starting with C++11:
Use explicit type construction instead of a cast.

::

   constexpr double pi = 3.14159;
   int x = int (pi);     // compiles. Narrows pi to 3
   int y = int {pi};     // Error. narrowing conversion from 'double' to 'int'


The explicit type construction will never implicitly allow a
type conversion that results in data loss.

Run the examples on each tab to see the results.
In each case, the code is (mostly) the same, but the results may be different.

.. tabbed:: convert_examples

   .. tab:: Explicit type construction

      .. activecode:: convert_summary_AC_1
         :language: cpp
         :compileargs: ['-Wall', '-Wextra', '-Werror', '-std=c++11']
         :nocodelens:
         :caption: Explicit construction

          #include <iostream>
          int main () {
              char p = int{104.5};
              std::cout << p;
          }

      Try changing ``char p`` to ``auto p`` and see what happens.

   .. tab:: Named cast

      .. activecode:: convert_summary_AC_2
         :language: cpp
         :compileargs: ['-Wall', '-Wextra', '-Werror', '-std=c++11']
         :nocodelens:
         :caption: Named cast

          #include <iostream>
          int main () {
              char p = static_cast<int>(104.5);
              std::cout << p;
          }

      Try changing ``char p`` to ``auto p`` and see what happens.

   .. tab:: Functional cast

      .. activecode:: convert_summary_AC_3
         :language: cpp
         :compileargs: ['-Wall', '-Wextra', '-Werror', '-std=c++11']
         :nocodelens:
         :caption: Functional cast

          #include <iostream>
          int main () {
              char p = int(104.5);
              std::cout << p;
          }

      Try changing ``char p`` to ``auto p`` and see what happens.


   .. tab:: C-style cast

      .. activecode:: convert_summary_AC_4
         :language: cpp
         :compileargs: ['-Wall', '-Wextra', '-Werror', '-std=c++11']
         :nocodelens:
         :caption: Bad type conversion

          #include <iostream>
          int main () {
              char p = (int)104.5;
              std::cout << p;
          }

      Try changing ``char p`` to ``auto p`` and see what happens.

To summarize, casting to some type ``T`` ordered from worst to best:

C-style cast
   ``new_value = (T) value;``

   Never protects against inappropriate conversions. Avoid.

Functional cast
   ``new_value = T (value);``

   Protects against inappropriate conversions.
   Allows narrowing conversions.

   Can't be used on types with spaces in the type name,
   such as ``long long`` and ``unsigned int``.

Named cast
   ``new_value = static_cast<T> (value);``

   Protects against inappropriate conversions.
   Allows narrowing conversions.

   Allows converting to types with spaces in the type name,
   such as ``long long`` and ``unsigned int``.

Explicit type construction
   ``new_value = T {value};``

   The ``T{value}`` construction syntax makes it explicit that construction is desired.
   The ``T{value}`` construction syntax doesn't allow narrowing.
   It is the **only safe and general expression** for constructing a value of 
   type ``T`` from a value or an expression. 


.. tabbed:: tab_check

   .. tab:: Q1

      .. mchoice:: double_to_int_1
         :answer_a: temp
         :answer_b: 8
         :answer_c: 7
         :answer_d: 8.0
         :answer_e: 7.0
         :correct: c
         :feedback_a: This is the name of a variable. Only the value of a variable will print with cout.
         :feedback_b: Remember that converting to an integer always truncates.
         :feedback_c: Correct!
         :feedback_d: This is not an integer data type, and it's not the right number.
         :feedback_e: This is not an integer data type.

         In the lab, we measured a temperature of 7.99999999 degrees C, using
         an extremely precise measuring device.  Now we are writing a program
         to perform some calculations with our data.  Consider the following C++
         code.

         ::

             int main () {
               double temp = 7.99999999;
               int approx_temp = int (temp);
               cout << approx_temp;
             }

         What is the value of ``approx_temp``?


   .. tab:: Q2

      .. mchoice:: double_to_int_2

          Your final grade consists of your average performance on exam 1 and exam 2.  
          Your professor is using C++ to grade the exams and allows you to choose which
          method you'd like your exam to be graded.

          ::

                double exam1 = 88.8;
                double exam2 = 72.7;
                double exam2 = 97.9;

          **Method 1:**

          ::

                double final = (int(exam1) + int(exam2) + int(exam3)) / 3;

          **Method 2:**

          ::

                int final = int((exam1 + exam2 + exam3) / 3);

          Which method would you choose and why?

          -   **Method 1:** ``final`` is a ``double``, meaning my final grade will
              have more digits past the decimal, and will be higher than the ``int``
              in Method 2.

              -   Although ``final`` is a ``double``, it doesn't have any digits past
                  the decimal due to the integer division.

          -   **Method 1:** the rounding happens at the beginning, so all three of my
              test scores will be rounded to the nearest ``int``, which in my case, will
              round all of them up.

              -   Converting to an ``int`` always rounds *down*, even if your ``double`` is very 
                  close to the next integer.

          -   **Method 2:** ``final`` is an ``int``, so it gets rounded up.

              -   Converting to an ``int`` always rounds *down*, even if your ``double`` is very 
                  close to the next integer.

          -   **Method 2:** the rounding happens at the very end, so my grade will be higher!

              +   Always save your rounding until the end!

-----

.. admonition:: More to Explore

   - From C++ Core Guidelines

     - Principle P.4 :core:`Ideally, a program should be statically type safe <#p4-ideally-a-program-should-be-statically-type-safe>`
     - Guideline ES.48 :core:`Avoid casts <#es48-avoid-casts>`
     - Guideline ES.46 :core:`Avoid narrowing conversions <#es46-avoid-lossy-narrowing-truncating-arithmetic-conversions>`
     - Guideline ES.64 :core:`Use the T{e} notation for construction <#es64-use-the-tenotation-for-construction>`

   - :lang:`Explicit casting <explicit_cast>` from cppreference.com

