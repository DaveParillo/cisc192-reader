.. _random-numbers-a-single-pass-solution:

A single-pass solution
----------------------

Although this code works, it is not as efficient as it could be. Every
time it calls ``how_many``, it traverses the entire vector. In this
example we have to traverse the vector ten times!

It would be better to make a single pass through the vector. For each
value in the vector we could find the corresponding counter and
increment it. In other words, we can use the value from the vector as an
index into the histogram. Here’s what that looks like:

::

     std::vector<std::size_t> histogram (static_cast<std::size_t>(upper_bound) + 1, 0);

     for (const int& value: numbers) {
       ++histogram[static_cast<std::size_t>(value)];
     }

The first line initializes the elements of the histogram to zeroes. That
way, when we use the increment operator (``++``) inside the loop, we
know we are starting from zero.
Not initializing our data to 0 is another form of undefined behavior and
a common error.

The loop assumes every value is between zero and ``upper_bound`` inclusive.
Check that condition before indexing when the values come from untrusted input.
The loop has the same assumption as before:
the index position of the histogram vector is the value in the
numbers vector.

.. admonition:: Try this!

   Encapsulate this code in a function called ``histogram``
   that takes a vector and the range of values in the vector (in this case
   0 through 9), and that returns a histogram of the values in the vector.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: single_pass_solution_1

         What happens if you don't initialize a counter?

         - [ ] Your code runs without a problem because counters are automatically initialized to zero.

           Incorrect! Variables are not automatically initialized.
         - [x] Your code might run, but it probably won't produce the output you desire.

           Correct! C++ might assign unused memory to the uninitialized variable, which will allow the code to run, but counts may be off.
         - [x] You might get an error for using an uninitialized variable.

           Correct! Depening on your compiler, you might be lucky enough to get an error message.
         - [ ] Your program will crash.

           Incorrect! You might get a compile error, but your program will not crash.

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: single_pass_solution_2

         Construct a function called histogram that takes a vector and the range of values in the vector, and that returns a histogram of values in the vector.

         .. code-block:: cpp

            {{group}}
            vector&#60;std::size_t&#62; histogram(const vector&#60;int&#62;& vec, std::size_t range) {
            {{endgroup}}
            {{group}}
               vector&#60;std::size_t&#62; histogram (range, 0);
            {{endgroup}}
            {{distractor}}
            {{group}}
               vector&#60;std::size_t&#62; histogram (range);
            {{endgroup}}
            {{group}}
               for (std::size_t i = 0; i &#60; vec.size(); i++) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               for (int i = 0; i &#60; range; i++) {
            {{endgroup}}
            {{group}}
                  std::size_t index = static_cast<std::size_t>(vec[i]);
            {{endgroup}}
            {{distractor}}
            {{group}}
                  std::size_t index = i;
            {{endgroup}}
            {{group}}
                  histogram[index]++;
            {{endgroup}}
            {{group}}
               }
               return histogram;
            }
            {{endgroup}}

