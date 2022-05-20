Keywords
--------

.. index::
   single: keyword

A few sections ago, I said that you can make up any name you want for
your variables, but that’s not quite true. There are certain words that
are reserved in C++ because they are used by the compiler to parse the
structure of your program, and if you use them as variable names, it
will get confused. These words, called **keywords**, include ``int``, ``char``,
``void``, ``endl`` and many more.

A list of C++ keywords is available publicly on ``cppreference``.  You can
take a look for yourself by pasting the following link into your browser.

::

    https://en.cppreference.com/w/cpp/keyword

Rather than memorize the list, I would suggest that you take advantage
of a feature provided in many development environments: code
highlighting. As you type, different parts of your program should appear
in different colors. For example, keywords might be blue, strings red,
and other code black. 

.. caution::
   If you type a variable name and it turns the color of a keyword in your editor, 
   then watch out! You might get 
   some strange behavior from the compiler.

.. note::
   Case matters!  You can name a ``string`` variable ``String`` without an issue
   because C++ does not consider ``String`` to be the same as keyword ``string``.
   Also, a anything written in quotes, for example ``"string"`` is not considered
   a keyword in C++, even if it is spelt the same.

Unlike variables and standard library objects like ``cout``,
you can't put a variable or object in a namespace to avoid a name conflict.
The language keywords are always "in scope".
More on scope and namespaces in the next chapter.

.. tabbed:: tab_check

   .. tab:: Q1

      .. fillintheblank:: keywords_1

         Words that are reserved in C++ because they are used by the compiler to parse the structure of your program are called |blank|.

         - :[Kk][Ee][Yy][Ww][Oo][Rr][Dd][Ss]: Correct!
           :.*: Try again!


   .. tab:: Q2

      .. mchoice:: keywords_2
         :practice: T
         :multiple_answers:
         :answer_a: integer
         :answer_b: cout
         :answer_c: variable
         :answer_d: string
         :answer_e: char
         :correct: b,d,e
         :feedback_a: integer is not a keyword, but int is.
         :feedback_b: cout cannot be used as a variable name!
         :feedback_c: variable is fair game to use to name a variable.
         :feedback_d: string cannot be used as a variable name.
         :feedback_e: char is a keyword and cannot be used as a variable name.

         Multiple Response: Which of the following are keywords or will otherwise generate some error from the compiler if used as a variable name?


   .. tab:: Q3

      .. clickablearea:: keywords_3
          :question: Click on all keywords.
          :iscode:
          :feedback: Try again!

          :click-correct:int:endclick: main() {
              :click-correct:double:endclick: :click-incorrect:x:endclick: = 1.0;
              :click-correct:int:endclick: :click-incorrect:y:endclick: = :click-incorrect:x:endclick: + 5;
              :click-correct:bool:endclick: :click-incorrect:Bool:endclick:;
              :click-correct:string:endclick: :click-incorrect:s:endclick: = :click-incorrect:"void":endclick:;
              :click-correct:if:endclick: (:click-incorrect:y:endclick: > :click-incorrect:x:endclick:) {
                 :click-incorrect:Bool:endclick: = :click-correct:true:endclick:;
              }
              :click-incorrect:cout:endclick: << :click-incorrect:Bool:endclick: << :click-correct:endl:endclick:;
          }


   .. tab:: Q4

      .. activecode:: keywords_4
         :language: cpp
         :autograde: unittest
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:

         Fix the code below so that it runs without errors.  Hint: you might need to change the names of some variables.
         ~~~~
         int main () {
             int friend = 4;
             int enemy = friend * (-1);
             cout << "enemy = " << enemy << endl;

             // Do not modify anything below.
             return 0;
         }

