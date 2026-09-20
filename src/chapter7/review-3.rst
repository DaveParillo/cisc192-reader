Coding Practice
---------------


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-group::
         :name: cp_7_1

         .. tb-tab:: Question

            A palindrome is a word, phrase, or sentence that reads the same forwards and backwards.
            Write a function ``is_palindrome`` that takes a ``string input`` as a parameter and returns 
            a boolean that is true if the input is a palindrome and false otherwise. 
            The tests skip non-alphanumeric characters (space, puncuation, etc).

            Run and test your code!

            .. tb-code:: cpp
               :name: cp_7_AC_1q-support
               :hidden:
               :compileargs: ['-Wall', '-std=c++11']


               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class T, class Compare = std::equal_to<T>>
               void check (const std::string& name, 
                           const T& actual, 
                           const T& expected,
                           const Compare& op = Compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << std::boolalpha << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                  check("is racecar?", is_palindrome("racecar"), true);
                  check("is kangaroo?", is_palindrome("kangaroo"), false);
                  check("is this phrase?", is_palindrome("able was I ere I saw elba"), true);
                  check("is this phrase?", is_palindrome("no lemon, no melon"), true);
                }


            .. tb-code:: cpp
               :name: cp_7_AC_1q
               :caption: Example cp_7_AC_1q
               :run-after: cp_7_AC_1q-support
               :compileargs: ['-Wall', '-std=c++11']

               #include <cctype>
               #include <iostream>
               #include <string>


               bool is_palindrome (std::string input) {
                   // Write your implementation here.
               }

         .. tb-tab:: Answer

            Below is one way to implement the program. We use the ``isalpha`` function
            to ignore the non alphabetical characters. Then we continuously check to see 
            if the letters in the front are equal to the ones in the back until we reach the 
            middle of the string.

            .. tb-code:: cpp
               :name: cp_7_AC_1a-support
               :hidden:
               :compileargs: ['-Wall', '-std=c++11']

               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class T, class Compare = std::equal_to<T>>
               void check (const std::string& name, 
                           const T& actual, 
                           const T& expected,
                           const Compare& op = Compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << std::boolalpha << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                  check("is racecar?", is_palindrome("racecar"), true);
                  check("is kangaroo?", is_palindrome("kangaroo"), false);
                  check("is this phrase?", is_palindrome("able was I ere I saw elba"), true);
                  check("is this phrase?", is_palindrome("no lemon, no melon"), true);
               }


            .. tb-code:: cpp
               :name: cp_7_AC_1a
               :caption: Example cp_7_AC_1a
               :run-after: cp_7_AC_1a-support
               :compileargs: ['-Wall', '-std=c++11']

               #include <cctype>
               #include <iostream>
               #include <string>

               bool is_palindrome (std::string input) {
                   int front = 0;
                   int back = input.size() - 1;
                   while (front < back) {
                       while (!std::isalpha(input[front])) {
                           ++front;
                       }
                       while (!std::isalpha(input[back])) {
                           --back;
                       }
                       if (input[front] != input[back]) {
                           return false;
                       }
                       ++front;
                       --back;
                   }
                   return true;
               }

   .. tb-tab:: Q2

      How much does Bubba love shrimp? Probably a lot. But how many times does the word "shrimp" come
      up in his monologue? Write a function ``count_word`` that counts the number of times a given word 
      appears in a given string. ``count_word`` should take two strings ``input`` and ``word`` as parameters and return an ``int``.
      Feel free to use the ``stringToLower`` function we wrote earlier.

      .. tb-code:: cpp
         :name: cp_7_AC_2q
         :caption: Example cp_7_AC_2q
         :compileargs: ['-Wall', '-std=c++11']

         #include <cctype>
         #include <iostream>
         #include <string>


         void stringToLower (string &input) {
            int i = 0;
            while (i < input.size()) {
                if (std::isalpha(input[i]) != 0 && std::isupper(input[i]) != 0) {
                    input[i] = std::tolower(input[i]);
                }
                ++i;
            }
         }

         int count_word (string input, string word) {
             // Write your implementation here.
         }

         int main() {
             string quote =
                 "Anyway, like I was sayin', shrimp is the fruit of the sea. You can "
                 "barbecue it, boil it, broil it, bake it, saute it. Dey's uh, "
                 "shrimp-kabobs, shrimp creole, shrimp gumbo. Pan fried, deep fried, "
                 "stir-fried. There's pineapple shrimp, lemon shrimp, coconut shrimp, "
                 "pepper shrimp, shrimp soup, shrimp stew, shrimp salad, shrimp and "
                 "potatoes, shrimp burger, shrimp sandwich. That- that's about "
                 "it.";
             cout << "Your output: " << count_word(quote, "shrimp") << ", Correct output: 14" << endl; 
         }

   .. tb-tab:: Q3

      .. tb-group::
         :name: cp_7_3

         .. tb-tab:: Question

            Write a void function ``censor_word`` that censors a given word from a given string and prints
            out the new string. ``censor_word`` should take two strings ``input`` and ``word`` as parameters
            and prints out ``input`` with every occurence of ``word`` censored with asterisks. For example, 
            ``censor_word ("I really, really, really, really, really, really like you", "really")`` results in 
            the following output:

            :: 

               I ******, ******, ******, ******, ******, ****** like you

            .. tb-code:: cpp
               :name: cp_7_AC_3q
               :caption: Example cp_7_AC_3q
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>
               #include <string>
               using std::string;

               void censor_word (string input, string word) {
                   // Write your implementation here.
               }

               int main() {
                   censor_word ("I really, really, really, really, really, really like you", "really");
               }


         .. tb-tab:: Answer

            Below is one way to implement the program. We use a while loop to
            repeatedly search for instances of word in input. Once found, we replace 
            the length of the word with asterisks.

            .. tb-code:: cpp
               :name: cp_7_AC_3a
               :caption: Example cp_7_AC_3a
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>
               #include <string>
               using std::string;

               void censor_word(string input, string word) {
                   int length = word.size();
                   while (input.find(word) != std::string::npos) {
                       int index = input.find(word);
                       int i = 0;
                       while (i < length) {
                           input[index + i] = '*';
                           ++i;
                       }
                   }
                   std::cout << input;
               }

               int main() {
                   censor_word ("I really, really, really, really, really, really like you", "really");
               }

   .. tb-tab:: Q4

      Write a void function ``remove_word`` that removes a given word from a given string and prints
      out the new string. ``remove_word`` should take two strings ``input`` and ``word`` as parameters
      and prints out ``input`` with every occurence of ``word`` removed. Use string concatenation and the C++
      string function ``substr``. ``substr`` takes two parameters, a starting index and a length. For example, 
      if ``string greeting = "hello world"``, then ``greeting.substr(6, 5)`` returns the string ``"world"``.  
      Test your function in main. The output should be:

      :: 

          Gucci , Gucci , Gucci , Gucci

      .. tb-code:: cpp
         :name: cp_7_AC_4q
         :caption: Example cp_7_AC_4q
         :compileargs: ['-Wall', '-std=c++11']

         #include <iostream>
         #include <string>

         void remove_word (std::string input, std::string word) {
             // Write your implementation here.
         }

         int main() {
             remove_word ("Gucci gang, Gucci gang, Gucci gang, Gucci gang", "gang");
         }

   .. tb-tab:: Q5

      .. tb-group::
         :name: cp_7_5

         .. tb-tab:: Question

            ROT13 is a simple letter substitution cipher that shifts every letter forward by 13,
            looping around if necessary. For example, the letter 'a', 1st in the alphabet, becomes
            the letter 'n', 14th in the alphabet. The letter 'r', 18th in the alphabet, becomes the 
            letter 'e', 5th in the alphabet. Since the alphabet has 26 letters and 13 is exactly half, 
            a message encrypted using ROT13 can be decrypted by calling ROT13 on the encrypted message.
            Write the function ``rotate13``, which takes a ``string input`` as a parameter and returns 
            an encrypted ``string``. Test your function in ``main``.

            .. tb-code:: cpp
               :name: cp_7_AC_5q
               :caption: Example cp_7_AC_5q
               :compileargs: ['-Wall', '-std=c++11']

               #include <cctype>
               #include <iostream>
               #include <string>

               std::string rotate13 (std::string message) {
                   // Write your implementation here.
               }

               int main() {
                   using std::cout;
                   string original = "Encrypt me then decrypt me!";
                   string encrypted = rotate13 (original);
                   string decrypted = rotate13 (encrypted);
                   cout << "Original string: " << original << '\n';
                   cout << "Encrypted string: " << encrypted << '\n';
                   cout << "Decrypted string: " << decrypted << '\n';

                   // Uncomment and run the code below once your function works!
                   // string secretMessage = "Pbatenghyngvbaf! Lbh'ir fhpprffshyyl vzcyrzragrq EBG13 naq qrpbqrq gur frperg zrffntr :)";
                   // cout << rotate13 (secretMessage) << '\n';
               }


         .. tb-tab:: Answer

            Below is one way to implement the ``rotate13`` function. We use a ``while`` loop to
            go through all the letters in the ``string``. If the letter is between 'a' and 'n' or 
            'A' and 'N', we use character operations to add 13 to each letter. Otherwise,
            we subtract 13 from each letter. We return the encrypted message at the end.

            .. tb-code:: cpp
               :name: cp_7_AC_5a
               :caption: Example cp_7_AC_5a
               :compileargs: ['-Wall', '-std=c++11']

               #include <cctype>
               #include <iostream>
               #include <string>
               using std::string;

               string rotate13(string message) {
                   size_t pos = 0;
                   while (pos < message.size()) {
                      char& letter = message[pos];
                       if (std::isalpha(letter) != 0) {
                          if ((std::islower(letter) != 0 && letter < 'n') ||
                              (std::isupper(letter) != 0 && letter < 'N')) {
                            letter = letter + 13;
                          } else {
                            letter = letter - 13;
                          }
                       }
                       ++pos;
                   }
                   return message;
               }

               int main() {
                   using std::cout;
                   string original = "Encrypt me then decrypt me!";
                   string encrypted = rotate13 (original);
                   string decrypted = rotate13 (encrypted);
                   cout << "Original string: " << original << '\n';
                   cout << "Encrypted string: " << encrypted << '\n';
                   cout << "Decrypted string: " << decrypted << '\n';

                   string secret = "Pbatenghyngvbaf! Lbh'ir fhpprffshyyl vzcyrzragrq EBG13 naq qrpbqrq gur frperg zrffntr :)";
                   cout << rotate13 (secret) << '\n';
               }

   .. tb-tab:: Q6

      Write the function ``reverse_word`` which takes a ``string input``, reverses it,
      and returns the reversed ``string``. Run and test your code!

      .. tb-code:: cpp
         :name: cp_7_AC_6q-support
         :hidden:
         :compileargs: ['-Wall', '-std=c++11']

         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, 
                     const T& actual, 
                     const T& expected,
                     const Compare& op = Compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
           if(op(actual, expected)) {
              std::cout << " OK      \n";
              return;
           }
           std::cout << " FAILED\n";
           std::cout << "\treceived [" << std::boolalpha << actual
                     << "], but expected [" << expected << "]\n";
           exit(1);
         }
         int main() {
           check("reverse 'hello'", reverse_word("hello"), "olleh");
           check("reverse 'world!'", reverse_word("world!"), "!dlrow");
           check("reverse 'racecar'", reverse_word("racecar"), "racecar");
         }



      .. tb-code:: cpp
         :name: cp_7_AC_6q
         :caption: Example cp_7_AC_6q
         :run-after: cp_7_AC_6q-support
         :compileargs: ['-Wall', '-std=c++11']

         #include <string>

         std::string reverse_word (std::string input) {
             // Write your implementation here.
         }

   .. tb-tab:: Q7

      .. tb-group::
         :name: cp_7_7

         .. tb-tab:: Question

            Write the function ``capitalize``, which takes a ``string input`` as a parameter.
            ``capitalize`` capitalizes the first letter of every word, and returns the new ``string``.

            .. tb-code:: cpp
               :name: cp_7_AC_7q
               :caption: Example cp_7_AC_7q
               :compileargs: ['-Wall', '-std=c++11']

               #include <cctype>
               #include <iostream>
               #include <string>

               std::string capitalize (std::string input) {
                   // Write your implementation here.
               }

               int main() {
                   std::cout << capitalize ("every word in this string should be capitalized!\n");
                   std::cout << capitalize ("this String As well\n");
               }


         .. tb-tab:: Answer

            Below is one way to implement the ``capitalize`` function. We use a ``while`` loop to
            go through all the ``char``\s in the ``string``. We capitalize the first character
            and all characters following a space using ``toupper``. At the end, we return the ``string``.

            .. tb-code:: cpp
               :name: cp_7_AC_7a
               :caption: Example cp_7_AC_7a
               :compileargs: ['-Wall', '-std=c++11']

               #include <cctype>
               #include <iostream>
               #include <string>

               std::string capitalize (std::string input) {
                   size_t pos = 0;
                   while (pos < input.size()) {
                       if (pos == 0) {
                           input[pos] = std::toupper(input[pos]);
                       }
                       else if (input[pos-1] == ' ') {
                           input[pos] = std::toupper(input[pos]);
                       }
                       ++pos;
                   }
                   return input;
               }

               int main() {
                   std::cout << capitalize ("every word in this string should be capitalized!\n");
                   std::cout << capitalize ("this String As well\n");
               }



   .. tb-tab:: Q8

      Write the function ``count_vowels`` which takes a ``string input`` and returns
      the number of vowels in the ``string``.
      For this exercvise, 'a', 'e', 'i', 'o', and 'u' are vowels.
      Run and test your code!

      .. tb-code:: cpp
         :name: cp_7_AC_8q-support
         :hidden:
         :compileargs: ['-Wall', '-std=c++11']

         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, 
                     const T& actual, 
                     const T& expected,
                     const Compare& op = Compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
           if(op(actual, expected)) {
              std::cout << " OK      \n";
              return;
           }
           std::cout << " FAILED\n";
           std::cout << "\treceived [" << std::boolalpha << actual
                     << "], but expected [" << expected << "]\n";
           exit(1);
         }
         int main() {
           check("count 'onomatopoeia'", count_vowels("onomatopoeia"), 8);
           check("count 'cycsts!'", count_vowels("cycsts"), 0);
           check("count 'vowels'", count_vowels("vowels"), 2);
         }




      .. tb-code:: cpp
         :name: cp_7_AC_8q
         :caption: Example cp_7_AC_8q
         :run-after: cp_7_AC_8q-support
         :compileargs: ['-Wall', '-std=c++11']

         #include <string>

         int count_vowels (std::string input) {
            // Write your implementation here.
         }

   .. tb-tab:: Q9

      .. tb-group::
         :name: cp_7_9

         .. tb-tab:: Question

            Write the function ``longest_word``, which takes a ``string input`` as a parameter.
            ``longest_word`` returns the words with the most letters in ``input``. If there's a tie,
            return the first word. Use the ``substr`` function. Run and test your code!

            .. tb-code:: cpp
               :name: cp_7_AC_9q-support
               :hidden:
               :compileargs: ['-Wall', '-std=c++11']

               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class T, class Compare = std::equal_to<T>>
               void check (const std::string& name, 
                           const T& actual, 
                           const T& expected,
                           const Compare& op = Compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << std::boolalpha << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                  using std::string;
                  check("Test 1", longest_word("what is the longest word in this string"), string("longest"));
                  check("Test 2", longest_word("these words are very close in size"), string("these"));
                  check("Test 3", longest_word("vowels"), string("vowels"));
               }



            .. tb-code:: cpp
               :name: cp_7_AC_9q
               :caption: Example cp_7_AC_9q
               :run-after: cp_7_AC_9q-support
               :compileargs: ['-Wall', '-std=c++11']

               #include <string>

               std::string longest_word (std::string input) {
                   // Write your implementation here.
               }

         .. tb-tab:: Answer

            Below is one way to implement the ``longest_word`` function. We use a ``while`` loop to
            go through all the ``char``\s in the ``string``. We use variables to keep track of the
            longest word, the longest amount of letters, and the length of the current word. We
            can determine the length of a word by counting the number of ``char``\s between spaces.
            If the length is greater than the max, length becomes the new max and we update the longest word.
            This keeps repeating until we reach the end of the string, and the longest word is returned.

            .. tb-code:: cpp
               :name: cp_7_AC_9a-support
               :hidden:
               :compileargs: ['-Wall', '-std=c++11']

               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class T, class Compare = std::equal_to<T>>
               void check (const std::string& name, 
                           const T& actual, 
                           const T& expected,
                           const Compare& op = Compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                  if(op(actual, expected)) {
                    std::cout << " OK      \n";
                    return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << std::boolalpha << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                  using std::string;
                  check("Test 1", longest_word("what is the longest word in this string"), string("longest"));
                  check("Test 2", longest_word("these words are very close in size"), string("these"));
                  check("Test 3", longest_word("vowels"), string("vowels"));
               }



            .. tb-code:: cpp
               :name: cp_7_AC_9a
               :caption: Example cp_7_AC_9a
               :run-after: cp_7_AC_9a-support
               :compileargs: ['-Wall', '-std=c++11']

               #include <string>

               std::string longest_word (std::string input) {
                   size_t pos = 0;
                   std::string longest;
                   int max_length = 0;
                   while (pos < input.size()) {
                       int word_length = 0;
                       while (input[pos] != ' ' && pos < input.size()) {
                           ++word_length;
                           ++pos;
                       }
                       if (word_length > max_length) {
                           max_length = word_length;
                           longest = input.substr(pos - max_length, max_length);
                       }
                       ++pos;
                   }
                   return longest;
               }

   .. tb-tab:: Q10

      Camel case is the practice of writing phrases without spaces or punctuation,
      indicating the separation of words using capital letter. For example, "camel case"
      in camel case is "camelCase". Snake case is the practice of writing phrases
      where each space is replaced by an underscore. For example, "snake case"
      in snake case is "snake_case". Write the functions ``snake_to_camel`` and ``camel_to_snake``.
      Each function takes a ``string input`` and returns the input using the other stylization.
      Feel free to use any ``string`` functions you'd like. Run and test your code!

      .. tb-code:: cpp
         :name: cp_7_AC_10q-support
         :hidden:
         :compileargs: ['-Wall', '-std=c++11']

         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, 
                     const T& actual, 
                     const T& expected,
                     const Compare& op = Compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
           if(op(actual, expected)) {
              std::cout << " OK      \n";
              return;
           }
           std::cout << " FAILED\n";
           std::cout << "\treceived [" << std::boolalpha << actual
                     << "], but expected [" << expected << "]\n";
           exit(1);
         }
         int main() {
           using std::string;
           check("Snake to Camel case 1", snake_to_camel("turn_this_into_camel_case"), string("turnThisIntoCamelCase"));
           check("Snake to Camel case 2", snake_to_camel("hello_world"), string("helloWorld"));
           check("Snake to Camel case 3", snake_to_camel("code"), string("code"));

           check("Camel to Snake case 1", camel_to_snake("turnThisIntoSnakeCase"), string("turn_this_into_snake_case"));
           check("Camel to Snake case 2", camel_to_snake("helloWorld"), string("hello_world"));
           check("Camel to Snake case 3", camel_to_snake("code"), string("code"));
         }


      .. tb-code:: cpp
         :name: cp_7_AC_10q
         :caption: Example cp_7_AC_10q
         :run-after: cp_7_AC_10q-support
         :compileargs: ['-Wall', '-std=c++11']

         #include <string>
         using std::string;

         string snake_to_camel (string input) {
              // Write your implementation here.
         }

         string camel_to_snake (string input) {
              // Write your implementation here.
         }

