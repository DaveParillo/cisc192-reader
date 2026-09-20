Invariants
----------

There are several conditions we expect to be true for a proper
``complex_number`` object. For example, if the ``cartesian`` flag is set then
we expect ``real`` and ``imag`` to contain valid data. Similarly, if
``polar`` is set, we expect ``mag`` and ``theta`` to be valid. Finally,
if both flags are set then we expect the other four variables to be
consistent; that is, they should be specifying the same point in two
different formats.

.. index::
   single: invariant

These kinds of conditions are called ``invariants``, for the obvious
reason that they do not vary—they are always supposed to be true. One of
the ways to write good quality code that contains few bugs is to figure
out what invariants are appropriate for your classes, and write code
that makes it impossible to violate them.

One of the primary things that data encapsulation is good for is helping
to enforce invariants. The first step is to prevent unrestricted access
to the instance variables by making them private. Then the only way to
modify the object is through accessor functions and modifiers. If we
examine all the accessors and modifiers, and we can show that every one
of them maintains the invariants, then we can prove that it is
impossible for an invariant to be violated.

Looking at the ``complex_number`` class, we can list the functions that make
assignments to one or more instance variables:

::

   the second constructor
   calculate_cartesian
   calculate_polar
   set_cartesian
   set_polar

In each case, it is straightforward to show that the function maintains
each of the invariants I listed. We have to be a little careful, though.
Notice that I said “maintain” the invariant. What that means is “If the
invariant is true when the function is called, it will still be true
when the function is complete.”

That definition allows two loopholes. First, there may be some point in
the middle of the function when the invariant is not true. That’s ok,
and in some cases unavoidable. As long as the invariant is restored by
the end of the function, all is well.

The other loophole is that we only have to maintain the invariant if it
was true at the beginning of the function. Otherwise, all bets are off.
If the invariant was violated somewhere else in the program, usually the
best we can do is detect the error, output an error message, and exit.

.. tb-choice::
   :name: question14_8_1

   How does data encapsulation help us enforce invariants? 

   - [x] It prevents unrestricted access to the instance variables by making them private.

     Correct! Users must instead use accessor functions to access them.
   - [ ] It allows users to directly modify private member variables.

     Incorrect! Try again.
   - [ ] It makes it so that private data members can never be modified by any function.

     Incorrect! Try again.
   - [ ] It eliminates the need for invariants.

     Incorrect! Try again.

.. tb-choice::
   :name: question14_8_2

   An invariant can be false in the middle of a function as long as it is true at the start and end. 

   - [x] True

     Correct! The invariant just has to be true when the function is complete, given that it's true at the start.
   - [ ] False

     Incorrect! Try again.

.. tb-choice::
   :name: question14_8_3

   If an invariant is false at the start of the function, the function must fix it to be true by the end. 

   - [ ] True

     Incorrect! Try again.
   - [x] False

     Correct! We only have to maintain the invariant if it was true at the start. If it's false, all bets are off.

.. tb-choice::
   :name: question14_8_4

   If we create a ``Triangle`` class, which of the following are invariants we must maintain?

   - [x] The interior angles of a ``Triangle`` object must add up to 180 degrees.

     Correct!
   - [x] The sum of two sides of a ``Triangle`` object must be greater than the third.

     Correct!
   - [ ] All angles of a ``Triangle`` object must be 60 degrees.

     Incorrect! An equilateral triangle is only one possible kind of triangle.
   - [ ] The greatest angle in a ``Triangle`` object must be less than 90 degrees.

     Incorrect! We are allowed to have obtuse triangles.

