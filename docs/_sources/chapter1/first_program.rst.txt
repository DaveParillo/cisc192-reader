.. _hello:

The First Program
-----------------

Traditionally the first program people write in a new language is called
“Hello, World.” because all it does is print the words “Hello, World.”
In C++, this program looks like this:


.. activecode:: first_program_AC
   :language: cpp
   :caption: Hello World
   :nocodelens:

   The "Hello, World!" program is a great place to start learning a new
   language.  Observe the program structure below.
   ~~~~
   #include <iostream>
   // main: generate some simple output
   int main () {
       std::cout << "Hello, World!" << std::endl;
   }


Some people judge the quality of a programming language by the
simplicity of the "Hello, World." program. By this standard, C++ does
reasonably well. 

.. index:: include file

The fist line, which starts with ``#include`` is simply a way to
use features that are not "built in" to the language, but are
available for you to use.
Soon you'll learn how to create your own,
but for now we are using code from the *Standard Library*.
All of the facilities provided by the standard library have the
prefix ``std::``.

.. index::
   single: comment

The second line begins with ``//``, which indicates that it is a **comment**.
A comment is a bit of English text that you can put in the middle of a
program, usually to explain what the program does. When the compiler
sees a ``//``, it ignores everything from there until the end of the line.

In the third line, you can ignore the word ``int`` for now, but notice the
word ``main``.  ``main`` is a special name that indicates the place in the
program where execution begins. When the program runs, it starts by
executing the first statement in ``main`` and it continues, in order, until
it gets to the last statement, and then it quits.

.. index::
   single: output
   single: cout

There is no limit to the number of statements that can be in ``main``, but
the example contains only one. It is a basic **output** statement,
meaning that it outputs or displays a message on the screen.

``cout`` is an object available from the C++ Standard Library
which allows you to send output to the screen.
The ``std::`` prefix means the facility we are using is part of
the standard library.
The symbol ``<<`` is an operator that you apply to
``cout`` and a string, and that causes the string to be displayed.

``endl`` is an object that represents the end of a line. When you
send an ``endl`` to ``cout``, it causes the cursor to move to the next line of
the display. The next time you output something, the new text appears on
the next line.

Like all statements, the output statement ends with a semi-colon (``;``).

.. warning::
   Failure to terminate a statement with a semicolon will result
   in a syntax (compile) error.

There are a few other things you should notice about the syntax of this
program. First, C++ uses curly-braces (``{`` and ``}``) to group things
together. In this case, the output statement is enclosed in
curly-braces, indicating that it is *inside* the definition of ``main``.
Also, notice that the statement is indented, which helps to show
visually which lines are inside the definition.

As I mentioned, the C++ compiler is a real stickler for syntax. If you
make any errors when you type in the program, chances are that it will
not compile successfully. For example, if you misspell ``iostream``, you
might get an error message like the following:

::

    hello.cpp:1: oistream: No such file or directory

There is a lot of information on this line, but it is presented in a
dense format that is not easy to interpret. A more friendly compiler
might say something like:

    "On line 1 of the source code file named ``hello.cpp``, you tried to
    include a header file named ``oistream``. I didn't find anything with
    that name, but I did find something named ``iostream``. Is that what you
    meant, by any chance?"

Unfortunately, few compilers are so accommodating. The compiler is not
actually smart, and in most cases the error message you get will be
only a hint about what is wrong. It will take some time to gain facility
at interpreting compiler messages.

Nevertheless, the compiler can be a useful tool for learning the syntax
rules of a language. 

.. admonition:: Try This!

   Starting with the working 'hello world' program above,
   modify it in various ways and see what happens. If you get an error
   message, try to remember what the message says and what caused it, so if
   you see it again in the future you will know what it means.

.. tabbed:: tab_check

   .. tab:: Q1

      .. fillintheblank:: first_program_1

         How do you indicate a single line comment in C++?
          
         - :[//][//]: Correct!
           :.*: Try again!


   .. tab:: Q2

      .. mchoice:: first_program_2
         :multiple_answers:
         :answer_a: The main marks the spot in the program where execution begins.
         :answer_b: There is a limit the number of statements you can put in the main because they occupy system memory.
         :answer_c: Inside the main, program execution happens in order from top to bottom.
         :answer_d: The main program is enclosed by parentheses.
         :answer_e: The end of each statement is marked with a semicolon ( ; ).
         :correct: a,c,e
         :feedback_a: The main indicates where the program begins executing!
         :feedback_b: There is no limit to the number of statements you can put in the main, but it is good practice to keep it as short as possible.
         :feedback_c: When the program runs, it starts by executing the first statement in main, and it continues until the last.
         :feedback_d: The main program and all functions in C++ are enclosed by curly brackets ( { and } ).
         :feedback_e: Forgetting a semicolon will cause a compile error!

         **Multiple Response** Which is true about writing a program?


   .. tab:: Q3

      .. fillintheblank:: first_program_3

         |blank| is an object that allows you to send output to the terminal.  
         It requires you to use the |blank| operator.
          
         - :(cout): Correct!
           :.*: Try again!
         - :(\<\<): Correct!
           :.*: Try again!

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :io:`cout` and :io:`endl`
     - :cpp:`Comments <comment>`
     - :lang:`Main function <main_function>`
     - :cpp:`Include files <preprocessor/include>`


