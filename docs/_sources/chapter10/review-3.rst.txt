Activecode Exercises
--------------------

Answer the following **Activecode** questions to assess what you have learned in this chapter.

.. tabbed:: self_check

   .. tab:: Q1


      .. tabbed:: vectors_a1

         .. tab:: Question

            .. activecode:: vectors_a1q
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:


               Fix the code below so that it creates a vector with 5 elements
               all initialized to 1, and changes
               the third element of that vector to a 2.
               ~~~~
               int make_vector () {
                   vector<int> nums (5) = 1;
                   return nums;
               }

         .. tab:: Answer

            .. activecode:: vectors_a1a
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:


               Below is one way to fix the program.

               - Always include the ``<vector>`` header when using vectors.
               - To initialize all vector elements to a certain value,
                 you must include that as a second argument after the size.
               - Finally, vectors are zero-indexed.
                 The third element is at index '2'.

               ~~~~
               #include <iostream>
               #include <vector>

               std::vector<int> make_vector () {
                   std::vector<int> nums (5,1);
                   nums[3] = 2;
                   return nums;
               }

               ====
               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>

               template <class T, class Compare = std::equal_to<T>>
               void check (const std::string& name, const T& actual, 
                           const T& expected, const Compare& op = Compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                 if(op(actual, expected)) {
                   std::cout << " OK      \n";
                   return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                 std::vector<int> expected = {1,1,1,2,1};
                 std::vector<int> actual = make_vector();
                 std::vector<std::string> ord = {"first", "second", "third", "fourth", "fifth"};
                 for (size_t i = 0; i<expected.size(); ++i) {
                   check(ord[i] , actual[i],  expected[i]);
                 }
               }

   .. tab:: Q2

      .. activecode::  vectors_a2
         :language: cpp
         :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
         :nocodelens:


         Fix the function below so that it returns how many even numbers are in ``nums``.
         ~~~~
         #include <vector>

         int count_even (const vector<int>& nums) {
             for (int i = 0; i < nums.size(); i++) {
                 if (i % 2 == 0) {
                     count = count + 1;
                 }
             }
             return count;
         }

         ====
         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, const T& actual, 
                     const T& expected, const Compare& op = Compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
           if(op(actual, expected)) {
             std::cout << " OK      \n";
             return;
           }
           std::cout << " FAILED\n";
           std::cout << "\treceived [" << actual
                     << "], but expected [" << expected << "]\n";
           exit(1);
         }
         int main() {
           std::vector<int> expected = {1,1,1,2,1};
           std::vector<int> actual = make_vector();
           std::vector<std::string> ord = {"first", "second", "third", "fourth", "fifth"};
           for (size_t i = 0; i<expected.size(); ++i) {
             check(ord[i] , actual[i],  expected[i]);
           }
         }


   .. tab:: Q3

      .. tabbed:: vectors_a3

         .. tab:: Question

            .. activecode:: vectors_a3q
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:


               Fix the function below so that it creates a vector of all of the
               words in ``words`` that end with the passed character.
               ~~~~
               #include <iostream>
               #include <string>
               #include <vector>

               int ends_with (const std::vector<std::string>& words, char c) {
                   int count;
                   for (size_t i = 0; i <= words.size(); i++) {
                       last = words.size() - 1;
                       if (words[last] == c) {
                           ++count;
                       }
                   }
                   return count;
               }

               ====
               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class T, class Compare = std::equal_to<T>>
               void check (const std::string& name, const T& actual, 
                           const T& expected, const Compare& op = Compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                 if(op(actual, expected)) {
                   std::cout << " OK      \n";
                   return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                 std::vector<std::string> words = 
                          {"quick", "brown", "fox", "jumps", "dogs"};
                 check("ends with n", ends_with(words, 'n'), 1);
                 check("ends with s", ends_with(words, 's'), 2);
                 check("ends with e", ends_with(words, 'e'), 0);
                 check("ends with x", ends_with(words, 'x'), 1);
                 check("ends with k", ends_with(words, 'k'), 1);
               }


         .. tab:: OK Answer

            .. activecode:: vectors_a3a
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:


               Below is one way to fix the function.
               However it is complicated and error prone.

               We must initialize ``count`` to zero and
               declare ``last`` as an integer.
               To access a string *inside* of ``vec``,  we use ``vec[i]``.
               To get the last character, we must index the
               string to the last index, which is one less than the length of the string.
               ~~~~
               #include <string>
               #include <vector>

               int ends_with (const std::vector<std::string>& words, char c) {
                   int count = 0;
                   for (size_t i = 0; i < words.size(); i++) {
                       int last = words[i].size() - 1;
                       if (words[i][last] == c) {
                           ++count;
                       }
                   }
                   return count;
               }

               ====
                 #include <functional>
                 #include <iomanip>
                 #include <iostream>
                 #include <string>
                 template <class T, class Compare = std::equal_to<T>>
                 void check (const std::string& name, const T& actual, 
                             const T& expected, const Compare& op = Compare())
                 {
                   std::cout << std::left << std::setfill('.') 
                             << std::setw(50) << name 
                             << std::setw(7) <<  std::left;
                   if(op(actual, expected)) {
                     std::cout << " OK      \n";
                     return;
                   }
                   std::cout << " FAILED\n";
                   std::cout << "\treceived [" << actual
                             << "], but expected [" << expected << "]\n";
                   exit(1);
                 }
                 int main() {
                   std::vector<std::string> words = 
                            {"quick", "brown", "fox", "jumps", "dogs"};
                   check("ends with n", ends_with(words, 'n'), 1);
                   check("ends with s", ends_with(words, 's'), 2);
                   check("ends with e", ends_with(words, 'e'), 0);
                   check("ends with x", ends_with(words, 'x'), 1);
                   check("ends with k", ends_with(words, 'k'), 1);
                 }



         .. tab:: Better Answer

            .. activecode:: vectors_a3a2
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:


               Below is a simpler way to fix the function.
               We still must initialize ``count`` to zero.
               However, it is better to avoid array indexing completely.
               In general, it is always better to avoid array indexing
               if it is not needed.
               ~~~~
               #include <string>
               #include <vector>

               int ends_with (const std::vector<std::string>& words, char c) {
                   int count = 0;
                   for (const std::string& word: words) {
                       if (word.back() == c) {
                           ++count;
                       }
                   }
                   return count;
               }
               ====
               #include <functional>
               #include <iomanip>
               #include <iostream>
               #include <string>
               template <class T, class Compare = std::equal_to<T>>
               void check (const std::string& name, const T& actual, 
                           const T& expected, const Compare& op = Compare())
               {
                 std::cout << std::left << std::setfill('.') 
                           << std::setw(50) << name 
                           << std::setw(7) <<  std::left;
                 if(op(actual, expected)) {
                   std::cout << " OK      \n";
                   return;
                 }
                 std::cout << " FAILED\n";
                 std::cout << "\treceived [" << actual
                           << "], but expected [" << expected << "]\n";
                 exit(1);
               }
               int main() {
                 std::vector<std::string> words = 
                          {"quick", "brown", "fox", "jumps", "dogs"};
                 check("ends with n", ends_with(words, 'n'), 1);
                 check("ends with s", ends_with(words, 's'), 2);
                 check("ends with e", ends_with(words, 'e'), 0);
                 check("ends with x", ends_with(words, 'x'), 1);
                 check("ends with k", ends_with(words, 'k'), 1);
               }


   .. tab:: Q4

      .. activecode::  vectors_a4
         :language: cpp
         :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
         :nocodelens:

         Someone could have COVID 19 if their temperature is above 99.9 degrees Fahrenheit.  Finish 
         the code below so that it counts how many students in the class may have been exposed.
         ~~~~

         int count_covid (const std::vector<double>& temps) {
         }
         ====

         #include <functional>
         #include <iomanip>
         #include <iostream>
         #include <string>
         template <class T, class Compare = std::equal_to<T>>
         void check (const std::string& name, const T& actual, 
                     const T& expected, const Compare& op = Compare())
         {
           std::cout << std::left << std::setfill('.') 
                     << std::setw(50) << name 
                     << std::setw(7) <<  std::left;
           if(op(actual, expected)) {
             std::cout << " OK      \n";
             return;
           }
           std::cout << " FAILED\n";
           std::cout << "\treceived [" << actual
                     << "], but expected [" << expected << "]\n";
           exit(1);
         }
         int main() {
           std::vector<double> temps = {
               98.6, 97.8, 100.3, 97.2, 98.7, 97.8, 
               99.8, 96.9, 98.2, 99.1, 99.9};
           check("test 1", count_covid(temps), 1);
           temps[2]= 97.4;
           check("test 2", count_covid(temps), 0);
           temps[2]= 100.3;
           temps[0]= 99.99;
           check("test 3", count_covid(temps), 2);
           temps.push_back(103.5);
           temps.push_back(104.0);
           check("test 4", count_covid(temps), 4);
         }


   .. tab:: Q5

      .. tabbed:: vectors_a5

         .. tab:: Question

            .. activecode:: vectors_a5q
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:

               Finish the code below so that it creates removes elements from the end of the vector until
               it ends with ``"stop"``.
               ~~~~

               int main () {
                   std::vector<string> words = {"roses", "are", "red", "violets", "stop", "are", "blue"}
               
                   while(          ) {

                   }

               }

         .. tab:: Answer

            .. activecode:: vectors_a5a
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:

               Below is one way to finish the program.  We just use the ``pop_back`` function until the 
               last element of the vector is ``"stop"``.
               ~~~~
               #include <string>
               #include <vector>

               int main () {
                   std::vector<std::string> words = {"roses", "are", "red", "violets", "stop", "are", "blue"};
                   while (words.back() != "stop"){
                       words.pop_back();
                   }
               }


   .. tab:: Q6

      .. activecode::  vectors_a6
         :language: cpp
         :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
         :nocodelens:

         Write the function ``ends_even`` that takes a vector and removes 
         elements from the end of the vector until
         it ends with an even number.

         No tests are provided for this question.
         ~~~~
         #include <vector>


   .. tab:: Q7

      .. tabbed:: vectors_a7

         .. tab:: Question

            .. activecode:: vectors_a7q
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:

               Write a function called ``all_have_char`` that returns a bool if
               every string in the provided vector contains the test character.
               It should return true only if all strings contain the character.

               No tests are provided for this question.
               ~~~~
               #include <vector>

         .. tab:: Answer

            .. activecode:: vectors_a7a
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:

               Below is one way to finish the program.
               We loop through the vector, and search each string.
               If the string has the character, then it is added to ``count``.
               We then check whether ``count``
               is equal to the number of elements in ``vec`` and return a boolean.
               ~~~~
               #include <cstddef>
               #include <vector>


               bool all_have_char (const vector<string>& data, char c) {
                   size_t count = 0;
                   for (const string& tokens: data) {
                      for (const char tok: tokens) {
                           if (tok == c) {
                               count++;
                           }
                       }
                   }
                   return count == data.size();
               }
               

   .. tab:: Q8

      .. tabbed:: vectors_a8

         .. tab:: Question

            .. activecode:: vectors_a9q
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:

               Write a function ``mean`` which returns the average of a vector of numbers.

               No tests are provided for this question.
               ~~~~


         .. tab:: Answer

            .. activecode:: vectors_a8a
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:

               Below is one way to finish the program.
               First we take the sum, then divide the sum by the number
               of elements in ``nums``.

               In the solution below, an empty vector results in a
               divide by zero error.

               How could we guard against that?
               ~~~~
               #include <vector>

               double mean (const vector<double> nums) {
                   double sum = 0;
                   for (const auto& value: nums) {
                       sum += value;
                   }
                   return sum/nums.size();
               }


   .. tab:: Q9

      .. activecode::  vectors_a9
         :language: cpp
         :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
         :nocodelens:

         Write the function ``hundyBundy`` that returns a count of all numbers
         in a vector that are divisible by 100.

         No tests are provided for this question.
         ~~~~
         #include <vector>

   .. tab:: Q10

      .. tabbed:: vectors_a10

         .. tab:: Question

            .. activecode:: vectors_a11q
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:

               Write the function ``make_odd`` which subtracts 1 from every
               even number in a vector of integers.
               We don't want any negative values so don't subtract 1 from 0.
               ( remember to take in the vector by reference to make changes to the actual vector! )
               ~~~~
               #include <vector>


         .. tab:: Answer

            .. activecode:: vectors_a11a
               :language: cpp
               :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
               :nocodelens:

               Below is one way to finish the program.
               We us the modulus operator to check for even numbers and decrement them.
               we keep an extra check for 0 to make sure we are not decrementing 0.
               ~~~~
               #include <vector>

               bool is_even (int value) {
                 return value % 2 == 0;
               }

               void make_odd ( std::vector<int>& nums) {
                 for (int& value: nums) {
                   if (is_even(value) && value > 0) {
                     --value;
                   } 
                 }
               }


      .. activecode::  vectors_a11
         :language: cpp
         :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
         :nocodelens:

         Write the function ``weird_print`` that prints the first half of a
         vector of integers in reverse order
         and then prints the second half in the order present in the vector.
         If we start with ``{1,2,3,4,5,6}``
         we would print ``3 2 1 4 5 6``.

         ~~~~
         
