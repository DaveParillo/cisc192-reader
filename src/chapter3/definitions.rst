Definitions and Uses
--------------------

Pulling together all the code fragments from the previous section, the
whole program looks like this:

.. tb-code:: cpp
   :name: function_definitions_AC_1
   :caption: Using function definitions
   :compileargs: ['-Wall', '-Wextra', '-Werror', '-std=c++11']

   #include <iostream>

   void new_line () {
     std::cout << '\n';
   }

   void three_line () {
     new_line ();  new_line ();  new_line ();
   }

   int main () {
     std::cout << "First Line.\n";
     three_line ();
     std::cout << "Second Line.\n";
     return 0;
   }

This program contains three function definitions: ``new_line``, ``three_line``,
and ``main``.

Inside the definition of ``main``, there is a statement that uses or calls
``three_line``. Similarly, ``three_line`` calls ``new_line`` three times. Notice that
the definition of each function appears above the place where it is
used.

This is necessary in C++; the declaration or definition of a function
must appear before (above) the first use of the function. 
It is possible for only the declarations for appear before a function is used
and for the definition to appear later.
These are called **forward declarations**.

.. tb-code:: cpp
   :name: function_definitions_AC_2
   :caption: Using function definitions
   :compileargs: ['-Wall', '-Wextra', '-Werror', '-std=c++11']

   #include <iostream>

   // forward declarations 
   void new_line ();
   void three_line ();

   int main () {
     std::cout << "First Line.\n";
     three_line ();
     std::cout << "Second Line.\n";
     return 0;
   }

   void new_line () {
     std::cout << '\n';
   }

   void three_line () {
     new_line ();  new_line ();  new_line ();
   }


.. admonition:: Try This!

   You should try compiling both programs with the functions in 
   a different order and see what error messages you get.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-blank::
         :name: defns_uses_1

         The function declaration or  definition must be written {{{{blank}}}}
         the first use of the function.

         .. tb-answer::
            :match: ([Bb][Ee][Ff][Oo][Rr][Ee])|([Aa][Bb][Oo][Vv][Ee])
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q2

      .. tb-choice::
         :name: defns_uses_2

         h of the following is a correct function declaration?

         ``void print_name()``

         - [ ] This declaration is missing a ``;``.

         ``total_cost_after_tax () {``

         - [x] This declaration is missing a return type.

         ``void todays_weather ();``

         +   Correct!

         ``void final_grade {``

         - [ ] This declaration is missing parentheses. Even if a function does not take in any parameters, empty parentheses should be used.


   .. tb-tab:: Q3

      .. tb-parsons::
         :name: defns_uses_3

         Construct a block of code that correctly defines the add_two function.

         .. code-block:: cpp

            {{group}}
            int add_two(int x) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            int add_two(int x); #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            add_two(int x) #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            int add_two(int x) #distractor
            {{endgroup}}
            {{group}}
             int result = x + 2;
            {{endgroup}}
            {{group}}
             return result;
            {{endgroup}}
            {{distractor}}
            {{group}}
             return x; #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Function definitions <definition>` and
       :lang:`declarations`
     - :lang:`Functions <functions>`

