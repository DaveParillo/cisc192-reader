Multiple Choice Exercises
-------------------------

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: mce_7_1

         ich variables below is declared as a ``string`` type?

          code-block:: cpp

          int main() {
            int x = 0;
            double y = 4.5;
            string word = "hello";
            string letter = "a";
            char c = 'c';
            bool isPrime = 1;
          }

         ``x``

         - [ ] ``x`` is an ``int``.

         ``y``

         - [x] ``y`` is a ``double``.

         ``word``

         + ``word`` is a ``string``.

         ``"hello"``

         - [x] "hello" is not a variable.

         ``letter``

         + ``letter`` is a ``string``.

         ``c``

         - [ ] ``c`` is a ``char``.

         ``isPrime``

         - [ ] ``isPrime`` is a ``bool``.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: mce_7_2

         at value should replace the question mark to output the character 'p'?

          code-block:: cpp

          int main() {
            string quote = "Not my tempo.";
            cout << quote[?];
          }

         11

         - [x] Remember that indexing begins at 0 in C++.

         10

         + 'p' is located at index 10 in quote.

         4

         - [ ] The character 'm' is located at index 4.

         0

         - [ ] The character "N" is located at index 0.

   .. tb-tab:: Q3

      .. tb-choice::
         :name: mce_7_3

         at is the output of the code below?

          code-block:: cpp

          int main() {
            string quote = "I love you 3000.";
            int x = 3;
            int y = 3 * x;
            int z = 1;
            if (y > 12) {
              z = z + x + y;
            } 
            else {
              z = z + y - x;
            }
            cout << quote[z];
          }

         I

         - [ ] The value of ``z`` is not 0.

         0

         - [ ] The value of ``z`` is not greater than 11.

         o

         - [x] The value of ``z`` is not 3.

         y

         + The final value of ``z`` is 7, and 'y' is at index 7 of ``quote``.

   .. tb-tab:: Q4

      .. tb-choice::
         :name: mce_7_4

         at is the output of the code below?

          code-block:: cpp

          int main() {
            string quote = "Look at me. I'm the captain now.";
            std::size_t x = quote.size();
            cout << quote.at(x);
          }

         -1

         - [ ] -1 is not in ``quote``.

         w

         - [ ] ``x`` is not the index value of the character 'w'.

         .

         - [ ] ``x`` is not the index value of the last period.

         ' '

         - [x] It might be logical to think that an invalid index refers to a space, but ``at()`` checks the index and throws.

         Error, we are indexing out of bounds.

         + ``x`` equals ``quote.size()``. The checked access throws ``std::out_of_range``.

   .. tb-tab:: Q5

      .. tb-choice::
         :name: mce_7_5

         at is the output of the code below?

          code-block:: cpp

          int main() {
            string quote = "With great power comes great responsiblity.";
            std::size_t n = 0;
            while (n < quote.size()) {
              if (n % 5 == 0) {
                cout << quote[n];
              }
              n++;
            }
          }

         teeest

         - [x] Remember that indexing begins at 0 in C++.

         Wg reeest

         + If we print out every fifth character, including the first, this is the answer.

         ith reatpowe coms grat rsponibliy.

         - [ ] This is what we would get if we removed every fifth character.

         With great power comes great responsiblity.

         - [ ] Take a look at the conditional in the while loop.

   .. tb-tab:: Q6

      .. tb-choice::
         :name: mce_7_6

         at is the output of the code below?

          code-block:: cpp

          int main() {
            string quote = "Why so serious?";
            std::size_t index = quote.find("a");
            if (index == string::npos) {
                cout << "not found";
            } else {
                cout << index;
            }
          }

         not found

         + Since 'a' is absent, ``find`` returns ``string::npos`` and the program prints ``not found``.

         0

         - [ ] The character at index 0 is 'W'.

         8

         - [ ] The character at index 8 is 'e'.

         15

         - [ ] There is no index ``15`` in quote.

   .. tb-tab:: Q7

      .. tb-choice::
         :name: mce_7_7

         at is the output of the code below?

          code-block:: cpp

          int main() {
            string tongue_twister = "How much wood could a woodchuck chuck if a woodchuck could chuck wood?";
            std::size_t index = tongue_twister.find("wood");
            cout << index;
          }

         4

         - [x] Although "wood" appears four times in the ``string``, that is not what the ``find`` function returns.

         9

         + The index of 'w' in the first "wood" is at index 9.

         10

         - [ ] Remember indexing begins at 0 in C++.

         12

         - [ ] The ``find`` function returns the index of the first character of the found string.

         22

         - [ ] The ``find`` function returns the index of the first character of the found string.

   .. tb-tab:: Q8

      .. tb-choice::
         :name: mce_7_8

         at is the output of the code below?

          code-block:: cpp

          int main() {
            string tongue_twister = "How much wood could a woodchuck chuck if a woodchuck could chuck wood?";
            std::size_t index = find (tongue_twister, 'w', tongue_twister.find("wood") + 1);
            cout << index;
          }

         9

         - [x] Take a closer look at the starting index for where we should start looking.

         22

         + After the first 'w', the second 'w' appears at index 22.

         43

         - [ ] Take a closer look at the ``find`` function and its arguments.

         65

         - [ ] Take a closer look at the ``find`` function and its arguments.

   .. tb-tab:: Q9

      .. tb-choice::
         :name: mce_7_9

         at is the output of the code below?

          code-block:: cpp

          int main() {
            string quote = "Life is like a box of chocolates. You never know what you're gonna get.";
            std::size_t i = 0;
            std::size_t count = 0;
            while (i < quote.size()) {
              if (quote[i] == 'e') {
                ++count;
              }
              ++i;
            }
            cout << count;
          }

         0

         - [ ] Are there any occurences of the letter 'e' in ``quote``?

         6

         - [x] Count the number of 'e's in ``quote``.

         7

         + There are 7 occurences of the letter 'e' in ``quote``.

         12

         - [ ] Count the number of 'e's in ``quote``.

   .. tb-tab:: Q10

      .. tb-choice::
         :name: mce_7_10

         at is the output of the code below?

          code-block:: cpp

          int main() {
            string call = "Marco!";
            string response = "Polo!";
            string output = "call" + "response";
            cout << output;
          }

         Marco! Polo!

         - [ ] Take a closer look at the initialization of ``output``.

         Marco!Polo!

         - [ ] Take a closer look at the initialization of ``output``.

         call response

         - [ ] Can we concatenate "call" and "response"?

         callresponse

         - [x] Can we concatenate "call" and "response"?

         Error!

         + We cannot concatenate native C strings like "call" and "response", so this code results in an error.

   .. tb-tab:: Q11

      .. tb-choice::
         :name: mce_7_11

          error occured while delivering a message. All instances of the letter 's'
         t replaced by 'X's. Can you complete the code below to fix this error by selecting 
         e correct line of code to replace the question marks?

          code-block:: cpp

          int main() {
            string question = "Honey? Where'X my Xuper Xuit?";
            std::size_t i = 0;
            while (i < question.size()) {
              if (question[i] == 'X') {
                ?????
              }
              i++;
            }
            cout << question;
          }

         ``question['X'] = 's';``

         - [ ] The argument in the ``[]`` operator should be a position in the string.

         ``'s' = question[i];``

         - [ ] Check the order of your assignment.

         ``'X' = 's';``

         - [x] We cannot assign the value of 's' to 'X'.

         ``question[i] = 's';``

         + This will successfully replace all instances of 'X' with 's'.

   .. tb-tab:: Q12

      .. tb-choice::
         :name: mce_7_12

         at is the output of the code below?

          code-block:: cpp

          cout << ("butter" < "butterfly");

         butterbutterfly

         - [ ] The operator between "butter" and "butterfly" is the ``<`` operator, not ``<<``.

         0

         - [x] Does "butter" come before or after "butterfly"?

         1

         + "butter" comes before "butterfly" in the dictionary.

         false

         - [ ] In C++, boolean values are printed as either a 0 or 1 unless ``boolalpha`` is used.

         true

         - [ ] In C++, boolean values are printed as either a 0 or 1 unless ``boolalpha`` is used.

   .. tb-tab:: Q13

      .. tb-choice::
         :name: mce_7_13

         at is the output of the code below?

          code-block:: cpp

          int main() {
             string quote = "Suffering builds character";
             std::size_t count = 0;
             std::size_t index = 17;
             while ( index != quote.size() ){
               if ( quote[index] == 'a' || quote[index] == 'e' ){
                 count = count + index;
               }
               index = index + 1;
             }
             cout << count << endl;
          }

         3

         - [ ] The code is not counting the number of a's or e's after position 17. Rather adding up their indices.

         4

         - [x] The code is not counting the number of a's or e's. Rather adding up their indices.

         64

         + Correct! the occurences of 'a' are 19  and 21, while that of 'e' is 24 (after ``index`` 17). The total is 64.

         68

         - [ ] The first occurence of 'e' is at index 4 so it is not counted.

   .. tb-tab:: Q14

      .. tb-choice::
         :name: mce_7_14

         at is the output of the code below?

          code-block:: cpp

          int main() {
             string quote = "Its Bond, James Bond";
             std::size_t index = 1;
             while( index < quote.size() ){
               quote[index] = 'M';
               index = index * 2;
             }
             cout << quote << endl;
          }

         "IMM MondM James Mond"

         + Correct! We change indices 1,2,4,8,16 to M before ``index`` becomes ``>`` ``quote.size()``.

         "IMMMMMMMMMMMMMMMMMMM"

         - [ ] We are not increasing ``index`` by 1, instead we are doubling it.

         "MMM MondM James Mond"

         - [ ] We don't start at position 0 this time.

         "IMsMBMnM,MJMmMsMBMnM"

         - [ ] we are not increasing ``index`` by 2, instead we are doubling it.

