Increment and decrement operators
---------------------------------
.. index::
   pair: operators; increment operator
   pair: operators; decrement operator

Incrementing and decrementing are such common operations that C++
provides special operators for them. The ``++`` operator adds one to the
current value of an ``int``, ``char`` or ``double``, and ``–`` subtracts
one. Neither operator works on ``string``\ s, and neither *should* be
used on ``bool``\ s.

Technically, it is legal to increment a variable and use it in an
expression at the same time. For example, you might see something like:

::

     cout << i++ << '\n';

Looking at this, it is not clear whether the increment will take effect
before or after the value is displayed. Because expressions like this
tend to be confusing, I would discourage you from using them. In fact,
to discourage you even more, I’m not going to tell you what the result
is. If you really want to know, you can try it.

The active code demonstrates how using increment operators
with ``cout`` statements can be confusing.

.. tb-code:: cpp
   :name: increment_decrement_AC_1
   :caption: Looping and counting
   :compileargs: ['-Wall', '-std=c++11']

   #include <cstddef>
   #include <iostream>
   using namespace std;

   using std::size_t;

   int main() {
      int x = 0;
      // We incremented x, so it should print out 1 now right?
      cout << x++ << '\n'; // Weird, x is still 0?
   }

If you're curious about this, feel free to search up about prefix and postfix 
increment operators. But for now, just avoid incrementing a variable 
and using it in an expression at the same time.

Using the increment operators, we can rewrite the letter-counter:

::

     std::size_t index = 0;
     while (index < fruit.size()) {
       if (fruit[index] == 'a') {
         count++;
       }
       index++;
     }

The active code below adds increment operators to our old letter-counter.

.. tb-code:: cpp
   :name: increment_decrement_AC_2
   :caption: Looping and counting

   #include <cstddef>
   #include <iostream>
   #include <string>

   using std::size_t;

   int main() {
      std::string fruit = "banana";
      std::size_t count = 0;

      std::size_t index = 0;
      while (index < fruit.size()) {
          if (fruit[index] == 'a') {
              count++;
          }
          index++;
      }
      std::cout << count;
   }

It is a common error to write something like

::

     index = index++;             // WRONG!!

Unfortunately, this is syntactically legal, so the compiler will not
warn you. The effect of this statement is to leave the value of
``index`` unchanged. This is often a difficult bug to track down.

.. warning::
   Remember, you can write ``index = index +1;``, or you can write
   ``index++;``, but you shouldn’t mix them.


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-click::
         :name: increment_decrement_1

         Click on the incorrect or not suggested increment statements.

         .. code-block:: cpp

            int main() {
                count = count + 1;
                index++;
                count = count++;
                cout << x++ << '\n';
                count--; 
            }


         .. tb-miss:: text:int main() {

            Re-read the text above and try again.

         .. tb-miss:: text:count = count + 1;

            Re-read the text above and try again.

         .. tb-miss:: text:index++;

            Re-read the text above and try again.

         .. tb-hit:: text:count = count++;

            Correct.

         .. tb-hit:: text:cout << x++ << '\n';

            Correct.

         .. tb-miss:: text:count--;

            Re-read the text above and try again.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: increment_decrement_2

         What does the following code print?

         .. code-block:: cpp
            :linenos:

            int x = -5;
            while (x < 0) {
              x++;
              cout << x << ' ';
            }

         - [ ] 5 4 3 2 1

           Notice that x is negative.
         - [ ] -5 -4 -3 -2 -1

           Notice that the value of x is incremented before it is printed.
         - [x] -4 -3 -2 -1 0

           The value of x is incremented before it is printed so the first value printed is -4.

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: increment_decrement_3

         Print every number from 1-10 in this format: "Number 1". Each number should be on its own line.

         .. code-block:: cpp

            {{group}}
            int x = 1;
            {{endgroup}}
            {{distractor}}
            {{group}}
            x = 1; #distractor
            {{endgroup}}
            {{group}}
            while (x <= 10) {
            {{endgroup}}
            {{group}}
                cout << "Number " << x << '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
                cout << "Number " << x; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
                --x; #distractor
            {{endgroup}}
            {{group}}
                x++;
            }
            {{endgroup}}

