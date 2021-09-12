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

.. index::
   single: function call

You can make up any name you want for your function, except that you
can’t call it ``main`` or any other C++ keyword. The list of parameters
specifies what information -- if any -- you have to provide in order to use, 
or **call**, the new function.

``main`` doesn't take any parameters, as indicated by the empty parentheses
() in it’s definition. The first couple of functions we are going to
write also have no parameters, so the syntax looks like this:

::

    void new_line () {
      cout << endl;
    }

This function is named ``new_line``; it contains only a single statement,
which outputs a new line character, represented by the special value
``endl``.

In ``main`` we can call this new function using syntax that is similar to
the way we call the built-in C++ commands:

::

    int main () {
      cout << "First Line." << endl;
      new_line ();
      cout << "Second Line." << endl;
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
      cout << "First Line." << endl;
      new_line ();
      new_line ();
      new_line ();
      cout << "Second Line." << endl;
      return 0;
    }

Or we could write a new function, named ``three_line``, that prints three new
lines:


.. activecode:: new_functions_AC_1
   :language: cpp
   :caption: The three_line Function

   Here we define the three_line function, which calls the new_line function
   three times.  The result is a function that prints three lines after it
   is called.
   ~~~~
   #include <iostream>
   using std::cout;
   using std::endl;

   void new_line () {
       cout << endl;
   }

   void three_line () {
       new_line ();  new_line ();  new_line ();
   }

   int main () {
       cout << "First Line." << endl;
       three_line ();
       cout << "Second Line." << endl;
       return 0;
   }


You should notice a few things about this program:

-  You can call the same procedure repeatedly. In fact, it is quite
   common and useful to do so.

-  You can have one function call another function. In this case, ``main``
   calls ``three_line`` and three_line calls ``new_line``.
   Again, this is common and useful.

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
   endl``?

#. Creating a new function can make a program smaller by eliminating
   repetitive code. For example, a short way to print nine consecutive
   new lines is to call three_line three times. How would you print 27
   new lines?


.. tabbed:: tab_check

   .. tab:: Q1

      .. mchoice:: new_functions_1

          Which of these statements is false about functions?

          -   You can name a function anything you want.

              +   You can't name a function the same name as a reserved keyword.

          -   You can have a fucntion with several parameters or a function with none.

              -   This is true! However, you must always use parentheses.

          -   You can call a function inside of another function.

              -   This is true! It is common and useful.

          -   You can write multiple statements on one line of a function.

              -   This is true! As long as each statement ends with a semicolon.

   .. tab:: Q2

      .. clickablearea:: new_functions_2
         :question: Click on all function HEADERS.
         :iscode:
         :feedback: Remember, the operator '=' is used for assignment.

         :click-correct:void printX() {:endclick:
             :click-incorrect:cout << "X";:endclick:
         }

         :click-correct:void printVar(int a) {:endclick:
             :click-incorrect:cout << a;:endclick:
         }  

         :click-correct:int main() {:endclick:
             :click-incorrect:int x = 7;:endclick:
             :click-incorrect:printVar(x);:endclick: 
             :click-incorrect:if (x < 10) {:endclick:
                 :click-incorrect:x = x - 1;:endclick:
             }
             :click-incorrect:printX();:endclick:
             :click-incorrect:int y = 3;:endclick:
             :click-incorrect:double result = x / y;:endclick:
             :click-incorrect:printVar(result);:endclick:
             return 0;
         }


   .. tab:: Q3

      .. clickablearea:: new_functions_3
         :question: Click on all function CALLS.
         :iscode:
         :feedback: Remember, the operator '=' is used for assignment.

         :click-incorrect:void printX() {:endclick:
             :click-incorrect:cout << "X";:endclick:
         }

         :click-incorrect:void printVar(int a) {:endclick:
             :click-incorrect:cout << a;:endclick:
         }  

         :click-incorrect:int main() {:endclick:
             :click-incorrect:int x = 7;:endclick:
             :click-correct:printVar(x);:endclick:  
             :click-incorrect:if (x < 10) {:endclick:
                 :click-incorrect:x = x - 1;:endclick:
             }
             :click-correct:printX();:endclick:     
             :click-incorrect:int y = 3;:endclick:
             :click-incorrect:double result = x / y;:endclick:
             :click-correct:printVar(result);:endclick:
             return 0;
         }

   .. tab:: Q4

      .. parsonsprob:: new_functions_4
         :numbered: left
         :adaptive:

         Construct a function that correctly prints the perimeter of a rectangle.
        
         -----
         void perimeter (int length,int width) {
         =====
         int twice_length = 2*length;
         =====
         int twice_width = 2*width; 
         =====
         int perimeter_value = twice_length + twice_width;
         =====
         cout << perimeter_value<<endl;
         =====
         return parameter_value; #distractor
         =====
         }

