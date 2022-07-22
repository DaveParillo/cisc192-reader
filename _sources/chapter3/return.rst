Functions with Results
----------------------

You might have noticed by now that some of the functions we are using,
like the math functions, yield results. Other functions, like ``new_line``,
perform an action but don’t return a value. That raises some questions:

-  What happens if you call a function and you don’t do anything with
   the result (i.e. you don’t assign it to a variable or use it as part
   of a larger expression)?

-  What happens if you use a function without a result as part of an
   expression, like ``new_line() + 7``?

-  Can we write functions that yield results, or are we stuck with
   things like new_line and print_twice?

The answer to the third question is “yes, you can write functions that
return values,” and we’ll do it next chapter. I will leave it
up to you to answer the other two questions by trying them out. 

.. note::
   Any time you have a question about what is legal or illegal in C++, a 
   good way to find out is to ask the compiler.  It will let you answer
   your question by throwing an error... or not!
