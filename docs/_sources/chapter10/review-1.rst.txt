Multiple Choice Exercises
-------------------------

Answer the following **Multiple Choice** questions to assess what you have learned in this chapter.

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: vectors_mc1

          Suppose you are collecting data for a science experiment. You are to perform three trials of eight temperature
          readings measured in degrees fahrenheit to the nearest hundredth and initialized to *freezing*.  Choose the vector 
          that has the proper amount of storage for this scenario.

          -   ``vector<int> temps (24, 32.00);``

              -   We can't declare the vector as an integer type because all temperature readings
                  will be truncated.

          -   ``vector<double> temps (24, 32.00);``

              +   First comes the vector size, *then* the initial values.

          -   ``vector<double> temps (0.00, 24);``

              -   Freezing is 32 degrees fahrenheit.  The order of parameters is incorrect.

          -   ``vector<double> temps (32, 24.00);``

              -   This statement creates a vector size 32 with elements initialized to 24.00 degress fahrenheit.


      .. mchoice:: vectors_mc2

          Suppose the following code is run:
          
          .. code-block::
          
             vector<string> lauren = {"happy", "to", "you", "September", "birthday", "girl"}

          How would you save the string ``"birthday"`` from ``lauren`` to the variable ``nurse``?

          -   ``nurse = lauren[4]``

              +   Vectors are zero-indexed, so the fifth element is the fourth index.

          -   ``nurse = lauren[5]``

              -    Remember, vectors are zero-indexed!

          -   ``nurse = lauren[6]``

              -   Remember, vectors are zero-indexed!

          -   ``nurse = lauren(4)``

              -   This is not proper vector indexing.

          -   ``nurse = lauren(5)``

              -   This is not proper vector indexing.  Also, vectors are zero-indexed.

      .. mchoice:: vectors_mc3

          What gets printed when the following code is run:
          
          .. code-block::
          
             vector<string> chant = {"Hail", "to", "the", "victors", "valiant"};
             chant[0]=chant[3];
             chant[3]=chant[0];
             chant[1]=chant[0];

             for ( size_t i = 0; i < chant.size(); i++ ){
                  cout << chant[1][i] << ' ';
             }
          
          -   victors victors the victors valiant

              -   Although this is the final version of ``chant``, we are not printing ``chant``!

          -   error! we run into an error somewhere in the execution due to an out of bounds access.

              -    Remember, ``chant`` at index 1 is no longer "hail".

          -   v i c t o r s 

              -   You are thinking of the correct word but consider upto what index we print.

          -   v i c t o 

              +   Correct! we print the first 5 letters of the string at index 1 which is "victors".



      .. mchoice:: vectors_mc4

          Select all of the following statments that correctly make a copy of ``lauren``.
          
          .. code-block::
          
             vector<string> lauren = {"happy", "to", "you", "September", "birthday", "girl"}

          How would you save the string ``"birthday"`` from ``lauren`` to the variable ``nurse``?

          -   ``vector<string> harry (lauren)``

              +   This syntax is correct, but isn't used often.

          -   ``vector<string> lauren (ella)``

              -   You make a copy of the vector in parentheses.

          -   ``vector<string> lauren = mariah``

              -   Remember how assignment statements work!

          -   ``vector<katie> string = lauren``

              -   This is not proper syntax.

          -   ``vector<string> mariah = lauren``

              +   This is the most common syntax.


      .. mchoice:: vectors_mc5

          What is the value of nums after the following code executes?
          
          .. code-block::
          
             int main () {
                 vector<int> nums = {0, 8, 5, 1, 4, 3};
                 for (int i = 0; i < 6; i++) {
                 for (const int& value: nums) {
                     if (value % 2 == 0) {
                        --value;   
                     }
                     value *= 2;
                 }
             }

          -   {0, 8, 5, 1, 4, 3}

              -   ``nums`` is modified inside of the loop.

          -   {0, 16, 10, 2, 8, 6}

              -   Take a look at the conditional.

          -   {0, 16, 8, 0, 8, 4}

              -   Take a closer look at the conditional.

          -   {-2, 14, 10, 2, 6, 6}

              +   All even numbers were decremeneted, then all numbers were multiplied by 2.

          -   {2, 18, 10, 2, 10, 6}

              -   Take a closer look at what happens inside of the conditional.


      .. mchoice:: vectors_mc6

          **Multiple Response** Select all ways to print out the contents of ``ryan`` without
          going out of bounds.
          
          .. code-block::
          
             vector<int> ryan = {2, 3, 1, 5, 6, 0, 0, 5, 4};

          -   .. code-block::
                 
                 for (int i = 0; i < ryan.size(); ++i) {
                     cout << ryan[i] << ' ';
                 }

              -   When we deal with the ``size`` function, we can't use type ``int``.

          -   .. code-block::
                 
                 for (size_t j = 0; j < ryan.size(); j++) {
                     cout << ryan[j] << ' ';
                 }

              +   When we deal with the ``size`` function, we must use type ``size_t``.

          -   .. code-block::
                 
                 for (int k = 0; k < 8; ++k) {
                     cout << ryan[k] << ' ';
                 }

              -   There are 9 elements, numbered 0 through 8, but here we only iterate through 8 of them.

          -   .. code-block::
                 
                 for (int n = 0; n < 9; n++) {
                     cout << ryan[n] << ' ';
                 }

              +   There are 9 elements numbered 0 through 8, and this statement iterates over all of them.

          -   .. code-block::
                 
                 for (int m = 0; m <= 8; ++m) {
                     cout << ryan[m] << ' ';
                 }

              +   There are 9 elements numbered 0 through 8, and this statement iterates over all of them.

          -   .. code-block::
                 
                 for (const int& n: ryan) {
                     cout << n << ' ';
                 }

              +   A range-for loop never goes out of bounds.



      .. mchoice:: vectors_mc7

          Suppose you want ``ryan`` to have the value

          .. code-block::
          
             vector<int> ryan = {2, 3, 1, 5, 6, 7, 8, 9};
          
          What vector functions will you use to achieve this, and how many times will you use them?
          Keep in mind, ``ryan`` is currently the following vector of integers.

          .. code-block::
          
             vector<int> ryan = {2, 3, 1, 5, 6, 0, 0, 5, 4};

          -   Use ``push_back`` 4 times with no arguments to get rid of the last 4 elements, then use ``push_back`` 3 times
              with arguments to specify which values you want to add to the end.

              -   You'll need to use two *different* functions to accomplish this task.

          -   Use ``push_back`` 4 times with no arguments to get rid of the last 4 elements, then use ``pop_back`` 3 times
              with arguments to specify which values you want to add to the end.

              -   ``push_back`` *pushes* new items onto the end of the vector, and ``pop_back`` *pops* old items off the end of the vector.

          -   Use ``pop_back`` 4 times with no arguments to get rid of the last 4 elements, then use ``pop_back`` 3 times
              with arguments to specify which values you want to add to the end.

              -   You'll need to use two *different* functions to accomplish this task.

          -   Use ``pop_back`` 4 times with no arguments to get rid of the last 4 elements, then use ``push_back`` 3 times
              with arguments to specify which values you want to add to the end.

              +   T``push_back`` *pushes* new items onto the end of the vector, and ``pop_back`` *pops* old items off the end of the vector.


      .. mchoice:: vectors_mc9

          Suppose you have defined the ``bar`` function as the following
          
          .. code-block::

              int bar (const vector<int>& vec, int num1, int num2) {
                  int count = 0;
                  for (const int& value: vec) {
                      if (value/num1 == 0 && value/num2 == 0) {
                          count++;
                      }
                  }
                  return count;
              }
          
          What would be printed in the following case?

          .. code-block::

              vector<int> numbers = {6, 8, 14, 21, 28, 35, 36, 42, 49, 70, 81, 98};
              cout << bar(numbers, 2, 7);

          -   1

              -   14 is 7 * 2. Don't forget about the other multiples of 7 and 2.

          -   2

              -   See if you can find the other multiples of 7 and 2.

          -   3

              -   See if you can find the other multiples of 7 and 2.
          
          -   4

              -   See if you can find the other multiples of 7 and 2.
          
          -   5

              +   14, 28, 42, 70, and 98 are all multiples of 7 and 2 and are counted by ``bar``.


      .. mchoice:: vectors_mc10

          Suppose you have defined the ``starts_with`` function as the following
          
          .. code-block::

              int starts_with (const vector<string> & words, char c) {
                  int count = 0;
                  int pos = 0;
                  for (size_t i = 0; i < words.size(); i++) {
                  for (const int& word: words) {
                      pos = word.find(' ');
                      if (std::string::npos != pos && word[pos + 1] == c) {
                          count++;
                      }
                  }
                  return count;
              }
          
          What would be printed in the following case?

          .. code-block::

              vector<string> names = {"Ross Meldrum", "Monica Morrissey", "Maria Geller", "Marty Bing"};
              cout << haw_many(names, 'M');

          -   1

              -   Is the function counting how many first and last ``names`` begin with ``"M"``?

          -   2

              +   The function is counting how many last names begin with ``"M"``.

          -   3

              -   Is the function counting how many first ``names`` begin with ``"M"``?
          
          -   4

              -   Is the function counting how many elements in ``names`` contain ``"M"``?
          
          -   5

              -   Is the function counting how many times ``"M"`` appears in ``names``?


      .. mchoice:: vectors_mc11

          Suppose you have defined the ``how_many`` function as the following
          
          .. code-block::

              int how_many (const vector<string>& words, char let) {
                  int count = 0;
                  for (const auto& word: words) {
                      for (const auto& c: word) {
                          if (c == let) {
                              count++;
                          }
                      }
                  }
                  return count;
              }
          
          What is the value of counts after the following code is run?

          .. code-block::

              vector<string> snacks = {"cheetos", "ruffles", "jalepeno chips", "oreos", "m&ms"};
              vector<char> letters = {'a', 'e', 'i', 'o', 'u'};
              vector<int> counts = {};
              for (const auto& c: letters) {
                  counts.push_back(how_many(snacks, c));
              }

          -   {1, 6, 2, 6, 2}

              -   What is being counted in ``counts``?

          -   {1, 4, 1, 3, 1}

              -   ``counts`` isn't a count of how many words each vowel appers in inside ``snacks``.

          -   {1, 6, 1, 4, 1}

              +   ``counts`` contains a count of how many times each vowel appers in ``snacks``.
          
          -   {1, 6, 2, 3, 2}

              -   What is being counted in ``counts``?
          
          -   Error!

              -   There isn't anything wrong with the code that would cause an error.

      .. mchoice:: vectors_mc12

          Suppose you have defined the ``repeater`` function as the following
          
          .. code-block::

              int repeater (const vector<int>& vec) {
                  int count = 0;
                  for (size_t i = 0; i < vec.size(); i++) {
                      for (size_t j = 0; j < vec.size(); j++) {
                          if ((vec[j] == vec[i]) && (i != j)) {
                              count++;
                          }
                      }
                  }
                  return count;
              }
          
          What is the value of counter after the following code is run?

          .. code-block::

              vector<int> vals = {1,1,3,2,2,3,3,4,5,6,7,4,4,5};
              int counter = repeater(vals);

          -   169

              -   What is being counted by ``repeater`` in each iteration of the outer loop? Definitely not everything!

          -   32

              -   ``repeater`` does count repeats but does it consider values at the same indexes repeats?

          -   18

              +   ``repeater`` considers the number of times each index shares a value with any of the other indices.
          
          -   13

              -   ``repeater`` dosen't simply count the number of elements.

