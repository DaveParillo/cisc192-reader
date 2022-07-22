Vector functions
----------------

The best feature of a vector is its ability to resize.
A vector, once declared, can be resized from anywhere within the program. 
Suppose we have a situation where we input numbers from the user and 
store them in a vector till the input is ``-1``, and then display them. 
In such a case, we do not know the size of the vector beforehand.
So we need a way add new values to the end of a vector as the user inputs them.
We can use then vector function :vector:`push_back` for that purpose.

.. note::

   ``push_back`` adds a specified element to the end of the vector, ``pop_back``
   removes element from the end of a vector.

::

   #include <iostream>
   #include <vector>
   
   int main() {
     std::vector<int> values;
     int c;
     cin >> c;

     while (c != -1) {
       values.push_back(c);
       cin >> c;
     }
     size_t len = values.size();
     for (size_t i = 0; i < len; i++) {
       cout << values[i] << endl;
     }
   }

.. activecode:: vector_functions_AC_1
   :language: cpp
   :nocodelens:

   The active code below uses the ``push_back`` function to add 
   even numbers less than or equal to 10 to the vector ``values``.
   ~~~~
   #include <iostream>
   #include <vector>

   void print_vec(std::vector<int> nums);
   
   int main() {
       std::vector<int> values;
       int i = 0;

       while (i <= 10) {
           values.push_back(i);
           i += 2;
       }
       print_vec(values);
   }

   ====

   void print_vec(std::vector<int> nums) {
      std::cout << '[';
      for (const auto& n: vec) {
          cout << n << ',';
      }
      cout << "]\n";
   }

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: vector_functions_1
         :answer_a: 5
         :answer_b: 6
         :answer_c: 7
         :answer_d: 8
         :correct: b
         :feedback_a: Incorrect! This is the size of the vector before we ran the command.
         :feedback_b: Correct!
         :feedback_c: Incorrect!
         :feedback_d: Incorrect! We are adding the element 3 to the end of the vector, not 3 elements!

         Let **nums** be the vector { 0, 1, 2, 3, 4 }. If we run the command ``nums.push_back(3)``, what will be returned by ``nums.size()``?

   .. tab:: Q2

      .. parsonsprob:: vector_functions_2
         :numbered: left
         :adaptive:

         Construct the <code>make_even</code> function that loops through vec, adds 1 to any elements
         that are odd, and returns the new vector.
         -----
         vector&#60;int&#62; make_even(vector&#60;int&#62; vec) {
         =====
         void make_even(vector&#60;int&#62; vec) {                         #paired
         =====
            for (size_t i = 0; i &#60; vec.size(); i++) {
         =====
            for (int i = 0; i &#60; vec.size(); i++) {                         #paired
         =====
               if (vec[i] % 2 == 1) {
         =====
               if (i % 2 == 1) {                         #paired
         =====
                  vec[i] += 1;
               }
         =====
                  i += 1;                         #paired
               }
         =====
               else {                         #distractor
                  vec[i] -= 1;
               }
         =====
            return vec;
         =====
            }
         }

   .. tab:: Q3

      .. mchoice:: vector_functions_3
         :practice: T
         :answer_a: 4 3 2 1 0
         :answer_b: 4 3 2 3 4
         :answer_c: 0 1 2 3 4
         :correct: b
         :feedback_a: we change the numbers in the first half of the vector before we copy them to the second half
         :feedback_b: when <code>i</code> is 3 we copy from <code>end = 1</code> copying the values we already changed.
         :feedback_c: we change values in the second loop.


         What does the following code print?

         .. code-block:: cpp
            :linenos:

            vector<int> numbers(5);
            int size = 5;
            for (int i = 0; i < size; ++i){
               numbers[i] = i;
            }

            int end = 4;

            for (int i = 0; i < size; ++i){
               numbers[i] = numbers[end];
               end--;
            }
            
            for (int i = 0; i < size; ++i){
               cout << numbers[i] << "  ";
            }

            cout << endl;

