Mixed-Up Code Exercises
-----------------------

Answer the following **Mixed-Up Code** questions to assess what you have learned in this chapter.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: vectors_p1
         :no-indent:

         Construct a block of code that changes the first element of <code>vec</code> to a 6,
         multiplies the third element of <code>vec</code> by 2, and increments the last element 
         of <code>vec</code> by 1 (in that order).  This should work no matter what <code>vec</code> is.

         .. code-block:: cpp

            {{group}}
            vec[0] = 6;
            {{endgroup}}
            {{group}}
            vec[2] = vec[2] * 2;
            {{endgroup}}
            {{group}}
            last = vec.size() - 1;
            vec[last]++;
            {{endgroup}}
            {{distractor}}
            {{group}}
            vec[1] = 6; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            vec[0] == 6; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            vec[3] = vec[3] * 2; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            last = vec.size(); #distractor
            vec[last]++;
            {{endgroup}}

      .. tb-parsons::
         :name: vectors_p2
         :no-indent:

         Construct a block of code that creates a vector called <code>digs</code> whose elements are
         7, 8, 7, 8.  Then access elements to change the <code>digs</code> to contain the elements
         7, 4, 7, 4.  <b>Important</b>: Change the <code>8</code>'s to <code>4</code>'s in order of 
         increasing index.

         .. code-block:: cpp

            {{group}}
            vector<int> digs = {7, 8, 7, 8};
            {{endgroup}}
            {{group}}
            digs[1] = 4;
            {{endgroup}}
            {{group}}
            digs.pop_back();
            {{endgroup}}
            {{group}}
            digs.push_back(4);
            {{endgroup}}
            {{distractor}}
            {{group}}
            vector digs = {7, 8, 7, 8}; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            vector<int> digs = [7, 8, 7, 8]; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            digs[2] = 4; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            digs.pop_back(4); #distractor
            {{endgroup}}

      .. tb-parsons::
         :name: vectors_p3
         :no-indent:

         Construct a block of code that creates a vector called <code>nums</code> whose elements are five <code>1</code>'s.
         Then make a copy of this vector called <code>digits</code>, and use vector operations to change
         digits to <code>{1, 2, 3}</code>.

         .. code-block:: cpp

            {{group}}
            vector<int> nums (5, 1);
            {{endgroup}}
            {{group}}
            vector<int> digits = nums;
            {{endgroup}}
            {{group}}
            digits.pop_back();
            digits.pop_back();
            {{endgroup}}
            {{group}}
            digits[1]++;
            digits[2] = digits[2] * 3;
            {{endgroup}}
            {{distractor}}
            {{group}}
            vector nums = {1, 1, 1, 1, 1}; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            vector<int> nums = digits; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            digits.push_back(); #distractor
            digits.push_back();
            {{endgroup}}
            {{distractor}}
            {{group}}
            digits[2]++; #distractor
            digits[3] = digits[3] * 3;
            {{endgroup}}

      .. tb-parsons::
         :name: vectors_p4
         :no-indent:

         Construct a block of code that loops over a vector called <code>numbers</code>
         and transforms the vector so each element is doubled.

         .. code-block:: cpp

            {{group}}
            vector<int> numbers = {1, 2, 3, 4, 5};
            {{endgroup}}
            {{group}}
            for (size_t i = 0; i < numbers.size(); i++) {
            {{endgroup}}
            {{group}}
             numbers[i] = numbers[i] * 2;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}
            {{distractor}}
            {{group}}
            vector numbers = {1, 2, 3, 4, 5}; #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            for (size_t i = 1; i <= numbers.size(); ++i) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            for (int i = 0; i < numbers.size(); i++) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            numbers[i] * 2; #distractor
            {{endgroup}}

      .. tb-parsons::
         :name: vectors_p5
         :no-indent:

         Suppose you have the vector

         <pre> <code>

            vector<string> words = {"car", "cat", "switch", "princess"};

         </code> </pre>

         Construct a block of code that transforms the vector to

         <pre> <code>

            vector<string> words = {"cAr", "cAt", "switch", "mArio"}

         </code> </pre>

         .. code-block:: cpp

            {{group}}
            words.pop_back();
            {{endgroup}}
            {{group}}
            words.push_back("mario");
            {{endgroup}}
            {{group}}
            for (size_t i = 0; i < words.size(); ++i) {
            {{endgroup}}
            {{group}}
             for (size_t c = 0; c < words[i].size(); ++c) {
            {{endgroup}}
            {{group}}
              if (words[i][c] == 'a') {
            {{endgroup}}
            {{group}}
                  words[i][c] = 'A';
            {{endgroup}}
            {{group}}
              }
             }
            }
            {{endgroup}}
            {{distractor}}
            {{group}}
            words.pop_back("mario"); #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            for (int i = 0; i < words.size(); ++i) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            for (int c = 0; c < words[i].size(); ++c) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            words[i][c] == 'A'; #distractor
            {{endgroup}}

      .. tb-parsons::
         :name: vectors_p7
         :no-indent:

         Suppose <code>album</code> has already been defined as

         <pre> <code>

            vector<string> album = {"imagine", "needy", "NASA", "bloodline", "fake smile", "bad idea", "make up", "ghostin", "in my head", "7 rings", "thank u, next", "break up with your girlfriend, i'm bored"}

         </code> </pre>

         Construct a block of code that counts how many songs in <code>album</code> start with b.

         .. code-block:: cpp

            {{group}}
            count = 0
            {{endgroup}}
            {{group}}
            for (size_t i = 0; i < album.size(); i++) {
            {{endgroup}}
            {{group}}
             if (album[i][0] == 'b') {
            {{endgroup}}
            {{group}}
              ++count;
            {{endgroup}}
            {{group}}
             }
            }
            {{endgroup}}
            {{distractor}}
            {{group}}
            for (int i = 0; i < album.size(); i++) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            if (album[i] == 'b') { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            if (album[i][1] == 'b') { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            count++ #distractor
            {{endgroup}}

      .. tb-parsons::
         :name: vectors_p8
         :no-indent:

         Suppose you have the following two vectors to describe the weekly forecast

         <pre> <code>

            vector<double> temps = {82.0, 76.8, 74.3, 58.8, 79.2, 73.4, 80.1}
            vector<double> precip = {0.00, 0.30, 0.60, 0.90, 0.10, 0.20, 0.80}

         </code> </pre>

         Your family will go to the beach if the temperature at least 75 degrees and the chance
         of precipitation is less than 50%.  Construct a block of code that counts how many days
         your family can hit the beach on your vacation.

         .. code-block:: cpp

            {{group}}
            count = 0;
            {{endgroup}}
            {{group}}
            for (int i = 0; i < 7; ++i) {
            {{endgroup}}
            {{group}}
             if (temps[i] >= 75.0 && precip[i] < 0.50) {
            {{endgroup}}
            {{group}}
              ++count;
            {{endgroup}}
            {{group}}
             }
            }
            {{endgroup}}
            {{distractor}}
            {{group}}
            for (size_t i = 1; i <= 7; ++i) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            if (temps[i] > 75.0 && precip[i] <= 0.50) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            count++ #distractor
            {{endgroup}}

      .. tb-parsons::
         :name: vectors_p9
         :no-indent:

         Suppose you have the following vector <code>nouns</code>

         <pre> <code>

            vector<string> nouns = {"cereal", "Cocoa Puffs", "Mario", "luigi", "Aerosmith"};

         </code> </pre>

         Construct a block of code that creates a vector of the <b>proper</b> nouns in <code>nouns</code>.
         Use the <code>isupper</code> function to check if a letter is uppercase.

         .. code-block:: cpp

            {{group}}
            vector<string> proper = {};
            {{endgroup}}
            {{group}}
            for (size_t i = 0; i < nouns.size(); ++i) {
            {{endgroup}}
            {{group}}
             if (isupper(nouns[i][0])) {
            {{endgroup}}
            {{group}}
              proper.push_back(nouns[i]);
            {{endgroup}}
            {{group}}
             }
            }
            {{endgroup}}
            {{distractor}}
            {{group}}
            if (isupper(nouns[i][1])) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            proper.push_back(nouns[i][0]); #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            proper.pop_back(nouns[i]); #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            vector proper = {}; #distractor
            {{endgroup}}

      .. admonition:: Parsons exercise

         Suppose you have the following function <code>howMany</code> and vector <code>exclamations</code>

         ::

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

            vector<string> excl = {"what?!", "how???", "fine!", "STOP.", "yay!!!!!", "ugh...!"};

         Construct a block of code that counts how many times ".", "!", and "?" occur in <code>exclamations</code>.
         Save the counts to a vector with "." count as the first element, "!" count as the second, and "?" count as the third.

         .. code-block:: cpp

            {{group}}
            vector<char> punc = {'.', '!', '?'};
            vector<int> counts = {};
            {{endgroup}}
            {{group}}
            for (int i = 0; i < punc.size(); ++i) {
            {{endgroup}}
            {{group}}
             counts.push_back(howMany(excl, punc[i]));
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}
            {{distractor}}
            {{group}}
            vector<string> punc = {".", "!", "?"}; #distractor
            vector<int> counts = {};
            {{endgroup}}
            {{distractor}}
            {{group}}
            for (int i = 0; i < excl.size(); ++i) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            counts.push_back(howMany(excl, i)); #distractor
            {{endgroup}}
