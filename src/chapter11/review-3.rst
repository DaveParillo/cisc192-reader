.. _random-numbers-activecode-exercises:

Activecode Exercises
--------------------

Answer the following **Activecode** questions to assess what you have learned in this chapter.


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1


      Write the function ``random_nums`` that takes two integers: 
      ``num`` which is the number of random numbers to generate,
      and ``max``,
      which is the maximum value of random number you wish to generate.
      Your function should return a vector of ``num`` integers that are
      between 1 and ``max``, inclusive.

      .. tb-code:: cpp
         :name: vectors_a8
         :caption: Example vectors_a8
         :compileargs: ['-Werror']

         #include <iostream>
         #include <random>
         #include <vector>



