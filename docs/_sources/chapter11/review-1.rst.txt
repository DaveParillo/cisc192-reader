Multiple Choice Exercises
-------------------------

Answer the following **Multiple Choice** questions to assess what you have learned in this chapter.

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: random_mc1

          Suppose you are randomly assigning students to discussions 1-8.  How would you do this correctly?  Assume
          you have alreay implemented the following code.
          
          .. code-block::

             int x = random ();
          
          -   .. code-block ::
              
                 int y = x % 7;
                 y = y + 1;

              +   The first part creates a random number between 0 and 7 (8 numbers) and the second part adds 1 so that
                  our random number is actually between 1 and 8.

          -   .. code-block ::
              
                 int y = x % 8;
                 y = y + 1;

              -   The first part creates a random number between 0 and 8 (9 numbers).  This is too many.

          -   .. code-block ::
              
                 int y = x % 7;

              -   This creates a random number between 0 and 7 (8 numbers), which are not the numbers we are looking for.

          -   .. code-block ::
              
                 int y = x % 8;

              -   The first part creates a random number between 0 and 8 (9 numbers).  This is too many, and not the numbers we are looking for.


   .. tab:: Q2

      .. mchoice:: random_mc2

          Suppose you have defined the ``fizzBuzz`` function as the following
          
          .. code-block::

              int fizzBuzz (const vector<int> & vec, int num1, int num2) {
                  int count = 0;
                  for (size_t i = 0; i < vec.size(); i++) {
                      if (vec[i]/num1 == 0 && vec[i]/num2 == 0) {
                          count++;
                      }
                  }
                  return count;
              }
          
          What would be printed in the following case?

          .. code-block::

              vector<int> numbers = {6, 8, 14, 21, 28, 35, 36, 42, 49, 70, 81, 98};
              cout << fizzBuzz(numbers, 2, 7);

          -   1

              -   14 is 7 * 2. Don't forget about the other multiples of 7 and 2.

          -   2

              -   See if you can find the other multiples of 7 and 2.

          -   3

              -   See if you can find the other multiples of 7 and 2.
          
          -   4

              -   See if you can find the other multiples of 7 and 2.
          
          -   5

              +   14, 28, 42, 70, and 98 are all multiples of 7 and 2 and are counted by ``fizzBuzz``.


   .. tab:: Q3

      .. mchoice:: random_mc3

          Suppose you have defined the ``startsWith`` function as the following
          
          .. code-block::

              int startsWith (const vector<string> & vec, char c) {
                  int count = 0;
                  int pos = 0;
                  for (size_t i = 0; i < vec.size(); i++) {
                      pos = vec[i].find(" ");
                      if (vec[i][pos + 1] == c) {
                          count++;
                      }
                  }
                  return count;
              }
          
          What would be printed in the following case?

          .. code-block::

              vector<string> names = {"Ross Meldrum", "Monica Morrissey", "Maria Geller", "Marty Bing"};
              cout << howMany(names, 'M');

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


   .. tab:: Q4

      .. mchoice:: random_mc4

          Suppose you have defined the ``howMany`` function as the following
          
          .. code-block::

              int howMany (const vector<string>& vec, char let) {
                  int count = 0;
                  for (size_t i = 0; i < vec.size(); i++) {
                      for (size_t c = 0; c < vec[i].size(); c++) {
                          if (vec[i][c] == let) {
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
              for (int i = 0; i < letters.size(); ++i) {
                  counts.push_back(howMany(snacks, letters[i]));
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


   .. tab:: Q5

      .. mchoice:: random_mc5

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

