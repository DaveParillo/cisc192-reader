Variables
---------

.. index::
   single: variable

One of the most powerful features of a programming language is the
ability to manipulate **variables**. A variable is a named location that
stores a value.

Just as there are different types of values (integer, character, etc.),
there are different types of variables. When you create a new variable,
you have to declare what type it is. 

.. note::
   In C++, integer variables are declared as type ``int`` and character variables 
   are declared as type ``char``.

The following statement creates a new variable named fred that has type ``char``.

::

    char fred;

.. index::
   single: declaration
   single: declaration statement

This kind of statement is called a **declaration**.

The type of a variable determines what kind of values it can store. A
``char`` variable can store a character, and it should come as no surprise
that ``int`` variables can store integers.

There are several types in C++ that can store ``string`` values, but we are
going to skip that for now (see Chapter 7).

To create an integer variable, the syntax is

::

    int bob;

where bob is the arbitrary name you made up for the variable. In
general, you will want to make up variable names that indicate what you
plan to do with the variable. For example, if you saw these variable
declarations:

::

    char first_letter;
    char last_letter;
    int hour, minute;

you could probably make a good guess at what values would be stored in
them. This example also demonstrates the syntax for declaring multiple
variables with the same type: hour and minute are both integers (``int``
type).

Although the language allows this, it should be avoided.
It is easy to accidentally create uninitialized variables,
one of the most common sources of error in C++ programs.
Consider the following:

.. tb-code:: cpp
   :name: variables_AC_1
   :caption: Bad variable declaration
   :compileargs: ['-std=c++11', '-Wall', '-Wextra']

   #include <iostream>

   int main () {
       int hour, minute = 59;
       std::cout << hour << ':' << minute;
   }

What do you think this program will output?

What should it output?

.. tb-reveal:: Details
   :name: variables_ub_reveal

   Uninitialized variables are an example of
   *undefined behavior*.

   The C++ language does specify what should happen here.
   Most compilers will **warn** that you did this,
   but none will stop you from compiling and running
   this program unless you ask it to.

   The value of ``hour`` could be 0, but might also be
   any value constructed from the bits that just happened
   to be stored in memory when ``hour`` was created.

   Many compilers will allow something along the lines of:

   .. code-block:: text

      -Werror=uninitialized

   To force an error if an uninitialized variable is detected.

.. index:: naming conventions

**Naming conventions**

C++ is a multi-paradigm language with a long history.
Over the years many different groups have developed different
programming styles for C++.
None of them are wrong as long as they apply their rules consistently.

Since this book intends to teach C++, it follows the conventions
used in the C++ Standard Library.
For more information about naming conventions, see the
:core:`Naming conventions <#S-naming>`
section of the C++ Core Guidelines,
edited by Bjarne Stroustrup and Herb Sutter.

If you continue programming in C++, you will undoubtedly encounter
variables that use other styles.

That's ok. You can't follow everyone's conventions.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-blank::
         :name: variables_3

         A(n) {{blank}} is a name given to a location in memory used to keep 
         track of a value.

         .. tb-answer::
            :match: variable
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q2

      .. tb-blank::
         :name: variables_1

         Take a look at the code block below:

         ::

             char tom;

         It's an example of a(n) {{blank}} statement.

         .. tb-answer::
            :match: declaration
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q3

      .. tb-click::
         :name: variables2_0

         Click on all instances of integer VARIABLES.

         .. code-block:: cpp

            int main() {
                int x = 7;
                int y = 10;
                char c = '8';
                while (x < y) {
                    cout << c << '\n';;
                    x++;
                }
                double d = 9;
                int z = x + y;
                cout << "It's the year " << 2000 + z << '!';
            }



         .. tb-miss:: text:int main() {

            Try again!

         .. tb-hit:: text:x

            Correct.

         .. tb-miss:: text:7

            Try again!

         .. tb-hit:: text:y

            Correct.

         .. tb-miss:: text:10

            Try again!

         .. tb-miss:: text:char c

            Try again!

         .. tb-miss:: text:8

            Try again!

         .. tb-hit:: text:x#2

            Correct.

         .. tb-hit:: text:y#2

            Correct.

         .. tb-hit:: text:x#3

            Correct.

         .. tb-miss:: text:d

            Try again!

         .. tb-miss:: text:9

            Try again!

         .. tb-hit:: text:z

            Correct.

         .. tb-hit:: text:x#4

            Correct.

         .. tb-hit:: text:y#3

            Correct.

         .. tb-miss:: text:2000

            Try again!

         .. tb-hit:: text:z#2

            Correct.

   .. tb-tab:: Q4

      .. tb-click::
         :name: variables2_1

         Click on all instances of character VARIABLES.

         .. code-block:: cpp

            int main() {
                char init1 = 'K';
                string init2 = "t";
                cout << init1 << '+' << init2 << '\n';
                string init3 = "C";
                char init4 = 'J';
                cout << init3 << '+' << init4 << '\n';
                string c = "Carved their initials in a tree!";
                cout << c;
            }



         .. tb-hit:: text:init1

            Correct.

         .. tb-miss:: text:K

            Try again!

         .. tb-miss:: text:init2

            Try again!

         .. tb-miss:: text:"t"

            Try again!

         .. tb-hit:: text:init1#2

            Correct.

         .. tb-miss:: text:+

            Try again!

         .. tb-miss:: text:init2#2

            Try again!

         .. tb-miss:: text:init3

            Try again!

         .. tb-miss:: text:"C"

            Try again!

         .. tb-hit:: text:init4

            Correct.

         .. tb-miss:: text:J

            Try again!

         .. tb-miss:: text:init3#2

            Try again!

         .. tb-miss:: text:+#2

            Try again!

         .. tb-hit:: text:init4#2

            Correct.

         .. tb-miss:: text:c

            Try again!

         .. tb-miss:: text:"Carved their initials in a tree!"

            Try again!

         .. tb-miss:: text:c#2

            Try again!

   .. tb-tab:: Q5

      .. tb-match::
         :name: variables_2

         Match the variable to the kind of value it can store.


         char joe;
            'x'
         string ten;
            "Joe"
         int x;
            10

   .. tb-tab:: Q6

      .. tb-parsons::
         :name: variables_4

         Write code that creates the variables name, first_initial, and number_of_siblings IN THAT ORDER.  It is up to you to choose the correct types for these variables.

         .. code-block:: cpp

            {{group}}
            string name;
            {{endgroup}}
            {{distractor}}
            {{group}}
            string name
            {{endgroup}}
            {{group}}
            char first_initial;
            {{endgroup}}
            {{distractor}}
            {{group}}
            char first_initial
            {{endgroup}}
            {{distractor}}
            {{group}}
            string first_initial;
            {{endgroup}}
            {{distractor}}
            {{group}}
            string first_initial
            {{endgroup}}
            {{group}}
            int number_of_siblings;
            {{endgroup}}
            {{distractor}}
            {{group}}
            int number_of_siblings
            {{endgroup}}
            {{distractor}}
            {{group}}
            double number_of_siblings;
            {{endgroup}}
            {{distractor}}
            {{group}}
            double number_of_siblings
            {{endgroup}}

-----

.. admonition:: More to Explore

   - From cppreference.com

     - C++ :lang:`identifiers`

   - C++ Core Guidelines :core:`naming conventions <#S-naming>`.
   - `Naming conventions <https://google.github.io/styleguide/cppguide.html#Variable_Names>`__
     from Google C++ style guide.
