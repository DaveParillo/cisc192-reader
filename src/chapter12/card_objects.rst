``playing_card`` objects
------------------------

If you are not familiar with common playing cards, now would be a good
time to get a deck, or else this chapter might not make much sense.
There are 52 cards in a deck, each of which belongs to one of four suits
and one of 13 ranks. The suits are Spades, Hearts, Diamonds and Clubs
(in descending order in Bridge). The ranks are Ace, 2, 3, 4, 5, 6, 7, 8,
9, 10, Jack, Queen and King. Depending on what game you are playing, the
rank of the Ace may be higher than King or lower than 2.

If we want to define a new object to represent a playing card, it is
pretty obvious what the instance variables should be: ``rank`` and
``suit``. It is not as obvious what type the instance variables should
be. One possibility is ``string``\ s, containing things like
``"Spade"`` for suits and ``"Queen"`` for ranks. One problem with this
implementation is that it would not be easy to compare cards to see
which had higher rank or suit.

.. index::
   single: encode

An alternative is to use integers to **encode** the ranks and suits. By
“encode,” I do not mean what some people think, which is to encrypt, or
translate into a secret code. What a computer scientist means by
“encode” is something like “define a mapping between a sequence of
numbers and the things I want to represent.” For example,

======== =============== =
Spades   :math:`\mapsto` 3
Hearts   :math:`\mapsto` 2
Diamonds :math:`\mapsto` 1
Clubs    :math:`\mapsto` 0
======== =============== =

The symbol :math:`\mapsto` is mathematical notation for “maps to.” The
obvious feature of this mapping is that the suits map to integers in
order, so we can compare suits by comparing integers. The mapping for
ranks is fairly obvious; each of the numerical ranks maps to the
corresponding integer, and for face cards:

===== =============== ==
Jack  :math:`\mapsto` 11
Queen :math:`\mapsto` 12
King  :math:`\mapsto` 13
===== =============== ==

The reason I am using mathematical notation for these mappings is that
they are not part of the C++ program. They are part of the program
design, but they never appear explicitly in the code. The class
definition for the ``playing_card`` type looks like this:

::

   struct playing_card {
     int suit, rank;

     playing_card ();
     playing_card (int s, int r);
   };

   playing_card::playing_card () {
     suit = 0;  rank = 1;
   }

   playing_card::playing_card (int s, int r) {
     suit = s;  rank = r;
   }

There are two constructors for ``playing_card``\ s. You can tell that they are
constructors because they have no return type and their name is the same
as the name of the structure. The first constructor takes no arguments
and initializes the object to the Ace of Clubs, a valid default card.

The second constructor is more useful. It takes two parameters, the suit
and rank of the card.

A constructor initializes an object as it is created. The declarations inside
the structure name the constructors; ``playing_card::`` on each definition
identifies the structure they belong to. Other functions declared inside a
structure are called *member functions* and are called on an object with ``.``.
A trailing ``const`` on a member function promises that it will not modify
that object's ordinary data members.

Constructor member initializer lists initialize members directly. For example,
the two constructors above can instead be written inside the structure as::

   playing_card() : suit{0}, rank{1} {}
   playing_card(int s, int r) : suit{s}, rank{r} {}

The empty braces are the constructor body; the expressions after the colon
initialize the members in their declaration order.

The following code creates an object named ``three_of_clubs`` that
represents the 3 of Clubs:

::

      playing_card three_of_clubs (0, 3);

The first argument, ``0`` represents the suit Clubs, the second,
naturally, represents the rank 3.

.. tb-blank::
   :name: c192_card_objects_1

   The instance variables for a playing card are {{blank:blank1}} and {{blank:blank2}}.

   .. tb-answer:: blank1
      :regex:
      :match: suit|rank
      :feedback: Correct!

   .. tb-answer:: blank2
      :match: x

.. tb-choice::
   :name: card_objects_2

   What does it mean to **encode** the ranks and suits?

   - [ ] To translate each rank / suit into a secret code.

     Incorrect! This is called encryption.
   - [ ] To create strings to represent each rank / suit.

     Incorrect! We create strings before we encode.
   - [x] To define a mapping between each rank / suit and a sequence of numbers.

     Correct! This makes it easier to compare cards.
   - [ ] To write code describing real objects, like cards, with their respective ranks / suits.

     Incorrect! This is how we describe object-oriented programming.

.. tb-blank::
   :name: c192_card_objects_3

   The symbol :math:`\mapsto` means __________.

   {{blank}}

   .. tb-answer::
      :regex:
      :match: maps to
      :feedback: Correct!
      :incorrect: Incorrect!  Try again!

.. tb-choice::
   :name: card_objects_4

   What is the purpose of mapping?

   - [ ] To have better organization in your code.

     Incorrect! Mapping helps more with order than with organization.
   - [x] To make it possible to compare objects that have non-numerical values.

     Correct! By mapping non-numerical values to integers, we can compare them!
   - [ ] To represent complex objects visually.

     Incorrect! There is nothing visual about mapping.
   - [ ] To add complexity to your code.

     Incorrect! Mapping actually simplifies your code.

