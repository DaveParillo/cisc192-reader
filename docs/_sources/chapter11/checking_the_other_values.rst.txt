Checking the other values
-------------------------

``how_many`` only counts the occurrences of a particular value, and we
are interested in seeing how many times each value appears. We can solve
that problem with a loop:

::

     int num_values = 20;
     int upper_bound = 9;
     std::vector<int> numbers = make_vector (num_values, upper_bound);

     std::cout << "value\thow_many";

     for (int i = 0; i<=upper_bound; ++i) {
       std::cout << i << '\t' << how_many (numbers, i) << '\n';
     }

Notice that it is legal to declare a variable inside a ``for``
statement. This syntax is sometimes convenient, but you should be aware
that a variable declared inside a loop only exists inside the loop. If
you try to refer to ``i`` later, you will get a compiler error.

This code uses the loop variable as an argument to ``how_many``, in order
to check each value between 0 and 9, in order. The result is:

::

   value   how_many
   0       2
   1       1
   2       3
   3       3
   4       0
   5       2
   6       5
   7       2
   8       0
   9       2

Again, it is hard to tell if the digits are really appearing equally often. 
If we increase ``num_values`` to 100,000 we get the following:

::

   value   how_many
   0       10130
   1       10072
   2       9990
   3       9842
   4       10174
   5       9930
   6       10059
   7       9954
   8       9891
   9       9958

In each case, the number of appearances is within about 1% of the
expected value (10,000), so we conclude that the random numbers are
probably uniform.

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: checking_values_1
         :answer_a: inside of the for loop.
         :answer_b: outside of the for loop, but inside of the function it's used in.
         :answer_c: outside of the function, and everywhere else in the program.
         :correct: a
         :feedback_a: Correct!
         :feedback_b: Incorrect! The variable goes out of scope as soon as the for loop terminates!
         :feedback_c: Incorrect! The variable goes out of scope as soon as the for loop terminates!

         If you declare a variable inside a ``for`` statement, where can it exist?

   .. tab:: Q2

      .. mchoice:: checking_values_2
         :multiple_answers:
         :answer_a: the difference between actual and expected number of appearances increases
         :answer_b: the difference between actual and expected number of appearances decreases
         :answer_c: the percent by which the number of appearances differs from the expected number increases
         :answer_d: the percent by which the number of appearances differs from the expected number decreases
         :correct: a,d
         :feedback_a: Correct! The numbers go from being off by less than 5 to more than 100.
         :feedback_b: Incorrect! Take a look at the numbers again!
         :feedback_c: Incorrect! Take a look at the numbers again!
         :feedback_d: Incorrect! As we continue to increase the size of num_values, the percent by which the number of appearances differes from the expected value approaches 0.


         **Multiple Response** When we increase the size of ``num_values``, which of the following is true?

