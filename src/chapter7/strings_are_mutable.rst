.. _strings-things-string-s-are-mutable:

``string``\ s are mutable
-------------------------

You can change the letters in an ``string`` one at a time using the
``[]`` operator on the left side of an assignment.

The active code below changes the first letter in ``greeting`` to be
``'J'``.

.. tb-code:: cpp
   :name: strings_are_mutable_AC_1
   :caption: String are mutable

   #include <cstddef>
   #include <iostream>
   #include <string>

   using std::size_t;

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

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: string_mutable_1

         What is printed by the following statements?

         .. code-block:: cpp

            string fav_food = "ice cream";
            fav_food[3] = 'd';
            cout << fav_food << '\n';

         - [ ] icd cream

           Remember that indexing begins at 0, not 1.
         - [x] icedcream

           Index 3 was a space and now it is "d".
         - [ ] ice cream

           The character at index 3 should be changed to "d".
         - [ ] iced

           The character at index 3 should be changed to "d", and the rest stays the same.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: string_mutable_2

         How can we fix the message to be "You're a wizard Harry"?

         .. code-block:: cpp

            string message = "You're a lizard Harry";

         - [x] message[9] = 'w';

           Since "l" is at index 9, replacing it with "w" fixes the message.
         - [ ] message[10] = 'w';

           Remember indexing starts at 0.
         - [ ] 'w' = message[9];

           In order to change a letter in a string, the ``[]`` operator must be on the left of the assignment.
         - [ ] message[8] = 'w';

           Remember indexing starts at 0.

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: string_mutable_3
         :no-indent:

         Construct ``mixer``, which returns a copy of ``s1`` with each even-indexed
         character replaced by the corresponding character from ``s2``.
         For example, ``mixer("food", "summer")`` returns ``"somd"``.
         Assume ``s2`` has at least as many characters as ``s1``.

         .. code-block:: cpp

            {{group}}
            string mixer(string s1, string s2) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void mixer(string s1, string s2) { #distractor
            {{endgroup}}
            {{group}}
               std::size_t i = 0;
            {{endgroup}}
            {{group}}
               while (i < s1.size()) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (i < s2.size()) {
            {{endgroup}}
            {{group}}
                  if (i % 2 == 0) {
                     s1[i] = s2[i];
                  }
            {{endgroup}}
            {{distractor}}
            {{group}}
                  if (i % 2 != 0) {
                     s1[i] = s2[i];
                  }
            {{endgroup}}
            {{group}}
                  ++i;
               }
            {{endgroup}}
            {{group}}
               return s1;
            {{endgroup}}
            {{distractor}}
            {{group}}
               return s2;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

