Leap of faith
-------------
.. index::
   single: leap of faith

Following the flow of execution is one way to read programs, but as you
saw in the previous section, it can quickly become labyrinthine. An
alternative is what I call the "leap of faith." 

.. note:: 
   When you come to a function call, instead of following the 
   flow of execution, you *assume* that the function works correctly
   and returns the appropriate value.  This is the **leap of faith**.

In fact, you are already practicing this leap of faith when you use
built-in functions. When you call :cmath:`cos` or :cmath:`exp`, 
you don't examine the
implementations of those functions. You just assume that they work,
because the people who wrote the built-in libraries were good
programmers.

Well, the same is true when you call one of your own functions. For
example, in Section \ `8 <#bool>`__ we wrote a function called
``is_digit`` that determines whether a number is between 0 and 9. Once
we have convinced ourselves that this function is correct—by testing and
examination of the code—we can use the function without ever looking at
the code again.

The same is true of recursive programs. When you get to the recursive
call, instead of following the flow of execution, you should *assume*
that the recursive call works (yields the correct result), and then ask
yourself, "Assuming that I can find the factorial of :math:`n-1`, can I
compute the factorial of :math:`n`?" In this case, it is clear that you
can, by multiplying by :math:`n`.

Of course, it is a bit strange to assume that the function works
correctly when you have not even finished writing it, but that's why
it's called a leap of faith!

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: recursive_leap_1
         :answer_a: Since you can find the factorial of the first 3 numbers in a list, you must also be able to find the factorial of the first 2.
         :answer_b: You assume that the log function works, without examining the implementation. 
         :answer_c: Since you can take the sum of the first 7 numbers in a list, you assume that you can also take the sum of the first 8.
         :answer_d: You write a function and assume that it will work.
         :correct: c
         :feedback_a: There is no leap of faith here.  In fact, it's quite flip-flopped.
         :feedback_b: This is a leap of faith, but it is not recursive.
         :feedback_c: Recursive leaps of faith always assume that the recursive call will work.
         :feedback_d: This is a leap of faith, but it is not recursive.

         Which of the following is an example of the recursive leap of faith?
