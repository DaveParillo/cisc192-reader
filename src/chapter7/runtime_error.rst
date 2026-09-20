A run-time error
----------------

Way back in Section `[run-time] <#run-time>`__ I talked about run-time
errors, which are errors that don't appear until a program has started
running.

The ``at()`` member function checks its index. If the index is greater than
or equal to the string's ``size()``, it throws ``std::out_of_range``.
A negative argument is converted to an unsigned index and is also out of
range. If the exception is not caught, the program terminates; the exact
error message depends on your development environment.

Running the active code below will result in a runtime error. Can you fix 
it so that we print out the first letter and last letter of string ``greeting`` instead
of indexing out of range?

.. tb-code:: cpp
   :name: runtime_error_AC_1
   :caption: Example runtime_error_AC_1
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>
   #include <string>

   int main() {
       std::string greeting = "Hello world";
       std::cout << "The first letter is " << greeting.at(-1) << '\n';
       std::cout << "The last letter is " << greeting.at(greeting.length()) << '\n';
   }

.. note:: Range-checked access vs. unchecked access

   In C++20, array indexing and the ``[]`` operators of ``std::string`` and
   ``std::vector`` do not provide the range checks performed by ``at()``.
   An invalid unchecked access can cause **undefined behavior**: the program
   might crash, produce unexpected results, or appear to work. You cannot
   rely on either an error message or successful execution.

   For example, ``mydata[-99]`` is invalid for ``int mydata[3] = {1, 2, 3};``.
   Use a valid index regardless of whether a particular run reports an error.

   String indexing has one special case: reading ``text[text.size()]``
   yields the terminating null character, not a character of the string's
   contents. To visit the characters, use indices strictly less than
   ``text.size()``. In contrast, ``text.at(text.size())`` throws an exception.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-click::
         :name: runtime_error_1

         Click on each out-of-range access. Consider each expression independently.

         .. code-block:: cpp

            int main() {
                string fruit = "apple";
                char a = fruit[0];
                char b = fruit[9];
                char c = fruit.at(0);
                char d = fruit.at(9);
                cout << fruit << '\n';
                cout <<  fruit[-4]  << '\n';
                char e = fruit.at(-4);
                cout <<  fruit[4]  << '\n';
            }


         .. tb-miss:: text:int main() {

            at() throws for an out-of-range index; invalid unchecked accesses have undefined behavior.

         .. tb-miss:: text:string fruit = "apple";

            at() throws for an out-of-range index; invalid unchecked accesses have undefined behavior.

         .. tb-miss:: text:fruit[0];

            at() throws for an out-of-range index; invalid unchecked accesses have undefined behavior.

         .. tb-hit:: text:fruit[9];

            Correct.

         .. tb-miss:: text:fruit.at(0);

            at() throws for an out-of-range index; invalid unchecked accesses have undefined behavior.

         .. tb-hit:: text:fruit.at(9);

            Correct.

         .. tb-miss:: text:cout << fruit << '\n';

            at() throws for an out-of-range index; invalid unchecked accesses have undefined behavior.

         .. tb-hit:: text:fruit[-4]

            Correct.

         .. tb-hit:: text:fruit.at(-4);

            Correct.

         .. tb-miss:: text:fruit[4]

            at() throws for an out-of-range index; invalid unchecked accesses have undefined behavior.

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: runtime_error_2

         Construct a block of code that correctly changes the string to say "cat in the hat" instead of "cat on the mat", then print it.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               string sentence = "cat on the mat";
            {{endgroup}}
            {{group}}
               sentence[4] = 'i';
            {{endgroup}}
            {{distractor}}
            {{group}}
               sentence[5] = 'i'; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               sentence[3] = 'i'; #distractor
            {{endgroup}}
            {{group}}
               sentence[11] = 'h';
            {{endgroup}}
            {{distractor}}
            {{group}}
               sentence [12] = 'h'; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               sentence[11] = 'h' #distractor
            {{endgroup}}
            {{group}}
               cout << sentence << '\n';
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

