Vector size
-----------

There are a few functions you can invoke on an ``vector``. One of them
is very useful, though: ``size``. Not surprisingly, it returns the
size of the vector (the number of elements).

It is a good idea to use this value as the upper bound of a loop, rather
than a constant. That way, if the size of the vector changes, you won’t
have to go through the program changing all the loops; they will work
correctly for any size vector.

::

     for (size_t i = 0; i < count.size(); ++i) {
       cout << count[i] << endl;
     }

.. note::

   On some machines, comparing an ``int`` to the output from ``size`` will generate 
   a type error.  This is because the size function returns an unsigned integer type. 
   To keep the variable type consistent, you should use ``size_t`` rather than ``int``
   for the type of iterator ``i``.

The last time the body of the loop gets executed, the value of ``i`` is
``count.size() - 1``, which is the index of the last element. When ``i``
is equal to ``count.size()``, the condition fails and the body is not
executed, which is a good thing, since it would cause a run-time error.
One thing that we should notice here is that the size() function is
called every time the loop is executed. Calling a function again and
again reduces execution speed, so it would be better to store the size
in some variable by calling the ``size`` function before the loop
begins, and use this variable to check for the last element. 

.. note::

   Starting in C++20, the size function is a :lang:`constexpr`.
   The constexpr instructs the compiler to evaluate and expression
   (in this case the ``size`` function) at compile time.

.. activecode:: vector_size_AC_1
   :language: cpp
   :nocodelens:

   Try running the active code below!
   ~~~~
   #include <iostream>
   #include <vector>

   int main() {
       std::vector<int> count = {1,2,3,4};
       for (size_t i = 0; i < count.size(); i++) {
           std::cout << count[i] << std::endl;
       }
   }

.. tabbed:: self_check

   .. tab:: Q1

      .. fillintheblank:: vector_size_1

          Let **nums** be the vector { 0, 1, 2, 3, 4 }. What is the variable type *of* ``nums.size()``?

          - :([Ss]ize_t|SIZE_T): Correct!
            :([Ii]nt|INT): Incorrect! Remember, the size function returns an unsigned integer type.
            :.*: Incorrect, Try again!

   .. tab:: Q2

      .. fillintheblank:: vector_size_2

          Let **nums** be the vector { 0, 1, 2, 3, 4 }. What is the value *of* ``nums.size()``?

          - :5: Correct!
            :.*: Incorrect, Try again!

   .. tab:: Q3

      .. mchoice:: vector_size_3
         :answer_a: 5
         :answer_b: 4
         :answer_c: 3
         :answer_d: none of the above due to runtime error
         :correct: d
         :feedback_a: Incorrect! This is what gets returned by nums.size()
         :feedback_b: Incorrect! This is the element before nums[nums.size()]
         :feedback_c: Incorrect!
         :feedback_d: Correct! This would be indexing out of bounds and would cause a runtime error.

         Let **nums** be the vector { 0, 1, 2, 3, 4 }. What is the value *at* ``nums[nums.size()]``?
