.. _vectors-objects-the-equals-function:

The ``equals`` function
-----------------------

In order for two cards to be equal, they have to have the same rank and
the same suit. Unfortunately, the ``==`` operator does not work for
user-defined types like ``playing_card``, so we have to write a function that
compares two cards. We’ll call it ``equals``. It is also possible to
write a new definition for the ``==`` operator, but we will not cover
that in this book.

It is clear that the return value from ``equals`` should be a boolean
that indicates whether the cards are the same. It is also clear that
there have to be two ``playing_card``\ s as parameters. But we have one more
choice: should ``equals`` be a member function or a free-standing
function?

As a member function, it looks like this:

::

   bool playing_card::equals (const playing_card& c2) const {
     return (m_rank == c2.m_rank && m_suit == c2.m_suit);
   }

To use this function, we have to invoke it on one of the cards and pass
the other as an argument:

::

     playing_card card1 (1, 11);
     playing_card card2 (1, 11);

     if (card1.equals(card2)) {
       std::cout << "Yup, that's the same card." << '\n';
     }

This method of invocation always seems strange to me when the function
is something like ``equals``, in which the two arguments are symmetric.
What I mean by symmetric is that it does not matter whether I ask “Is A
equal to B?” or “Is B equal to A?” in this case, I think it looks better
to rewrite ``equals`` as a nonmember function:

::

   bool equals (const playing_card& c1, const playing_card& c2) {
     return (c1.m_rank == c2.m_rank && c1.m_suit == c2.m_suit);
   }

When we call this version of the function, the arguments appear
side-by-side in a way that makes more logical sense, to me at least.

::

     if (equals (card1, card2)) {
       std::cout << "Yup, that's the same card." << '\n';
     }

Of course, this is a matter of taste. My point here is that you should
be comfortable writing both member and nonmember functions, so that you
can choose the interface that works best depending on the circumstance.

Run the active code below to see how the ``equals()`` function works.

.. tb-code:: cpp
   :name: c192_12_4-support
   :hidden:


   playing_card::playing_card () {
     m_suit = 0;  m_rank = 1;
   }

   playing_card::playing_card (int s, int r) {
     m_suit = s;  m_rank = r;
   }

   bool playing_card::equals (const playing_card& c2) const {
     bool boolean = (m_rank == c2.m_rank && m_suit == c2.m_suit);
     if (boolean == true) {
       std::cout << "Yup, that's the same card." << '\n';
     }
     else {
       std::cout << "Nope, those cards are different." << '\n';
     }
     return boolean;
   }

   void playing_card::print () const {
     std::vector<std::string> suits (4);
     suits[0] = "Clubs";
     suits[1] = "Diamonds";
     suits[2] = "Hearts";
     suits[3] = "Spades";

     std::vector<std::string> ranks (14);
     ranks[1] = "Ace";
     ranks[2] = "2";
     ranks[3] = "3";
     ranks[4] = "4";
     ranks[5] = "5";
     ranks[6] = "6";
     ranks[7] = "7";
     ranks[8] = "8";
     ranks[9] = "9";
     ranks[10] = "10";
     ranks[11] = "Jack";
     ranks[12] = "Queen";
     ranks[13] = "King";

      std::cout << ranks[m_rank] << " of " << suits[m_suit] << '\n';
   }


.. tb-code:: cpp
   :name: c192_12_4
   :caption: Example c192_12_4
   :run-after: c192_12_4-support

   #include <iostream>
   #include <string>
   #include <vector>

   struct playing_card {
       int m_suit, m_rank;

       playing_card ();
       playing_card (int s, int r);
       void print () const;
       bool equals (const playing_card& c2) const;
   };

   int main() {
       playing_card card1 (1,11);
       playing_card card2 (1,11);
       playing_card card3 (3,11);
       card1.equals(card2);
       card1.equals(card3);
   }

.. tb-choice::
   :name: equals_function_1

   How can we compare two ``card`` objects?

   - [ ] Directly, using the build in == operator.

     Incorrect! We have to create our own method to compare two card objects, the == operator won't work.
   - [ ] compare their ranks and suits separately using the == operator. If either comparison is true, then they are equal.

     Incorrect! This would return true if two cards have the same rank, but different suits OR the same suit, but different ranks.
   - [x] compare their ranks and suits separately using the == operator. If either comparison is false, then they are NOT equal.

     Correct! Both ranks and suits must be the same for two cards to be equal.
   - [ ] They cannot be compared because they are non-numerical objects.

     Incorrect! card objects can be compared, but we must create our own method.

.. tb-choice::
   :name: equals_function_2

   Should we write the ``equals()`` function as a free-standing function, or as a member function of ``card``?

   - [ ] A free-standing function, because we shouldn't "invoke" the function on just one ``card``.

     - Incorrect! We can invoke the function on a ``card``!

   - [ ] A member function, because the ``equals()`` operation is part of the ``card`` data structure.

     -  Incorrect! The ``equals()`` operation is not necessarily part of the ``card`` data structure.

   - [x] Both are viable.

     + Correct! This is a matter of preference!


.. tb-parsons::
   :name: c192_equals_function_3

   in a card game called Euchre, the highest ranked suit is called the trump suit.  The trump suit contains
   all of the cards of that suit, and the Jack of the other suit of the same color.  For example, if Hearts
   was trump, the trump suit would contain all Hearts, and the Jack of Diamonds.  Implement the is_trump()
   function that returns true of a playing_card is part of the trump suit.  Assume we have a helper function same_color()
   that returns the other suit of the same color.

   .. code-block:: c++

      {{group}}
      bool playing_card::is_trump (std::string trump_suit) {
      {{endgroup}}
      {{group}}
       if (m_suit == trump_suit) {
        return true;
       }
      {{endgroup}}
      {{distractor}}
      {{group}}
       if (m_suit != trump_suit) {
        return false;
       }
      {{endgroup}}
      {{group}}
       else if (m_rank == "Jack" && m_suit == same_color()) {
        return true;
       }
      {{endgroup}}
      {{distractor}}
      {{group}}
       else if (m_rank == "Jack") {
        return true;
       }
      {{endgroup}}
      {{group}}
       else {
        return false;
       }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
      {{distractor}}
      {{group}}
      };
      {{endgroup}}

