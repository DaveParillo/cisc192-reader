Vector of random numbers
------------------------

The first step is to generate a large number of random values and store
them in a vector. By “large number,” of course, I mean 20. It’s always a
good idea to start with a manageable number, to help with debugging, and
then increase it later.

The following function takes a single argument, the size of the vector.
It allocates a new vector of ``int``\ s, and fills it with random values
between 0 and ``upper_bound``.

::

   std::vector<int> make_vector (int size, int upper_bound) {
     std::vector<int> data (size);
     std::random_device r;
     std::default_random_engine eng(r());
     for (int& value: data) {
       value = std::uniform_int_distribution<int> {0, upper_bound} (eng);
     }
     return data;
   }

The return type is ``std::vector<int>``, which means that this function
returns a vector of integers. To test this function, it is convenient to
have a function that outputs the contents of a vector.

::

   void print (const std::vector<int>& data) {
     for (const int& value: data) {
       cout << value << ' ';
     }
   }

Notice that it is legal to pass ``vector``\ s by reference. In fact it
is quite common, since it makes it unnecessary to copy the vector. Since
``print`` does not modify the vector, we declare the parameter
``const``.
We use the same technique to get values out of the vector without
copying every single one.
Avoiding these kinds of copy operations makes code run faster.
It is also less error prone.

The following code generates a vector and outputs it:

::

     int num_values = 20;
     int upper_bound = 9;
     std::vector<int> numbers = make_vector (num_values, upper_bound);
     print (numbers);

On my machine the output is

::

   1 9 9 5 9 5 5 2 8 6 2 7 1 0 5 6 2 7 5 6

which is pretty random-looking. Your results might be different.

.. activecode:: vector_of_rand_nums_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
   :nocodelens:

   Try running the active code below!
   ~~~~
   #include <iostream>
   #include <random>
   #include <vector>

   // forward declarations
   std::vector<int> make_vector (int, int);
   void print (const std::vector<int>&);

   int main() {
     int num_values = 20;
     int upper_bound = 9;
     std::vector<int> numbers = make_vector (num_values, upper_bound);
     print (numbers);
   }

   std::vector<int> make_vector (int size, int upper_bound) {
     std::vector<int> data (size);
     std::random_device r;
     std::default_random_engine eng(r());
     for (int& value: data) {
       value = std::uniform_int_distribution<int> {0, upper_bound} (eng);
     }
     return data;
   }

   void print (const std::vector<int>& data) {
     for (const int& value: data) {
       std::cout << value << ' ';
     }
   }

If these numbers are really random, we expect each digit to appear the
same number of times—twice each. In fact, the number 5 appears five
times, and the numbers 3 and 4 never appear at all.

Do these results mean the values are not really uniform? It’s hard to
tell. With so few values, the chances are slim that we would get exactly
what we expect. But as the number of values increases, the outcome
should be more predictable.

To test this theory, we’ll write some programs that count the number of
times each value appears, and then see what happens when we increase
``num_values``.

.. tabbed:: self_check

   .. tab:: Q1

      .. fillintheblank:: vector_of_rand_nums_1

          How should we declare the parameter, **vector**,
          if we don't intend to make any changes to it?

          - :([Cc]onst|CONST): Correct!
            :.*: Incorrect, Try again!

   .. tab:: Q2

      .. mchoice:: vector_of_rand_nums_2
         :answer_a: more uniform
         :answer_b: less uniform
         :answer_c: more normal
         :answer_d: less normal
         :correct: a
         :feedback_a: Correct!
         :feedback_b: Incorrect! As we store more random numbers in a vector, we see that the frequencies of each number are approximately equal.
         :feedback_c: Incorrect! The distribution of random numbers is not related to the normal distribution.
         :feedback_d: Incorrect! The distribution of random numbers is not related to the normal distribution.

         As we store more and more random numbers in a vector, we expect its contents to be __________.

   .. tab:: Q3

      .. mchoice:: vector_of_rand_nums_3
         :practice: T
         :answer_a: yes we would get a compile error
         :answer_b: no we would not because values are valid.
         :correct: a
         :feedback_a: Correct! we can't make changes to a vector we take in by constant reference
         :feedback_b: Even if the values are legal and valid we are editing a constant which is not allowed.

         Would compiling the following code lead to a compiler error?

         .. code-block:: cpp
            :linenos:

            void dostuff (const std::vector<int> & vec) {
               for (size_t i = 0; i < vec.size(); ++i) {
                  vec[i] = i;
               }
            }
