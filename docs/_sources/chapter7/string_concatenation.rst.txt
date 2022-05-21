String concatenation
--------------------
.. index::
   pair: string; string concatenation

Interestingly, the ``+`` operator can be used on strings; it performs
string **concatenation**. To concatenate means to join the two operands
end to end. 

.. activecode:: string_concatenation_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: String concatenation

   In the active code below, we use the ``+`` operator to concatenate ``fruit`` with
   ``bakedGood`` to create ``dessert``.
   ~~~~
   #include <iostream>
   using namespace std;

   int main() {
       string fruit = "banana";
       string bakedGood = " nut bread";
       string dessert = fruit + bakedGood;
       cout << dessert << endl;
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

.. activecode:: string_concatenation_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:
   :caption: String concatenation

   The active code below outputs the ducklings names in alphabetical order.
   ~~~~
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

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: string_concatenation_1
         :practice: T
         :answer_a: C++ rocks
         :answer_b: C++
         :answer_c: C++rocks
         :answer_d: Error, you cannot add two strings together.
         :correct: c
         :feedback_a: Concatenation does not automatically add a space.
         :feedback_b: The expression s+t is evaluated first, then the resulting string is printed.
         :feedback_c: Yes, the two strings are glued end to end.
         :feedback_d: The + operator has different meanings depending on the operands, in this case, two strings.


         What is printed by the following statements?

         .. code-block:: cpp

            string s = "C++";
            string t = "rocks";
            cout << s + t << endl;

   .. tab:: Q2

      .. parsonsprob:: string_concatenation_2
         :numbered: left
         :adaptive:

         As an exercise, put together the code below so that it prints ``C++ is so fun!""
         -----
         int main() {
         =====
            string language = "C++";
            string action = " is so ";
            string adjective = "fun!";
         =====
            string language = "C++"; #distractor
            string action = "is so";
            string adjective = "fun!";
         =====
            cout << language + action + adjective << endl;
         =====
            cout << "language" + "action" + "adjective" << endl; #distractor
         =====
         }

   .. tab:: Q3

      .. parsonsprob:: string_concatenation_3
         :numbered: left
         :adaptive:

         Put together the code below to creater a function <code>greeter</code> that adds "hello" and "goodbye" behind and ahead of a message
         respectively and then prints the new message.
         Example: <code>greeter("ssup")</code> will print "hello ssup goodbye";

         -----
         void greeter(string message) {
         =====
         string greeter (string message) { #distractor
         =====
            string beginning = "hello "; 
            string end = " goodbye";
         =====
            string beginning = "hello"; #paired
            string end = "goodbye";
         =====
            string new_Word = beginning + message;
            new_Word = new_Word + end; 
         =====
            string new_Word = message + beginning; #paired
            new_Word = message + end;
         =====
            cout << "new_Word"; #distractor
         =====
            cout &lt&lt new_Word; 
         =====
         }

