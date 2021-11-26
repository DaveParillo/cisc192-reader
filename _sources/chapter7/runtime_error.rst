A run-time error
----------------

Way back in Section `[run-time] <#run-time>`__ I talked about run-time
errors, which are errors that don't appear until a program has started
running.

So far, you probably haven't seen many run-time errors, because we
haven’t been doing many things that can cause one. Well, now we are. If
you use the ``at()`` function and you provide an index that is negative or
greater than ``length-1``, you will get a run-time error and a message
something like this:

::

   index out of range: 6, string: banana

Try it in your development environment and see how it looks.

.. activecode:: runtime_error_AC_1 
   :language: cpp

   Running the active code below will result in a runtime error. Can you fix 
   it so that we print out the first letter and last letter of string ``greeting`` instead
   of indexing out of range?
   ~~~~
   #include <iostream>
   #include <string>

   int main() {
       std::string greeting = "Hello world";
       std::cout << "The first letter is " << greeting.at(-1) << '\n';
       std::cout << "The last letter is " << greeting.at(greeting.length()) << '\n';
   }

.. note:: Range-checked access vs. Unchecked access

   In the C++ Standard Library, the ``[]`` operator does **not**
   check the index value provided.
   The ``[]`` operator will *never* generate a runtime error,
   even if the value is clearly impossible:

   ::

      int mydata[3] = {1,2,3};
      cout << mydata[-99];

   Containers that provide an ``at()`` function provide a range-checked
   alternative to the ``[]`` operator.
   the ``[]`` operator and you provide an index that is negative or
   greater than ``length-1``, you will get a run-time error and a message
   something like this:

.. tabbed:: self_check

   .. tab:: Q1

      .. clickablearea:: runtime_error_1
          :question: Click on each spot that would cause a runtime error.
          :iscode:
          :feedback: Remember, an index that is negative or greater than the length of the string - 1 will give a run-time error.

          :click-incorrect:def main() {:endclick:
              :click-incorrect:string fruit = "apple";:endclick:
              char a = :click-incorrect:fruit[0];:endclick:
              char b = :click-incorrect:fruit[9];:endclick:
              char c = :click-incorrect:fruit.at(0);:endclick:
              char d = :click-correct:fruit.at(9);:endclick:
              :click-incorrect:cout << fruit << endl;:endclick:
              cout <<  :click-incorrect:fruit[-4]:endclick:  << endl;
              char d = :click-correct:fruit.at(-4);:endclick:
              cout <<  :click-incorrect:fruit[4]:endclick:  << endl;
          }

   .. tab:: Q2

      .. parsonsprob:: runtime_error_2
         :numbered: left
         :adaptive:

         Construct a block of code that correctly changes the string to say "cat in the hat" instead of "cat on the mat", then print it.
         -----
         int main() {

            string sentence = "cat on the mat";

            sentence[4] = "i";

            sentence[5] = "i"; #distractor

            sentence[3] = "i"; #distractor

            sentence[11] = "h";

            sentence [12] = "h"; #distractor

            sentence[11] = "h" #distractor

            cout << sentence << endl;

         }
