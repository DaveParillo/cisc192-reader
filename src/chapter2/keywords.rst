Keywords
--------

.. index::
   single: keyword

A few sections ago, I said that you can make up any name you want for
your variables, but that’s not quite true. There are certain words that
are reserved in C++ because they are used by the compiler to parse the
structure of your program, and if you use them as variable names, it
will get confused. These words, called **keywords**, include 
:cpp:`int <keyword/int>`, :cpp:`char <keyword/char>`,
:lang:`return`, :cpp:`using <keyword/using>` and many more.

C++ :cpp:`keywords <keyword>` are available publicly on ``cppreference``.
Many of the C++ language links from this textbook link to this site,
for example:

::

    https://en.cppreference.com/w/cpp/keyword

Rather than memorize the list, I would suggest that you take advantage
of a feature provided in many development environments: source code
highlighting. As you type, different parts of your program should appear
in different colors. For example, keywords might be blue, strings red,
and other code black. 

.. caution::
   If you type a variable name and it turns the color of a keyword in your editor, 
   then watch out! You might get 
   some strange behavior from the compiler.
 
In addition to keywords, the facilities you include in your programs
using ``#include`` add additional names that you want to avoid
conflict with. The include files 
:io:`iostream <basic_iostream>`, :cpp:`string`, and :container:`vector`
are commonly included.

.. note::
   Case matters!  You can name a ``string`` variable ``String`` without an issue
   because C++ does not consider ``String`` to be the same as ``string``.
   Also, a anything written in quotes, for example ``"string"`` is not considered
   a keyword or variable in C++, even if it is spelled the same.

Unlike variables and standard library objects like ``cout``,
you can't put a variable or object in a namespace to avoid a name conflict
with a language keyword.
The language keywords are always "in scope".
More on scope and namespaces in the next chapter.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-blank::
         :name: keywords_1

         Words that are reserved in C++ because they are used by the compiler to parse the structure of your program are called {{{{blank}}}}.

         .. tb-answer::
            :match: [Kk][Ee][Yy][Ww][Oo][Rr][Dd][Ss]
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q2

      .. tb-choice::
         :name: keywords_2






         - [ ] integer

           integer is not a keyword, but int is.
         - [x] cout

           cout should not be used as a variable name.
         - [ ] variable

           variable is fair game to use to name a variable.
         - [x] string

           string should not be used as a variable name.
         - [x] char

           char is a keyword and cannot be used as a variable name.

   .. tb-tab:: Q3

      .. tb-click::
         :name: keywords_3

         Click on all keywords.

         .. code-block:: cpp

            int main() {
                double x = 1.0;
                int y = x + 5;
                bool Bool;
                string s = "void";
                if (y > x) {
                   Bool = true;
                }
                cout << Bool << endl;
            }



         .. tb-hit:: text:int

            Correct.

         .. tb-hit:: text:double

            Correct.

         .. tb-miss:: text:x

            Try again!

         .. tb-hit:: text:int#2

            Correct.

         .. tb-miss:: text:y

            Try again!

         .. tb-miss:: text:x#2

            Try again!

         .. tb-hit:: text:bool

            Correct.

         .. tb-miss:: text:Bool

            Try again!

         .. tb-miss:: text:string

            Try again!

         .. tb-miss:: text:s

            Try again!

         .. tb-miss:: text:"void"

            Try again!

         .. tb-hit:: text:if

            Correct.

         .. tb-miss:: text:y#2

            Try again!

         .. tb-miss:: text:x#3

            Try again!

         .. tb-miss:: text:Bool#2

            Try again!

         .. tb-hit:: text:true

            Correct.

         .. tb-miss:: text:cout

            Try again!

         .. tb-miss:: text:Bool#3

            Try again!

         .. tb-miss:: text:endl

            Try again!

   .. tb-tab:: Q4

      Fix the code below so that it runs without errors.  Hint: you might need to change the names of some variables.

      .. tb-code:: cpp
         :name: keywords_4
         :caption: Example keywords_4
         :compileargs: ['-Wall', '-Werror', '-std=c++11']

         int main () {
             int friend = 4;
             int enemy = friend * (-1);
             cout << "enemy = " << enemy << '\n';

             // Do not modify anything below.
             return 0;
         }

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :cpp:`Keywords <keyword>`
     - :cpp:`Source file inclusion <preprocessor/include>`
     - :cpp:`input/output <io>` library
     - :cpp:`string` library
     - :container:`vector`

