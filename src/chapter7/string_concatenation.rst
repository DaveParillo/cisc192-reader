.. _strings-things-string-concatenation:

String concatenation
--------------------
.. index::
   pair: string; string concatenation

Interestingly, the ``+`` operator can be used on strings; it performs
string **concatenation**. To concatenate means to join the two operands
end to end. 

In the active code below, we use the ``+`` operator to concatenate ``fruit`` with
``baked_good`` to create ``dessert``.

.. tb-code:: cpp
   :name: string_concatenation_AC_1
   :caption: String concatenation

   #include <iostream>
   using namespace std;

   int main() {
       string fruit = "banana";
       string baked_good = " nut bread";
       string dessert = fruit + baked_good;
       cout << dessert << '\n';
   }

The output of this program is ``banana nut bread``.

.. warning::
   Unfortunately, the ``+`` operator does not work on native C strings.

Thus, you cannot write something like

::

     string dessert = "banana" + " nut bread";

because both operands are C strings. As long as one of the operands is
a ``string``, though, C++ will automatically convert the other.

It is also possible to concatenate a character onto the beginning or end
of an ``string``. In the following example, we will use concatenation
and character arithmetic to output an abecedarian series.

“Abecedarian” refers to a series or list in which the elements appear in
alphabetical order. For example, in Robert McCloskey’s book *Make Way
for Ducklings*, the names of the ducklings are Jack, Kack, Lack, Mack,
Nack, Ouack, Pack and Quack. Here is a loop that outputs these names in
order:

The active code below outputs the ducklings names in alphabetical order.

.. tb-code:: cpp
   :name: string_concatenation_AC_2
   :caption: String concatenation

   #include <iostream>
   #include <string>

   int main() {
       std::string suffix = "ack";
       char letter = 'J';
       while (letter <= 'Q') {
           std::cout << letter + suffix << '\n';
           ++letter;
       }
   }

Again, be careful to use string concatenation only with ``string``\ s
and not with native C strings. Unfortunately, an expression like
``letter + "ack"`` is syntactically legal in C++, although it produces
essentially garbage output.
Try it for yourself and see what happens.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: string_concatenation_1

         What is printed by the following statements?

         .. code-block:: cpp

            string s = "C++";
            string t = "rocks";
            cout << s + t << '\n';

         - [ ] C++ rocks

           Concatenation does not automatically add a space.
         - [ ] C++

           The expression s+t is evaluated first, then the resulting string is printed.
         - [x] C++rocks

           Yes, the two strings are glued end to end.
         - [ ] Error, you cannot add two strings together.

           The + operator has different meanings depending on the operands, in this case, two strings.

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: string_concatenation_2

         As an exercise, put together the code below so that it prints "C++ is so fun!"

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               string language = "C++";
               string action = " is so ";
               string adjective = "fun!";
            {{endgroup}}
            {{distractor}}
            {{group}}
               string language = "C++"; #distractor
               string action = "is so";
               string adjective = "fun!";
            {{endgroup}}
            {{group}}
               cout << language + action + adjective << '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << "language" + "action" + "adjective" << '\n'; #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: string_concatenation_3

         Put together the code below to creater a function <code>greeter</code> that adds "hello" and "goodbye" behind and ahead of a message
         respectively and then prints the new message.
         Example: <code>greeter("ssup")</code> will print "hello ssup goodbye";

         .. code-block:: cpp

            {{group}}
            void greeter(string message) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            string greeter (string message) { #distractor
            {{endgroup}}
            {{group}}
               string beginning = "hello ";
               string end = " goodbye";
            {{endgroup}}
            {{distractor}}
            {{group}}
               string beginning = "hello";
               string end = "goodbye";
            {{endgroup}}
            {{group}}
               string new_Word = beginning + message;
               new_Word = new_Word + end;
            {{endgroup}}
            {{distractor}}
            {{group}}
               string new_Word = message + beginning;
               new_Word = message + end;
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << "new_Word"; #distractor
            {{endgroup}}
            {{group}}
               cout &lt&lt new_Word;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

