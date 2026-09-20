.. _more-structures-functions-for-objects:

Functions for objects
---------------------

In the next few sections, I will demonstrate several possible interfaces
for functions that operate on objects. For some operations, you will
have a choice of several possible interfaces, so you should consider the
pros and cons of each of these:

.. index::
   pair: functions; pure functions
   single: modifier
   pair: functions; fill-in functions


pure function:
   Takes objects and/or basic types as arguments but does not modify the
   objects. The return value is either a basic type or a new object
   created inside the function.

.. index::
   single: modifier

modifier:
   Takes objects as parameters and modifies some or all of them. Often
   returns void.

.. index::
   single: fill-in function

fill-in function:
   One of the parameters is an “empty” object that gets filled in by the
   function. Technically, this is a type of modifier.


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-match::
         :name: dnd9_1

         Match the term to its definition.

         pure function
            Does not modify objects. The return values is either a basic type or a new object that was create in the function. Takes objects and/or basic types as arguments.
         modifier
            Often returns void. Modifies some or all parameters. Takes objects as parameters.
         fill-in function
            Technically a type of modifier. One of the parameters is an "empty" object that gets filled in my the function.

