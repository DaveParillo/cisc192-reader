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
     std::size_t len = values.size();
     for (std::size_t i = 0; i < len; i++) {
       cout << values[i] << endl;
     }
   }

The active code below uses the ``push_back`` function to add 
even numbers less than or equal to 10 to the vector ``values``.

.. tb-code:: cpp
   :name: vector_functions_AC_1-support
   :hidden:


   void print_vec(std::vector<int> nums) {
      std::cout << '[';
      for (const auto& n: vec) {
          cout << n << ',';
      }
      cout << "]\n";
   }


.. tb-code:: cpp
   :name: vector_functions_AC_1
   :caption: Example vector_functions_AC_1
   :run-after: vector_functions_AC_1-support

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

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: vector_functions_1



         - [ ] 5

           Incorrect! This is the size of the vector before we ran the command.
         - [x] 6

           Correct!
         - [ ] 7

           Incorrect!
         - [ ] 8

           Incorrect! We are adding the element 3 to the end of the vector, not 3 elements!

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: vector_functions_2

         Construct the <code>make_even</code> function that loops through vec, adds 1 to any elements
         that are odd, and returns the new vector.

         .. code-block:: cpp

            {{group}}
            vector&#60;int&#62; make_even(vector&#60;int&#62; vec) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void make_even(vector&#60;int&#62; vec) {
            {{endgroup}}
            {{group}}
               for (std::size_t i = 0; i &#60; vec.size(); i++) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               for (std::size_t i = 0; i &#60; vec.size(); i++) {
            {{endgroup}}
            {{group}}
                  if (vec[i] % 2 == 1) {
            {{endgroup}}
            {{distractor}}
            {{group}}
                  if (i % 2 == 1) {
            {{endgroup}}
            {{group}}
                     vec[i] += 1;
                  }
            {{endgroup}}
            {{distractor}}
            {{group}}
                     i += 1;
                  }
            {{endgroup}}
            {{distractor}}
            {{group}}
                  else {                         #distractor
                     vec[i] -= 1;
                  }
            {{endgroup}}
            {{group}}
               return vec;
            {{endgroup}}
            {{group}}
               }
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-choice::
         :name: vector_functions_3

         t does the following code print?

         code-block:: cpp
         :linenos:

         vector<int> numbers(5);
         std::size_t size = 5;
         for (std::size_t i = 0; i < size; ++i){
            numbers[i] = i;
         }

         int end = 4;

         for (std::size_t i = 0; i < size; ++i){
            numbers[i] = numbers[end];
            end--;
         }

         for (std::size_t i = 0; i < size; ++i){
            cout << numbers[i] << "  ";
         }

         cout << endl;

         - [ ] 4 3 2 1 0

           we change the numbers in the first half of the vector before we copy them to the second half
         - [x] 4 3 2 3 4

           when <code>i</code> is 3 we copy from <code>end = 1</code> copying the values we already changed.
         - [ ] 0 1 2 3 4

           we change values in the second loop.

