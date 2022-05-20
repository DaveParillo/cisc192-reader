``const`` parameters
--------------------

You might have noticed that the parameters for ``after`` and ``addTime``
are being passed by reference. Since these are pure functions, they do
not modify the parameters they receive, so I could just as well have
passed them by value.

The advantage of passing by value is that the calling function and the
callee are appropriately encapsulated—it is not possible for a change in
one to affect the other, except by affecting the return value.

On the other hand, passing by reference usually is more efficient,
because it avoids copying the argument. Furthermore, there is a nice
feature in C++, called ``const``, that can make reference parameters
just as safe as value parameters.


.. index::
   single: constant reference
   single: constant reference parameter

If you are writing a function and you do not intend to modify a
parameter, you can declare that it is a **constant reference
parameter**. The syntax looks like this:

::

   void printTime (const Time& time) ...
   Time addTime (const Time& t1, const Time& t2) ...

I've included only the first line of the functions.
If you tell the compiler that you don't intend to change a parameter,
it can help remind you.
If you try to change one, you should get a compiler error, 
or at least a warning.

.. dragndrop:: const_parameters_1
    :feedback: Try again.
    :match_1: passing by value|||the calling function and the callee are appropriately encapsulated—it is not possible for a change in one to affect the other, except by affecting the return value.
    :match_2: passing by reference|||more efficient, because it avoids copying the argument

    Match the action to a benefit of its use.

.. mchoice:: const_parameters_2
   :answer_a: Makes reference parameters just as safe as value parameters.
   :answer_b: Can be used when you intend to modify a parameter.
   :answer_c: The syntax can look like this: void printTime (const Time& time)...
   :correct: b
   :feedback_a: This is true.
   :feedback_b: It is used when you are writing a function and you do not intend to modify a parameter.
   :feedback_c: This is true

   Which statement does NOT describe the ``const`` as a parameter feature in C++?
