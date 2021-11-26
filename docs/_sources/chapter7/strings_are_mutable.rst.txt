``string``\ s are mutable
-------------------------

You can change the letters in an ``string`` one at a time using the
``[]`` operator on the left side of an assignment.

.. activecode:: strings_are_mutable_AC_1
  :language: cpp
  :caption: String are mutable

  The active code below changes the first letter in ``greeting`` to be
  ``'J'``.
  ~~~~
  #include <iostream>
  #include <string>

  int main() {
      std::string greeting = "Hello, world!";
      std::cout << greeting << '\n';
      std::cout << "First letter: " << greeting[0] << '\n';
      greeting[0] = 'J';
      std::cout << greeting << '\n';
  }


Notice we are using the same operator (``[]``) to either
get a single character from a string or to modify a
single character in the string.

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: string_mutable_1
         :practice: T
         :answer_a: icd cream
         :answer_b: icedcream
         :answer_c: ice cream
         :answer_d: iced
         :correct: b
         :feedback_a: Remember that indexing begins at 0, not 1.
         :feedback_b: Index 3 was a space and now it is "d".
         :feedback_c: The character at index 3 should be changed to "d".
         :feedback_d: The character at index 3 should be changed to "d", and the rest stays the same.


         What is printed by the following statements?

         .. code-block:: cpp

            string fav_food = "ice cream";
            fav_food[3] = "d";
            cout << fav_food << '\n';

   .. tab:: Q2

      .. mchoice:: string_mutable_2
         :practice: T
         :answer_a: message[9] = "w";
         :answer_b: message[10] = "w";
         :answer_c: "w" = message[9];
         :answer_d: message[8] = "w";
         :correct: a
         :feedback_a: Since "l" is at index 9, replacing it with "w" fixes the message.
         :feedback_b: Remember indexing starts at 0.
         :feedback_c: In order to change a letter in a string, the ``[]`` operator must be on the left of the assignment.
         :feedback_d: Remember indexing starts at 0.

         How can we fix the message to be "You're a wizard Harry"?

         .. code-block:: cpp

            string message = "You're a lizard Harry";

   .. tab:: Q3

      .. parsonsprob:: string_mutable_3
         :numbered: left
         :adaptive:
         :noindent:

         Put together the code below to creater a function <code>mixer<\code> that takes in two strings and replaces every even index 
         of the first string by the corresponding index of the second. It returns the modified first string.
         Example: 
         <code>string_a = "food"<\code>  and <code>string_b = "summer"<\code> .
         <code> mixer(string_a ,string_b )<\code> makes <code>string_a<\code> become "somd".

         Assume second string is greater than first.

         -----
         string greeter(string s1,string s2) {
         =====
         void mixer(string s1,string s2) { #distractor
         =====
            int size = s1.length(); 
         =====
            int size = s2.length(); #paired
         =====
            index i = 0;
            while (i &lt size) {
         =====
            index i = size - 1; #distractor
            while (i &lt size) {
         =====
              if( (i % 2) == 0){
                s1[i] = s2[i];
              } 
         =====
              if( (i % 2) == 1){ #paired
                s1[i] = s2[i];
              } 
         =====
            }
         =====
            return s1; 
         =====
            return s2; #paired
         =====
         }

