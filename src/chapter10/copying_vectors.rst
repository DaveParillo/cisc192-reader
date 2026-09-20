Copying vectors
---------------

There is one more constructor for ``vector``\ s, which is called a copy
constructor because it takes one ``vector`` as an argument and creates a
new vector that is the same size, with the same elements.

::

     vector<int> copy (count);

Although this syntax is legal, it is almost never used for ``vector``\ s
because there is a better alternative:

::

   vector<int> copy = count;

The ``=`` operator works on ``vector``\ s in pretty much the way you
would expect.

Take a look at the active code below, which uses the copy constructor.

.. tb-code:: cpp
   :name: copying_vectors_AC_1-support
   :hidden:
   :compileargs: ['-Wall', '-std=c++11']


   void print_vec(std::vector<int> vec) {
      cout << '[';
      for (const auto& n: vec) {
          cout << n << ',';
      }
      cout << "]\n";
   }




.. tb-code:: cpp
   :name: copying_vectors_AC_1
   :caption: Example copying_vectors_AC_1
   :run-after: copying_vectors_AC_1-support
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>
   #include <vector>
   using std::cout;

   void print_vec(std::vector<int> vec);

   int main() {
       using std::vector;
       vector<int> count = {1,2,3,4};
       cout << "count = "; print_vec(count);

       vector<int> copy_1 (count);
       vector<int> copy_2 = count;

       cout << "copy_1 = "; print_vec(copy_1);
       cout << "copy_2 = "; print_vec(copy_2);
       cout << "We just made two copies of count.\n"
            << "As you can see, both methods work the same!\n";
   }

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: copying_vectors_1

         **Multiple Response** How would you make a copy of ``vector<double> decimals`` called **nums**?

         - [x] ``vector<double> nums = decimals;``

           +   This is one way to make a copy.

         - [ ] ``vector<double> decimals = nums;``

           -   This makes a copy of nums called decimals.

         - [x] ``vector<double> nums (decimals);``

           +   This is one way to make a copy.

         - [ ] ``vector<double> decimals (nums);``

           -   This makes a copy of nums called decimals.


   .. tb-tab:: Q2

      .. tb-blank::
         :name: copying_vectors_2

         What is the name of the function that takes a vector as an argument, and 
         creates a new vector of the same size and with the same elements?

         {{blank}}

         .. tb-answer::
            :match: copy constructor
            :feedback: Correct!
            :incorrect: incorrect! You can find the answer by re-reading the text above.

