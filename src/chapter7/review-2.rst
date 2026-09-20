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
               cout << word[3] << endl;
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << irritating[3] << endl;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << word.at(4) << endl;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << word[4] << endl;  #distractor
            {{endgroup}}
            {{group}}
               while (word.find('i') != string::npos) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (word.find('e') != string::npos) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (word.find('i')) {  #distractor
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
               cout << word << endl;
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

         Let's write the function longerString, which takes two parameters, 
         first and second. If first has more letters
         than second, longerString prints "first is longer than second",
         and vice versa. If they have the same number of letters, longerString 
         prints "first and second are the same length".
         Put the necessary blocks in the correct order.

         .. code-block:: cpp

            {{group}}
            void longerString (string first, string second) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            string longerString (string first, string second) {
            {{endgroup}}
            {{group}}
               if (first.length() > second.length()) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (first.length() >= second.length()) {
            {{endgroup}}
            {{group}}
                  cout << first << " is longer than " << second << endl;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else if (first.length() < second.length()) {
            {{endgroup}}
            {{group}}
                  cout << second << " is longer than " << first << endl;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  cout << second << " is longer than " << second << endl;
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
                  cout << first << " and " << second << " are the same length" << endl;
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

         Let's write the code for the cipherText function. cipherText 
         should be a void function that takes input as a parameter,
         increases the value of each character by 1 (i.e. "bad" turns into "cbe"),
         and prints the encrypted string.

         .. code-block:: cpp

            {{group}}
            void cipherText (string input) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            string cipherText (string input) {
            {{endgroup}}
            {{group}}
               std::size_t i = 0;
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
               std::size_t count = 0;
            {{endgroup}}
            {{distractor}}
            {{group}}
               std::size_t count = 1;
            {{endgroup}}
            {{group}}
               std::size_t i = 0;
            {{endgroup}}
            {{group}}
               while (i < tongue_twister.size()) {
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
               std::size_t i = 0;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (i < quote.length()) {  #distractor
            {{endgroup}}
            {{group}}
               std::size_t first = quote.find("i");
            {{endgroup}}
            {{group}}
               std::size_t index = find (quote, 'i', first + 1);
            {{endgroup}}
            {{distractor}}
            {{group}}
               std::size_t index = find (quote, 'i', first);
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
                     cout << letter + suffix << endl;
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
         As a result, they hired you to write a function called censorE that replaces all occurences
         of the letter "e" in a string with an asterisk and returns the censored string. For example, 
         if the input is "hello world", the function returns "h*llo world".

         .. code-block:: cpp

            {{group}}
            string censorE (string input) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void censorE (string input) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               string copy = input;  #distractor
            {{endgroup}}
            {{group}}
               std::size_t i = 0;
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
         Using generalization, write the function censorLetter which takes input and a char to censor 
         as parameters and returns a censored string. For example, censorLetter("Bye world", 'o') returns the
         string "Bye w*rld".

         .. code-block:: cpp

            {{group}}
            string censorLetter (string input, char letter) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            string censorLetter (string input) {
            {{endgroup}}
            {{group}}
               std::size_t i = 0;
            {{endgroup}}
            {{distractor}}
            {{group}}
               std::size_t i = 1;
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

         Let's write a function called alphaCombine which takes
         two strings, first and second,
         and returns a string which concatenates first and second in
         alphabetical order. For example,
         alphabetizer ("zebra, mega") returns the string
         "megazebra" since "mega" comes before "zebra" in the alphabet. 
         Put the necessary blocks in the correct order.

         .. code-block:: cpp

            {{group}}
            string alphaCombine (string first, string second) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void alphaCombine (string first, string second) {
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
               std::size_t front = 0, back = input.size();
            {{endgroup}}
            {{distractor}}
            {{group}}
               std::size_t front = 0, back = input.size() - 1;
            {{endgroup}}
            {{group}}
               while (front < back) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               while (front > back) {
            {{endgroup}}
            {{group}}
                  if (input[front] != input[back - 1]) {
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

