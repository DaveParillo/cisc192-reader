More Output
-----------

As I mentioned in the last chapter, you can put as many statements as
you want in ``main``. For example, to output more than one line:


This program prints two different statements on two different lines
using ``endl``.

.. tb-code:: cpp
   :name: more_output_AC_1
   :caption: Two Lines of Output
   :compileargs: ['-Wall', '-std=c++11']

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


This program prints two different statements on the same line.

.. tb-code:: cpp
   :name: more_output_AC_2
   :caption: Two Statements, One Line of Output
   :compileargs: ['-Wall', '-std=c++11']

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


This program accomplishes the same thing as the one above.  The
difference is that there are no spaces separating the different
components of each line.  This is a matter of personal preference.

.. tb-code:: cpp
   :name: more_output_AC_3
   :caption: Spaces Removed (messy)
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>

   int main () {
       std::cout<<"Goodbye, ";
       std::cout<<"cruel world!"<<std::endl;
   }


This program would compile and run just as well as the original. The
breaks at the ends of lines (newlines) do not affect the program’s
behavior either, so I could have written:


This program accomplishes the same thing as the two above, but
it only uses one line.  Once again, this is a matter of personal
preference.  However, this format is pretty messy and relatively 
hard to follow.

.. tb-code:: cpp
   :name: more_output_AC_4
   :caption: Spaces removed, One Line (very messy)
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>
   int main(){std::cout<<"Goodbye, ";std::cout<<"cruel world!"<<std::endl;}


That would work, too, although you have probably noticed that the
program is getting harder and harder to read. Newlines and spaces are
useful for organizing your program visually, making it easier to read
the program and locate syntax errors.

We can make another minor change to this program that do not
change how the program behaves, but changes the source code.

Use ``\n`` instead of ``endl``.

The ``endl`` object actually performs two tasks:
- It sends the ``\n`` char (newline) to the output stream
- It flushes any remaining buffered contents in the stream

.. tb-code:: cpp
   :name: more_output_AC_5
   :caption: Replace endl with newline char
   :compileargs: ['-Wall', '-std=c++11']

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



.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-blank::
         :name: more_output_2

         The phrases that appear in quotation marks are called {{{{blank}}}}.

         .. tb-answer::
            :match: [Ss][Tt][Rr][Ii][Nn][Gg][Ss]?
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q2

      .. tb-choice::
         :name: assignment_2

         What must be changed in order for this code block to work?

         ::

             #include <iostream>
             using namespace std;
             // main: generate some simple output

             int main () {
               int p;
               int q;
               p = "h";
               q = "9";
             }


         - [ ] Change the type of variable q from int to string.

           Yes, but take a look at variable p.
         - [x] Change the type of both variables (p and q) from int to string.

           Both variables are a character surrounded by double quotes, so they should be type string.
         - [ ] Change the type of variable p from int to char.

           Yes, but take a look at variable q.
         - [ ] Nothing needs to change! The code will work just fine!

           No! There will be a compile error.

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: more_output_3
         :no-indent:

         Construct a main function that prints "Snap!" on the first line, "Crackle!" on the third line, and "Pop!" on the sixth line.  You might not use all of endl blocks provided.

         .. code-block:: cpp

            {{group}}
            int main () {
            {{endgroup}}
            {{group}}
             cout << "Snap!";
            {{endgroup}}
            {{group}}
             cout << endl; // first endl
            {{endgroup}}
            {{group}}
             cout << endl; // second endl
            {{endgroup}}
            {{group}}
             cout << "Crakcle!" << endl;
            {{endgroup}}
            {{group}}
             cout << endl; // third endl
            {{endgroup}}
            {{group}}
             cout << endl; // fourth endl
            {{endgroup}}
            {{group}}
             cout << "Pop!";
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << endl; // fifth endl #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << endl; // sixth endl #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q4

      .. tb-parsons::
         :name: more_output_3_1
         :no-indent:

         Construct a main function that prints "Hello, world!" so that "Hello," and "world!" are printed on two separate lines.

         .. code-block:: cpp

            {{group}}
            int main () {
            {{endgroup}}
            {{group}}
             cout << "Hello," << endl; cout << "world!";
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout << "Hello," << "world!" << endl; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout >> "Hello," >> endl; cout >> "world!"; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             cout >> "Hello," >> "world!" >> endl; #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :io:`cout` and :io:`endl`
     - :lang:`Main function <main_function>`

   - :wiki:`The whitespace character <Whitespace_character>` from Wikipedia
   - :core:`Guideline SL.io.50: Avoid endl <#Rio-endl>`

