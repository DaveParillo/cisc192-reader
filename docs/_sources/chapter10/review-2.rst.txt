Mixed-Up Code Exercises
-----------------------

Answer the following **Mixed-Up Code** questions to assess what you have learned in this chapter.

.. tabbed:: self_check

   .. tab:: Q1

      .. parsonsprob:: vectors_p1
         :numbered: left
         :adaptive:
         :noindent:

         Construct a block of code that changes the first element of <code>vec</code> to a 6,
         multiplies the third element of <code>vec</code> by 2, and increments the last element 
         of <code>vec</code> by 1 (in that order).  This should work no matter what <code>vec</code> is.
         -----
         vec[0] = 6;
         =====
         vec[2] = vec[2] * 2;
         =====
         last = vec.size() - 1;
         vec[last]++;
         =====
         vec[1] = 6; #distractor
         =====
         vec[0] == 6; #distractor
         =====
         vec[3] = vec[3] * 2; #distractor
         =====
         last = vec.size(); #distractor
         vec[last]++;



      .. parsonsprob:: vectors_p2
         :numbered: left
         :adaptive:
         :noindent:

         Construct a block of code that creates a vector called <code>digs</code> whose elements are
         7, 8, 7, 8.  Then access elements to change the <code>digs</code> to contain the elements
         7, 4, 7, 4.  <b>Important</b>: Change the <code>8</code>'s to <code>4</code>'s in order of 
         increasing index.

         -----
         vector<int> digs = {7, 8, 7, 8};
         =====
         digs[1] = 4;
         =====
         digs.pop_back();
         =====
         digs.push_back(4);
         =====
         vector digs = {7, 8, 7, 8}; #distractor
         =====
         vector<int> digs = [7, 8, 7, 8]; #distractor
         =====
         digs[2] = 4; #distractor
         =====
         digs.pop_back(4); #distractor


      .. parsonsprob:: vectors_p3
         :numbered: left
         :adaptive:
         :noindent:

         Construct a block of code that creates a vector called <code>nums</code> whose elements are five <code>1</code>'s.
         Then make a copy of this vector called <code>digits</code>, and use vector operations to change
         digits to <code>{1, 2, 3}</code>.

         -----
         vector<int> nums (5, 1);
         =====
         vector<int> digits = nums;
         =====
         digits.pop_back();
         digits.pop_back();
         =====
         digits[1]++;
         digits[2] = digits[2] * 3;
         =====
         vector nums = {1, 1, 1, 1, 1}; #distractor
         =====
         vector<int> nums = digits; #distractor
         =====
         digits.push_back(); #distractor
         digits.push_back();
         =====
         digits[2]++; #distractor
         digits[3] = digits[3] * 3;


      .. parsonsprob:: vectors_p4
         :numbered: left
         :adaptive:
         :noindent:

         Construct a block of code that loops over a vector called <code>numbers</code>
         and transforms the vector so each element is doubled.
         -----
         vector<int> numbers = {1, 2, 3, 4, 5};
         =====
         for (size_t i = 0; i < numbers.size(); i++) {
         =====
          numbers[i] = numbers[i] * 2;
         =====
         }
         =====
         vector numbers = {1, 2, 3, 4, 5}; #distractor
         =====
         for (size_t i = 1; i <= numbers.size(); ++i) { #distractor
         =====
         for (int i = 0; i < numbers.size(); i++) { #distractor
         =====
         numbers[i] * 2; #distractor


      .. parsonsprob:: vectors_p5
         :numbered: left
         :adaptive:
         :noindent:

         Suppose you have the vector

         <pre> <code>

            vector<string> words = {"car", "cat", "switch", "princess"};

         </code> </pre>

         Construct a block of code that transforms the vector to

         <pre> <code>

            vector<string> words = {"cAr", "cAt", "switch", "mArio"}

         </code> </pre>
         -----
         words.pop_back();
         =====
         words.push_back("mario");
         =====
         for (size_t i = 0; i < words.size(); ++i) {
         =====
          for (size_t c = 0; c < words[i].size(); ++c) {
         =====
           if (words[i][c] == 'a') {
         =====
               words[i][c] = 'A';
         =====
           }
          }
         }
         =====
         words.pop_back("mario"); #distractor
         =====
         for (int i = 0; i < words.size(); ++i) { #distractor
         =====
         for (int c = 0; c < words[i].size(); ++c) { #distractor
         =====
         words[i][c] == 'A'; #distractor


      .. parsonsprob:: vectors_p7
         :numbered: left
         :adaptive:
         :noindent:
         
         Suppose <code>album</code> has already been defined as

         <pre> <code>

            vector<string> album = {"imagine", "needy", "NASA", "bloodline", "fake smile", "bad idea", "make up", "ghostin", "in my head", "7 rings", "thank u, next", "break up with your girlfriend, i'm bored"}

         </code> </pre>

         Construct a block of code that counts how many songs in <code>album</code> start with b.
         -----
         count = 0
         =====
         for (size_t i = 0; i < album.size(); i++) {
         =====
          if (album[i][0] == 'b') {
         =====
           ++count;
         =====
          }
         }
         =====
         for (int i = 0; i < album.size(); i++) { #distractor
         =====
         if (album[i] == 'b') { #distractor
         =====
         if (album[i][1] == 'b') { #distractor
         =====
         count++ #distractor


      .. parsonsprob:: vectors_p8
         :numbered: left
         :adaptive:
         :noindent:
         
         Suppose you have the following two vectors to describe the weekly forecast

         <pre> <code>

            vector<double> temps = {82.0, 76.8, 74.3, 58.8, 79.2, 73.4, 80.1}
            vector<double> precip = {0.00, 0.30, 0.60, 0.90, 0.10, 0.20, 0.80}

         </code> </pre>

         Your family will go to the beach if the temperature at least 75 degrees and the chance
         of precipitation is less than 50%.  Construct a block of code that counts how many days
         your family can hit the beach on your vacation.
         -----
         count = 0;
         =====
         for (int i = 0; i < 7; ++i) {
         =====
          if (temps[i] >= 75.0 && precip[i] < 0.50) {
         =====
           ++count;
         =====
          }
         }
         =====
         for (size_t i = 1; i <= 7; ++i) { #distractor
         =====
         if (temps[i] > 75.0 && precip[i] <= 0.50) { #distractor
         =====
         count++ #distractor


      .. parsonsprob:: vectors_p9
         :numbered: left
         :adaptive:
         :noindent:
         
         Suppose you have the following vector <code>nouns</code>

         <pre> <code>

            vector<string> nouns = {"cereal", "Cocoa Puffs", "Mario", "luigi", "Aerosmith"};

         </code> </pre>

         Construct a block of code that creates a vector of the <b>proper</b> nouns in <code>nouns</code>.
         Use the <code>isupper</code> function to check if a letter is uppercase.
         -----
         vector<string> proper = {};
         =====
         for (size_t i = 0; i < nouns.size(); ++i) {
         =====
          if (isupper(nouns[i][0])) {
         =====
           proper.push_back(nouns[i]);
         =====
          }
         }
         =====
         if (isupper(nouns[i][1])) { #distractor
         =====
         proper.push_back(nouns[i][0]); #distractor
         =====
         proper.pop_back(nouns[i]); #distractor
         =====
         vector proper = {}; #distractor


      .. parsonsprob:: vectors_p10
         :numbered: left
         :adaptive:
         :noindent:
         
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
         -----
         vector<char> punc = {'.', '!', '?'};
         vector<int> counts = {};
         =====
         for (int i = 0; i < punc.size(); ++i) {
         =====
          counts.push_back(howMany(excl, punc[i]));
         =====
         }
         =====
         vector<string> punc = {".", "!", "?"}; #distractor
         vector<int> counts = {};
         =====
         for (int i = 0; i < excl.size(); ++i) { #distractor
         =====
         counts.push_back(howMany(excl, i)); #distractor
