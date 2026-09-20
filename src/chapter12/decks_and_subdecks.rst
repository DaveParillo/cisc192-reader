Decks and subdecks
------------------

Looking at the interface to ``find_bisect``

::

   std::ptrdiff_t find_bisect (const playing_card& card, const std::vector<playing_card>& deck,
           std::ptrdiff_t low, std::ptrdiff_t high) {

it might make sense to treat three of the parameters, ``deck``, ``low``
and ``high``, as a single parameter that specifies a *subdeck*.

.. index::
   single: abstract
   single: abstraction
   single: abstract parameter

This kind of thing is quite common, and I sometimes think of it as an
**abstract parameter**. What I mean by **abstract,** is something that is
not literally part of the program text, but which describes the function
of the program at a higher level.

For example, when you call a function and pass a vector and the bounds
``low`` and ``high``, there is nothing that prevents the called function
from accessing parts of the vector that are out of bounds. So you are
not literally sending a subset of the deck; you are really sending the
whole deck. But as long as the recipient plays by the rules, it makes
sense to think of it, abstractly, as a subdeck.

A container can be empty: its size is zero. An object can also represent
an absence of data through its interface. Neither meaning implies that
ordinary local variables automatically receive usable values. Initialize
data members and variables before reading them, as discussed in
:doc:`../chapter8/operations_on_structures`.

This kind of thinking, in which a program comes to take on meaning
beyond what is literally encoded, is a very important part of thinking
like a computer scientist. Sometimes, the word “abstract” gets used so
often and in so many contexts that it is hard to interpret.
Nevertheless, abstraction is a central idea in computer science (as well
as many other fields).

A more general definition of “abstraction” is “The process of modeling a
complex system with a simplified description in order to suppress
unnecessary details while capturing relevant behavior.”

.. tb-choice::
   :name: decks_and_subdecks_1

   Which is false about the ``findBisect()`` funtion?

   - [ ] It uses binary search to locate the card in the deck.

     This is true. Binary search is very efficient.
   - [ ] If the program user plays by the rules, we can think of deck, low, and high abstractly as a subdeck.

     This is true. If the user doesn't follow the rules, we might be in trouble.
   - [x] It can only access the part of the deck that is between the bounds high and low.

     This is false! findBisect() can access the entire deck, even when you pass high and low parameters.
   - [ ] There is no such thing as an empty object.

     This is true.  When you create an object, it is given default values.

.. tb-blank::
   :name: c192_decks_and_subdecks_2

   When a programmer hides all unnecessary details from the user to reduce complexity and increase efficiency, this is called __________.

   {{blank}}

   .. tb-answer::
      :match: [Aa][Bb][Ss][Tt][Rr][Aa][Cc][Tt][Ii][Oo][Nn]
      :feedback: Correct!
      :match: x

