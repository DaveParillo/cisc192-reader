.. index::
   pair: function; declaration and definition

Adding New Functions
--------------------

So far we have only been using the functions that are built into C++,
but it is also possible to add new functions. Actually, we have already
seen one function definition: ``main``. The function named ``main`` is special
because it indicates where the execution of the program begins, but the
syntax for ``main`` is the same as for any other function definition:

::

    RETURN_TYPE NAME ( LIST OF PARAMETERS ) {
      STATEMENTS
    }

The first line of this definition is called the 
:lang:`declaration <declarations>`.
A declaration introduces a new name into the program.
For functions, the function name and all of the parameter types must unique.
In the previous example, the declaration also included the
:lang:`definition`, however, the declaration can appear as a 
separate statement:

::

    RETURN_TYPE NAME ( LIST OF PARAMETERS );

Note the semicolon ``;`` at the end of the statement, just like any other
legal statement in C++.

.. index::
   single: function call

You can make up any name you want for your function, except that you
can’t call it ``main`` or any other C++ keyword. 
It should also not begin with an underscore ``_`` --
variables and function that start with an underscore are reserved
for the C++ implementation.
The list of parameters specifies what information -- 
if any -- you have to provide in order to use, 
or **call**, the new function.

``main`` doesn't take any parameters, as indicated by the empty parentheses
() in it’s definition. The first couple of functions we are going to
write also have no parameters, so the syntax looks like this:

::

    void new_line () {
      cout << '\n';
    }

This function is named ``new_line``; it contains only a single statement,
which outputs a new line character, represented by the special character
``'\n'``.

In ``main`` we can call this new function using syntax that is similar to
the way we call the built-in C++ commands:

::

    int main () {
      cout << "First Line.\n";
      new_line ();
      cout << "Second Line.\n";
      return 0;
    }

The output of this program is

::

    First line.

    Second line.

Notice the extra space between the two lines. What if we wanted more
space between the lines? We could call the same function repeatedly:

::

    int main () {
      cout << "First Line.\n";
      new_line ();
      new_line ();
      new_line ();
      cout << "Second Line.\n";
      return 0;
    }

Or we could write a new function, named ``three_line``, that prints three new
lines:


Here we define the three_line function, which calls the new_line function
three times.  The result is a function that prints three lines after it
is called.

.. tb-code:: cpp
   :name: new_functions_AC_1
   :caption: The three_line Function
   :compileargs: ['-Wall', '-std=c++11']

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


You should notice a few things about this program:

-  You can call the same procedure repeatedly. In fact, it is quite
   common and useful to do so.

-  You can have one function call another function. In this case, ``main``
   calls ``three_line`` and three_line calls ``new_line``.
   Again, this is common and useful.

-  The space between the function name and the function parentheses ``()``
   is not required. These space is included here to make it easier to see,
   but in most book examples, you will see no space after the function name.

-  In ``three_line`` I wrote three statements all on the same line, which is
   syntactically legal (remember that spaces and new lines usually don’t
   change the meaning of a program). On the other hand, **it is usually a
   better idea to put each statement on a line by itself**, to make your
   program easy to read. I sometimes break that rule in this book to
   save space.

.. note::
   In general, you'll want to write your code so that it is easy for others
   to follow.  This is especially important if you choose computer science
   as a career!

So far, it may not be clear why it is worth the trouble to create all
these new functions. Actually, there are a lot of reasons, but this
example only demonstrates two:

#. Creating a new function gives you an opportunity to give a name to a
   group of statements. Functions can simplify a program by hiding a
   complex computation behind a single command, and by using English
   words in place of arcane code. Which is clearer, ``new_line`` or ``cout <<
   '\n'``?

#. Creating a new function can make a program smaller by eliminating
   repetitive code. For example, a short way to print nine consecutive
   new lines is to call three_line three times. How would you print 27
   new lines?


.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: new_functions_mc_1

         Which of these statements is false about functions?

         - [x] You can name a function anything you want.

           +   You can't name a function the same name as a reserved keyword.

         - [ ] You can have a function with several parameters or a function with none.

           -   This is true! However, you must always use parentheses.

         - [ ] You can call a function inside of another function.

           -   This is true! It is common and useful.

         - [ ] You can write multiple statements on one line of a function.

           -   This is true! As long as each statement ends with a semicolon.


   .. tb-tab:: Q2

      .. tb-click::
         :name: new_functions_2

         Click on all function DECLARATIONS.

         .. code-block:: cpp

            void print_x() {
                cout << 'X';
            }

            void print_var(int a) {
                cout << a;
            }  

            int main() {
                int x = 7;
                print_var(x); 
                if (x < 10) {
                    x = x - 1;
                }
                print_x();
                int y = 3;
                double result = x / y;
                print_var(result);
                return 0;
            }



         .. tb-hit:: text:void print_x() {

            Correct.

         .. tb-miss:: text:cout << 'X';

            Remember, the operator '=' is used for assignment.

         .. tb-hit:: text:void print_var(int a) {

            Correct.

         .. tb-miss:: text:cout << a;

            Remember, the operator '=' is used for assignment.

         .. tb-hit:: text:int main() {

            Correct.

         .. tb-miss:: text:int x = 7;

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:print_var(x);

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:if (x < 10) {

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:x = x - 1;

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:print_x();

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:int y = 3;

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:double result = x / y;

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:print_var(result);

            Remember, the operator '=' is used for assignment.

   .. tb-tab:: Q3

      .. tb-click::
         :name: new_functions_3

         Click on all function CALLS.

         .. code-block:: cpp

            void print_x() {
                cout << 'X';
            }

            void print_var(int a) {
                cout << a;
            }  

            int main() {
                int x = 7;
                print_var(x);  
                if (x < 10) {
                    x = x - 1;
                }
                print_x();     
                int y = 3;
                double result = x / y;
                print_var(result);
                return 0;
            }


         .. tb-miss:: text:void print_x() {

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:cout << 'X';

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:void print_var(int a) {

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:cout << a;

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:int main() {

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:int x = 7;

            Remember, the operator '=' is used for assignment.

         .. tb-hit:: text:print_var(x);

            Correct.

         .. tb-miss:: text:if (x < 10) {

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:x = x - 1;

            Remember, the operator '=' is used for assignment.

         .. tb-hit:: text:print_x();

            Correct.

         .. tb-miss:: text:int y = 3;

            Remember, the operator '=' is used for assignment.

         .. tb-miss:: text:double result = x / y;

            Remember, the operator '=' is used for assignment.

         .. tb-hit:: text:print_var(result);

            Correct.

   .. tb-tab:: Q4

      .. tb-parsons::
         :name: new_functions_4

         Construct a function that correctly prints the perimeter of a rectangle.

         .. code-block:: cpp

            {{group}}
            void perimeter (int length,int width) {
            {{endgroup}}
            {{group}}
            int twice_length = 2*length;
            {{endgroup}}
            {{group}}
            int twice_width = 2*width;
            {{endgroup}}
            {{group}}
            int perimeter_value = twice_length + twice_width;
            {{endgroup}}
            {{group}}
            cout << perimeter_value<<'\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
            return parameter_value; #distractor
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

