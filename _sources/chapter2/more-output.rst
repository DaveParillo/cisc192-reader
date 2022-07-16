More Output
-----------

As I mentioned in the last chapter, you can put as many statements as
you want in ``main``. For example, to output more than one line:


.. activecode:: more_output_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Two Lines of Output

   This program prints two different statements on two different lines
   using ``endl``.
   ~~~~
   #include <iostream>

   // main: generate some simple output
   int main () {
       std::cout << "Hello, world." << std::endl;     // output one line
       std::cout << "How are you?" << std::endl;      // output another
   }


As you can see, it is legal to put comments at the end of a line, as
well as on a line by themselves.

.. index::
   single: string

The phrases that appear in quotation marks are called **strings**,
because they are made up of a sequence (string) of letters.

.. note::
   In C++, strings are declared as type ``string``.  We'll explain what that
   means in the next few pages.

Actually, strings can contain any combination of letters, numbers,
punctuation marks, and other special characters.

Often it is useful to display the output from multiple output statements
all on one line. You can do this by leaving out the first ``endl``:


.. activecode:: more_output_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Two Statements, One Line of Output

   This program prints two different statements on the same line.
   ~~~~
   #include <iostream>

   int main () {
       std::cout << "Goodbye, ";
       std::cout << "cruel world!" << std::endl;
   }


In this case the output appears on a single line as ``Goodbye, cruel
world!``. Notice in ``main`` that there is a space between “Goodbye,” and the
second quotation mark. This space appears in the output, so it affects
the behavior of the program.

Spaces that appear outside of quotation marks generally do not affect
the behavior of the program. For example, I could have written:


.. activecode:: more_output_AC_3
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Spaces Removed (messy)

   This program accomplishes the same thing as the one above.  The
   difference is that there are no spaces separating the different
   components of each line.  This is a matter of personal preference.
   ~~~~
   #include <iostream>

   int main () {
       std::cout<<"Goodbye, ";
       std::cout<<"cruel world!"<<std::endl;
   }


This program would compile and run just as well as the original. The
breaks at the ends of lines (newlines) do not affect the program’s
behavior either, so I could have written:


.. activecode:: more_output_AC_4
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Spaces removed, One Line (very messy)

   This program accomplishes the same thing as the two above, but
   it only uses one line.  Once again, this is a matter of personal
   preference.  However, this format is pretty messy and relatively 
   hard to follow.
   ~~~~
   #include <iostream>
   int main(){std::cout<<"Goodbye, ";std::cout<<"cruel world!"<<std::endl;}


That would work, too, although you have probably noticed that the
program is getting harder and harder to read. Newlines and spaces are
useful for organizing your program visually, making it easier to read
the program and locate syntax errors.

We can make another minor change to this program that do not
change how the program behaves, but changes the source code.

.. activecode:: more_output_AC_5
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: Replace endl with newline char

   Use ``\n`` instead of ``endl``.

   The ``endl`` object actually performs two tasks:
   - It sends the ``\n`` char (newline) to the output stream
   - It flushes any remaining buffered contents in the stream
   ~~~~
   #include <iostream>

   int main () {
       std::cout << "Goodbye, ";
       std::cout << "cruel world!" << '\n';
   }

The 'buffer flush' part of ``endl`` is a relatively
expensive operation, so it is often best to avoid it if you don't
need it.

We can use ``'\n'`` more compactly, by embedding the ``\n`` character
as part of a string:

::

   int main () {
       std::cout << "Goodbye, ";
       std::cout << "cruel world!\n";
   }



.. tabbed:: tab_check

   .. tab:: Q1

      .. fillintheblank:: more_output_2

         The phrases that appear in quotation marks are called |blank|.

         - :[Ss][Tt][Rr][Ii][Nn][Gg][Ss]?: Correct!
           :.*: Try again!


   .. tab:: Q2

      .. mchoice:: more_output_3_0
         :practice: T
         :answer_a: 1
         :answer_b: 2
         :answer_c: 3
         :answer_d: 4
         :correct: b
         :feedback_a: There is an "endl" statement, implying that a new line is created.
         :feedback_b: "endl" creates one new line. The first line will say 7, while the second will print 777.
         :feedback_c: In C++, you must make sure to say "endl" every time you'd like to create a new line.
         :feedback_d: In C++, you must make sure to say "endl" every time you'd like to create a new line.

         On how many separate lines will the 7's be printed?

         ::

             #include <iostream>
             using namespace std;

             int main () {
               cout << 7 << endl;
               cout << 7;
               cout << 7;
               cout << 7;
             }


   .. tab:: Q3

      .. parsonsprob:: more_output_3
         :numbered: left
         :adaptive:
         :noindent:

         Construct a main function that prints "Snap!" on the first line, "Crackle!" on the third line, and "Pop!" on the sixth line.  You might not use all of endl blocks provided.

         -----
         int main () {
         =====
          cout << "Snap!";
         =====
          cout << endl; // first endl
         =====
          cout << endl; // second endl
         =====
          cout << "Crakcle!" << endl;
         =====
          cout << endl; // third endl
         =====
          cout << endl; // fourth endl
         =====
          cout << "Pop!";
         =====
          cout << endl; // fifth endl #distractor
         =====
          cout << endl; // sixth endl #distractor
         =====
         }


   .. tab:: Q4

      .. parsonsprob:: more_output_3_1
         :numbered: left
         :adaptive:
         :noindent:

         Construct a main function that prints "Hello, world!" so that "Hello," and "world!" are printed on two separate lines.

         -----
         int main () {
         =====
          cout << "Hello," << endl; cout << "world!";
         =====
          cout << "Hello," << "world!" << endl; #distractor
         =====
          cout >> "Hello," >> endl; cout >> "world!"; #distractor
         =====
          cout >> "Hello," >> "world!" >> endl; #distractor
         =====
         }

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :io:`cout` and :io:`endl`
     - :lang:`Main function <main_function>`

   - :wiki:`The whitespace character <Whitespace_character>` from Wikipedia
   - :core:`Guideline SL.io.50: Avoid endl <#Rio-endl>`

