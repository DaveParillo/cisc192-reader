Counting
--------

.. index::
   single: bottom-up design

A good approach to problems like this is to think of simple functions
that are easy to write, and that might turn out to be useful. Then you
can combine them into a solution. This approach is sometimes called
**bottom-up design**. Of course, it is not easy to know ahead of time
which functions are likely to be useful, but as you gain experience you
will have a better idea.

Also, it is not always obvious what sort of things are easy to write,
but a good approach is to look for subproblems that fit a pattern you
have seen before.

Back in Section `[loopcount] <#loopcount>`__ we looked at a loop that
traversed a string and counted the number of times a given letter
appeared. You can think of this program as an example of a pattern
called “traverse and count.” The elements of this pattern are:

-  A set or container that can be traversed, like a string or a vector.

-  A test that you can apply to each element in the container.

-  A counter that keeps track of how many elements pass the test.

In this case, I have a function in mind called ``how_many`` that counts
the number of elements in a vector that equal a given value. The
parameters are the vector and the integer value we are looking for. The
return value is the number of times the value appears.

::

   std::size_t how_many (const std::vector<int>& data, int value) {
     std::size_t count = 0;
     for (const int& number: data) {
       if (number == value) {
         count++;
       }
     }
     return count;
   }

Take a look at the active code below which uses the ``how_many`` function. Run the
code to see how many times the target appears in the vector! Feel free to 
modify the code and experiment around.

.. tb-code:: cpp
   :name: counting_AC_1-support
   :hidden:
   :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']


   std::size_t how_many (const std::vector<int>& data, int value) {
     std::size_t count = 0;
     for (const int& number: data) {
       if (number == value) {
         count++;
       }
     }
     return count;
   }

   std::vector<int> make_vector (std::size_t size, int upper_bound) {
     std::vector<int> data (size);
     std::random_device r;
     std::default_random_engine eng(r());
     for (std::size_t i = 0; i < data.size(); ++i) {
       data[i] = std::uniform_int_distribution<int> {0, upper_bound} (eng);
     }
     return data;
   }

   void print (const std::vector<int>& data) {
     for (const int& value: data) {
       cout << value << ' ';
     }
   }


.. tb-code:: cpp
   :name: counting_AC_1
   :caption: Example counting_AC_1
   :run-after: counting_AC_1-support
   :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']

   #include <cstddef>
   #include <iostream>
   #include <random>
   #include <vector>

   // forward declarations
   std::size_t how_many (const vector<int>&, int);
   std::vector<int> make_vector (std::size_t, int);
   void print (const std::vector<int>&);

   int main() {
     std::size_t num_values = 20;
     int upper_bound = 9;
     int target = 6;
     std::vector<int> numbers = make_vector (num_values, upper_bound);
     print (numbers);
     cout << "\nThe number " << target << " appears " 
          << how_many(numbers,target) << " times in our vector!";
   }

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: counting_1

         Which of the following is the best definition of bottom-up design?

         - [x] a method of programming where you write simple "helper" functions that are later incorporated into larger functions

           Correct! Bottom-up design starts with a lot of small functions and assembles them into a few larger ones that accomplish a task.
         - [ ] a method of programming in which you tackle the largest functions first, and save the simple functions for later

           Incorrect! This is describing top-down design.
         - [ ] a method of programming where you break the task down into smaller and smaller components until it cannot be simplified further

           Incorrect! This is describing top-down design.
         - [ ] a method of programming where you use the minimum number of functions to accomplish the task

           Incorrect! Bottom-up design uses many simple functions rather than a few complex ones, so it is not minimizing the number of functions being used.

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: counting_2

         Construct a block of code that counts how many numbers are between lowerbound and upperbound inclusive.

         .. code-block:: cpp

            {{group}}
            std::size_t just_right (const vector<int>& vec, int lowerbound, int upperbound) {
            {{endgroup}}
            {{group}}
               std::size_t count = 0;
            {{endgroup}}
            {{group}}
               for (std::size_t i = 0; i &#60; vec.size(); i++) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               for (int i = 0; i &#60; upperbound; i++)
            {{endgroup}}
            {{group}}
                  if (vec[i] i &#62;= lowerbound && vec[i] i &#60;= upperbound) {
                count++;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  if (vec[i] i &#62; lowerbound && vec[i] i &#60; upperbound) {
                     count++;
            {{endgroup}}
            {{group}}
                  }
               }
               return count;
            }
            {{endgroup}}

