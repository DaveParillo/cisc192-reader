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

.. activecode:: variables_AC_1
   :language: cpp
   :compileargs: ['-std=c++11', '-Wall', '-Wextra']
   :nocodelens:
   :caption: Bad variable declaration

   #include <iostream>

   int main () {
       int hour, minute = 59;
       std::cout << hour << ':' << minute;
   }

What do you think this program will output?

What should it output?

.. reveal:: variables_ub_reveal

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

.. tabbed:: tab_check

   .. tab:: Q1

      .. fillintheblank:: variables_3

         A(n) |blank| is a name given to a location in memory used to keep 
         track of a value.

         - :[Vv][Aa][Rr][Ii][Aa][Bb][Ll][Ee]: Correct!
           :.*: Try again!


   .. tab:: Q2

      .. fillintheblank:: variables_1

         Take a look at the code block below:
         
         ::

             char tom;

         It's an example of a(n) |blank| statement.

         - :[Dd][Ee][Cc][Ll][Aa][Rr][Aa][Tt][Ii][Oo][Nn]: Correct!
           :.*: Try again!


   .. tab:: Q3

      .. clickablearea:: variables2_0
          :question: Click on all instances of integer VARIABLES.
          :iscode:
          :feedback: Try again!

          :click-incorrect:int main() {:endclick:
              int :click-correct:x:endclick: = :click-incorrect:7:endclick:;
              int :click-correct:y:endclick: = :click-incorrect:10:endclick:;
              :click-incorrect:char c:endclick: = :click-incorrect:'8':endclick:;
              while (:click-correct:x:endclick: < :click-correct:y:endclick:) {
                  cout << :click-incorrect:c:endclick: << '\n';;
                  :click-correct:x:endclick:++;
              }
              double :click-incorrect:d:endclick: = :click-incorrect:9:endclick:;
              int :click-correct:z:endclick: = :click-correct:x:endclick: + :click-correct:y:endclick:;
              cout << "It's the year " << :click-incorrect:2000:endclick: + :click-correct:z:endclick: << "!";
          }


   .. tab:: Q4

      .. clickablearea:: variables2_1
          :question: Click on all instances of character VARIABLES.
          :iscode:
          :feedback: Try again!

          int main() {
              char :click-correct:init1:endclick: = :click-incorrect:'K':endclick:;
              string :click-incorrect:init2:endclick: = :click-incorrect:"T":endclick:;
              cout << :click-correct:init1:endclick: << :click-incorrect:"+":endclick: << :click-incorrect:init2:endclick: << '\n';
              string :click-incorrect:init3:endclick: = :click-incorrect:"C":endclick:;
              char :click-correct:init4:endclick: = :click-incorrect:'J':endclick:;
              cout << :click-incorrect:init3:endclick: << :click-incorrect:'+':endclick: << :click-correct:init4:endclick: << '\n';
              string :click-incorrect:c:endclick: = :click-incorrect:"Carved their initials in a tree!":endclick:;
              cout << :click-incorrect:c:endclick:;
          }


   .. tab:: Q5

      .. dragndrop:: variables_2
         :feedback: Ideally, you want your variables to be named according to what they represent.  Not the case here!  Try again!
         :match_1:  char joe;|||'x'
         :match_2: string ten;|||"Joe"
         :match_3: int x;|||10

         Match the variable to the kind of value it can store.


   .. tab:: Q6

      .. parsonsprob:: variables_4
         :numbered: left
         :adaptive:
         
         Write code that creates the variables name, first_initial, and number_of_siblings IN THAT ORDER.  It is up to you to choose the correct types for these variables.
         -----
         string name;
         =====
         string name #paired
         =====
         char first_initial;
         =====
         char first_initial #paired
         =====
         string first_initial; #paired
         =====
         string first_initial #paired
         =====
         int number_of_siblings;
         =====
         int number_of_siblings #paired
         =====
         double number_of_siblings; #paired
         =====
         double number_of_siblings #paired


-----

.. admonition:: More to Explore

   - From cppreference.com

     - C++ :lang:`identifiers`

   - C++ Core Guidelines :core:`naming conventions <#S-naming>`.
   - `Naming conventions <https://google.github.io/styleguide/cppguide.html#Variable_Names>`__
     from Google C++ style guide.

