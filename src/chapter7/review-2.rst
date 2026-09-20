.. _strings-things-mixed-up-code-practice:

Mixed Up Code Practice
----------------------

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: mucp_7_1
         :no-indent:

         Write a program that prints the 4th character of word, 
         and finds and replaces all instances of 'i' with 'e'.
         Finally, print out the string. Put the necessary blocks in the correct order.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               string word = "irritating";
            {{endgroup}}
            {{group}}
               cout << word[3] << '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << irritating[3] << '\n';  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << word.at(4) << '\n';  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << word[4] << '\n';  #distractor
            {{endgroup}}
            {{group}}
               while ((int)word.find('i') != -1) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while ((int)word.find('e') != -1) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               while ((int)word.find('i')) {  #distractor
            {{endgroup}}
            {{group}}
                  word[word.find('i')] = 'e';
            {{endgroup}}
            {{distractor}}
            {{group}}
                  word[word.find('e')] = 'i';  #distractor
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               cout << word << '\n';
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: mucp_7_2
         :no-indent:

         An anagram is a play on words by rearranging the letters of the original words
         to form new words. For example, the letters in "listen" can be rearranged to
         make "silent". Write a program that rearranges "night" into "thing" and prints the anagram.
         Put the necessary blocks in the correct order.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               string original = "night";
            {{endgroup}}
            {{distractor}}
            {{group}}
               string original = "thing";
            {{endgroup}}
            {{group}}
               string anagram = original;
            {{endgroup}}
            {{group}}
               anagram[0] = original[original.find('t')];
            {{endgroup}}
            {{group}}
               anagram[1] = original[original.find('h')];
            {{endgroup}}
            {{group}}
               anagram[2] = original[original.find('i')];
            {{endgroup}}
            {{group}}
               anagram[3] = original[original.find('n')];
            {{endgroup}}
            {{group}}
               anagram[4] = original[original.find('g')];
            {{endgroup}}
            {{group}}
               cout << anagram;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: mucp_7_3
         :no-indent:

         Let's write the function longer_string, which takes two parameters, 
         first and second. If first has more letters
         than second, longer_string prints "first is longer than second",
         and vice versa. If they have the same number of letters, longer_string 
         prints "first and second are the same length".
         Put the necessary blocks in the correct order.

         .. code-block:: cpp

            {{group}}
            void longer_string (string first, string second) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            string longer_string (string first, string second) {
            {{endgroup}}
            {{group}}
               if (first.length() > second.length()) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (first.length() >= second.length()) {
            {{endgroup}}
            {{group}}
                  cout << first << " is longer than " << second << '\n';
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else if (first.length() < second.length()) {
            {{endgroup}}
            {{group}}
                  cout << second << " is longer than " << first << '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
                  cout << second << " is longer than " << second << '\n';
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else {
            {{endgroup}}
            {{distractor}}
            {{group}}
               else (first.length() == second.length()) {  #distractor
            {{endgroup}}
            {{group}}
                  cout << first << " and " << second << " are the same length" << '\n';
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q4

      .. tb-parsons::
         :name: mucp_7_4

         Let's write the code for the cipher_text function. cipher_text 
         should be a void function that takes input as a parameter,
         increases the value of each character by 1 (i.e. "bad" turns into "cbe"),
         and prints the encrypted string.

         .. code-block:: cpp

            {{group}}
            void cipher_text (string input) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            string cipher_text (string input) {
            {{endgroup}}
            {{group}}
               int i = 0;
            {{endgroup}}
            {{group}}
               while (i < input.length()) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (i < input.length() - 1) {
            {{endgroup}}
            {{group}}
                  input[i] = input[i] + 1;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  input[i] = input[i] - 1;
            {{endgroup}}
            {{group}}
                  i++;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               cout << input;
            {{endgroup}}
            {{distractor}}
            {{group}}
               return input;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q5

      .. tb-parsons::
         :name: mucp_7_5

         The program below should print out the number of occurences of the character 't'
         in the string tongue_twister but the code is mixed up. Put the necessary blocks 
         in the correct order, with declaration in the order of tongue_twister, count, and i.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               string tongue_twister = "twelve twins twirled twelve twigs";
            {{endgroup}}
            {{group}}
               int count = 0;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int count = 1;
            {{endgroup}}
            {{group}}
               int i = 0;
            {{endgroup}}
            {{group}}
               while (i < (int)tongue_twister.length()) {
            {{endgroup}}
            {{group}}
                  if (tongue_twister[i] == 't') {
            {{endgroup}}
            {{distractor}}
            {{group}}
                  if (tongue_twister[i] = 't') {
            {{endgroup}}
            {{group}}
                     count++;
            {{endgroup}}
            {{group}}
                  }
            {{endgroup}}
            {{group}}
                  i++;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               cout << count;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q6

      .. tb-parsons::
         :name: mucp_7_6

         The program below should print out the index of the second instance of the 
         character 'i' but the code is mixed up and contains extra blocks. 
         Put the necessary blocks in the correct order.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               string quote = "Your time is limited, so don't waste it living someone else's life.";
            {{endgroup}}
            {{distractor}}
            {{group}}
               int i = 0;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (i < quote.length()) {  #distractor
            {{endgroup}}
            {{group}}
               int first = quote.find('i');
            {{endgroup}}
            {{group}}
               int index = find (quote, 'i', first + 1);
            {{endgroup}}
            {{distractor}}
            {{group}}
               int index = find (quote, 'i', first);
            {{endgroup}}
            {{group}}
               cout << index;
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << first;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q7

      .. tb-parsons::
         :name: mucp_7_7

         Deep in the forest live the 7 dwarves named Sorty, Torty, Vorty,
         Worty, Xorty, Yorty, and Zorty. The program below should print 
         out each of their names but the code is mixed up and contains extra blocks. 
         Put the necessary blocks in the correct order.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{distractor}}
            {{group}}
               string name = “Sorty”; #distractor
            {{endgroup}}
            {{group}}
               string suffix = "orty";
            {{endgroup}}
            {{group}}
               char letter = 'S';
            {{endgroup}}
            {{group}}
               while (letter <= 'Z') {
            {{endgroup}}
            {{group}}
                  if (letter != 'U') {
            {{endgroup}}
            {{distractor}}
            {{group}}
                  if (letter == 'U') {
            {{endgroup}}
            {{group}}
                     cout << letter + suffix << '\n';
            {{endgroup}}
            {{group}}
                  }
            {{endgroup}}
            {{group}}
                  letter++;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  suffix++;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q8

      .. tb-parsons::
         :name: mucp_7_8

         On the strange planet of Noes, there's a law that prohibits the usage of the letter "e". 
         As a result, they hired you to write a function called censor_e that replaces all occurences
         of the letter "e" in a string with an asterisk and returns the censored string. For example, 
         if the input is "hello world", the function returns "h*llo world".

         .. code-block:: cpp

            {{group}}
            string censor_e (string input) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void censor_e (string input) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               string copy = input;  #distractor
            {{endgroup}}
            {{group}}
               int i = 0;
            {{endgroup}}
            {{group}}
               while (i < input.length()) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (i < input.length() - 1) {
            {{endgroup}}
            {{group}}
                  if (input[i] == 'e') {
            {{endgroup}}
            {{distractor}}
            {{group}}
                  if (input[i] = 'e') {
            {{endgroup}}
            {{group}}
                     input[i] = '*';
            {{endgroup}}
            {{distractor}}
            {{group}}
                     '*' = input[i];
            {{endgroup}}
            {{group}}
                  }
            {{endgroup}}
            {{group}}
                  i++;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               return input;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q9

      .. tb-parsons::
         :name: mucp_7_9

         Your work for the planet of Noes impressed the nearby planets of Noas, Nois, Noos, and Nous.
         They want you to write different functions that censor out each planet's corresponding forbidden letter.
         However, your galaxy brain knows better than to write a different function for each planet.
         Using generalization, write the function censor_letter which takes input and a char to censor 
         as parameters and returns a censored string. For example, censor_letter("Bye world", 'o') returns the
         string "Bye w*rld".

         .. code-block:: cpp

            {{group}}
            string censor_letter (string input, char letter) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            string censor_letter (string input) {
            {{endgroup}}
            {{group}}
               int i = 0;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int i = 1;
            {{endgroup}}
            {{group}}
               while (i < input.length()) {
            {{endgroup}}
            {{group}}
                  if (input[i] == letter) {
            {{endgroup}}
            {{distractor}}
            {{group}}
                  if (input[i] == "letter") {
            {{endgroup}}
            {{group}}
                     input[i] = '*';
            {{endgroup}}
            {{distractor}}
            {{group}}
                     '*' = input[i];
            {{endgroup}}
            {{group}}
                  }
            {{endgroup}}
            {{group}}
                  i++;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               return input;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q10

      .. tb-parsons::
         :name: mucp_7_10

         Let's write a function called alpha_combine which takes
         two strings, first and second,
         and returns a string which concatenates first and second in
         alphabetical order. For example,
         alphabetizer ("zebra, mega") returns the string
         "megazebra" since "mega" comes before "zebra" in the alphabet. 
         Put the necessary blocks in the correct order.

         .. code-block:: cpp

            {{group}}
            string alpha_combine (string first, string second) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void alpha_combine (string first, string second) {
            {{endgroup}}
            {{group}}
               if (first > second) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if ("first" > "second") {
            {{endgroup}}
            {{group}}
                  return second + first;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  cout << second << first;  #distractor
               }
            {{endgroup}}
            {{group}}
               else {
            {{endgroup}}
            {{group}}
                  return first + second;
            {{endgroup}}
            {{group}}
                  cout << first << second;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q11

      .. tb-parsons::
         :name: mucp_7_11
         :no-indent:

         Let's write a function called <code>ispalindrome</code> which takes
         a <code>string</code> named input
         and returns a <code>bool</code>
         The function returns true if the <code>string</code> is a palindrome and false if not.
         palindromes are symmetrical strings.
         That is a string that reads the same backwards is palindrome.
         palindromes:  "hih", "i", "bob", "tenet", "soos", "madam" .
         not palindromes: "join", "hat", "frat", "supper", "rhythm".
         The code is mixed up and contains extra blocks.
         Put the necessary blocks in the correct order.

         .. code-block:: cpp

            {{group}}
            bool ispalindrome(string input) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            string ispalindrome(bool input) {
            {{endgroup}}
            {{group}}
               int front = 0 , back = input.length() - 1;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int front = 0 , back = input.length();
            {{endgroup}}
            {{group}}
               while ( front &lt back) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while ( front &gt back) {
            {{endgroup}}
            {{group}}
                  if( input[b] != input[e] ) {
            {{endgroup}}
            {{distractor}}
            {{group}}
                  else { #distractor
            {{endgroup}}
            {{group}}
                     return false;
            {{endgroup}}
            {{group}}
                  }
            {{endgroup}}
            {{group}}
                  front = front + 1;
            {{endgroup}}
            {{group}}
                  back = back - 1;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               return true;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

