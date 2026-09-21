.. _vectors-objects-searching:
.. _c192_find:

Searching
---------

Container sizes and ordinary indices use ``std::size_t`` from ``<cstddef>``.
This search returns ``std::ptrdiff_t``, the signed difference type from the
same header, because ``-1`` means "not found." Check that result before
using it as an index. These examples assume the deck's size fits in
``std::ptrdiff_t``. C++20's ``std::ssize`` from ``<iterator>`` provides a
signed size when we need to subtract one, including for an empty deck.

The next function I want to write is ``find``, which searches through a
vector of ``playing_card``\ s to see whether it contains a certain card. It may
not be obvious why this function would be useful, but it gives me a
chance to demonstrate two ways to go searching for things, a ``linear``
search and a ``bisection`` search.

Linear search is the more obvious of the two; it involves traversing the
deck and comparing each card to the one we are looking for. If we find
it we return the index where the card appears. If it is not in the deck,
we return -1.

::

   std::ptrdiff_t find (const playing_card& card, const std::vector<playing_card>& deck) {
     for (std::size_t i = 0; i < deck.size(); i++) {
       if (equals (deck[i], card)) return static_cast<std::ptrdiff_t>(i);
     }
     return -1;
   }

The loop here is exactly the same as the loop in ``print_deck``. In fact,
when I wrote the program, I copied it, which saved me from having to
write and debug it twice.

Inside the loop, we compare each element of the deck to ``card``. The
function returns as soon as it discovers the card, which means that we
do not have to traverse the entire deck if we find the card we are
looking for. If the loop terminates without finding the card, we know
the card is not in the deck and return ``-1``.

To test this function, I wrote the following:

::

     std::vector<playing_card> deck = build_deck ();

     std::ptrdiff_t index = find (deck[17], deck);
     std::cout << "I found the card at index = " << index << '\n';

The output of this code is

::

   I found the card at index = 17

The code below searches for a particular card in a standard deck of 52 cards.
It returns the index that the card was located at.

.. tb-code:: cpp
   :name: c192_12_8-support
   :hidden:


   playing_card::playing_card () {
      m_suit = 0;  m_rank = 1;
   }

   playing_card::playing_card (int s, int r) {
      m_suit = s;  m_rank = r;
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

    void print_deck (const std::vector<playing_card>& deck) {
      for (std::size_t i = 0; i < deck.size(); i++) {
        deck[i].print ();
      }
    }

   std::vector<playing_card> build_deck() {
      std::vector<playing_card> deck (52);
      std::size_t i = 0;
      for (int m_suit = 0; m_suit <= 3; m_suit++) {
         for (int m_rank = 1; m_rank <= 13; m_rank++) {
            deck[i].m_suit = m_suit;
            deck[i].m_rank = m_rank;
            i++;
         }
      }
      return deck;
   }

   std::ptrdiff_t find (const playing_card& card, const std::vector<playing_card>& deck) {
      for (std::size_t i = 0; i < deck.size(); i++) {
       if (equals (deck[i], card)) return static_cast<std::ptrdiff_t>(i);
      }
      return -1;
   }


.. tb-code:: cpp
   :name: c192_12_8
   :caption: Example c192_12_8
   :run-after: c192_12_8-support

   #include <cstddef>
   #include <iostream>
   #include <string>
   #include <vector>

   struct playing_card {
       int m_suit, m_rank;

       playing_card ();
       playing_card (int s, int r);
       void print () const;
   };

   std::vector<playing_card> build_deck();

   bool equals (const playing_card& c1, const playing_card& c2){
       return (c1.m_rank == c2.m_rank && c1.m_suit == c2.m_suit);
   }

   void print_deck(const std::vector<playing_card>& deck);

   std::ptrdiff_t find (const playing_card& card, const std::vector<playing_card>& deck);

   int main() {
       std::vector<playing_card> deck = build_deck();
       playing_card card (3, 6);
       std::cout << find(card, deck);
   }

.. tb-blank::
   :name: c192_searching_1

   Say we have standard deck of cards. According to our ``find()`` function, the
   for loop will execute a minimum of {{blank:blank1}} times, and a maximum of {{blank:blank2}}
   times while searching for a particular card.

   .. tb-answer:: blank1
      :match: 1
      :feedback: Correct!

   .. tb-answer:: blank2
      :match: x

.. tb-blank::
   :name: c192_searching_2

   ``build_euchre_deck()`` returns the deck of Euchre cards defined on the previous page.
   If we run the following code, what is returned?

   ::

     int main() {
        euchre_deck = build_euchre_deck();
        playing_card card (3, 6);
        find(card, euchre_deck);
      }

   {{blank}}.

   .. tb-answer::
      :match: -1
      :feedback: Correct! The find method should return -1 if the card is not part of the deck.
      :match: x
