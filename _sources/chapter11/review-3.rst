Activecode Exercises
--------------------

Answer the following **Activecode** questions to assess what you have learned in this chapter.


.. tabbed:: self_check

   .. tab:: Q1


      .. activecode::  vectors_a8
         :language: cpp
         :compileargs: ['-Wall', '-Wextra', '-Werror' '-std=c++11']
         :nocodelens:

         Write the function ``random_nums`` that takes two integers: 
         ``num`` which is the number of random numbers to generate,
         and ``max``,
         which is the maximum value of random number you wish to generate.
         Your function should return a vector of ``num`` integers that are
         between 1 and ``max``, inclusive.
         ~~~~
         #include <iostream>
         #include <random>
         #include <vector>


         
