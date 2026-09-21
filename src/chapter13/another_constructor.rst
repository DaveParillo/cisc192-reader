.. _objects-vectors-another-constructor:

Another constructor
-------------------

Now that we have a ``card_deck`` object, it would be useful to initialize the
cards in it. From the previous chapter we have a function called
``build_deck`` that we could use (with a few adaptations), but it might
be more natural to write a second ``card_deck`` constructor.

::

   card_deck::card_deck () {
     std::vector<playing_card> temp (52);
     cards = temp;

     std::size_t i = 0;
     for (int m_suit = clubs; m_suit <= spades; ++m_suit) {
       for (int m_rank = ace; m_rank <= king; ++m_rank) {
         cards[i].m_suit = static_cast<card_suit>(m_suit);
         cards[i].m_rank = static_cast<card_rank>(m_rank);
         i++;
       }
     }
   }

Notice how similar this function is to ``build_deck``, except that we had
to change the syntax to make it a constructor. Now we can create a
standard 52-card deck with the simple declaration ``card_deck deck;``

The active code below prints out the cards in a deck using the loop from the previous section.

.. tb-code:: cpp
   :name: c192_deck_constructor_ac_1-support
   :hidden:

   playing_card::playing_card () {
       m_suit = spades;  m_rank = ace;
   }

   playing_card::playing_card (card_suit s, card_rank r) {
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

   card_deck::card_deck () {
       std::vector<playing_card> temp (52);
       cards = temp;

       std::size_t i = 0;
       for (int m_suit = clubs; m_suit <= spades; ++m_suit) {
           for (int m_rank = ace; m_rank <= king; ++m_rank) {
               cards[i].m_suit = static_cast<card_suit>(m_suit);
               cards[i].m_rank = static_cast<card_rank>(m_rank);
               i++;
           }
       }
   }


.. tb-code:: cpp
   :name: c192_deck_constructor_ac_1
   :caption: Example c192_deck_constructor_ac_1
   :run-after: c192_deck_constructor_ac_1-support

   #include <cstddef>
   #include <iostream>
   #include <string>
   #include <vector>

   enum card_suit { clubs, diamonds, hearts, spades };

   enum card_rank { ace=1, two, three, four, five, six, seven, eight, nine,
   ten, jack, queen, king };

   struct playing_card {
       card_rank m_rank;
       card_suit m_suit;
       playing_card ();
       playing_card (card_suit s, card_rank r);
       void print () const;
   };

   struct card_deck {
       std::vector<playing_card> cards;
       card_deck ();
   };

   int main() {
       card_deck deck;
       for (std::size_t i = 0; i < 52; i++) {
           deck.cards[i].print();
       }
   }

.. tb-choice::
   :name: deck_constructor_1

   Based on your observations from the active code above, the cards in ``deck`` are initialized 
   to the correct suits and ranks of a standard deck of 52 cards.

   - [ ] True - we used the build_deck function with a few modifications to do this.

     How do we create the deck?
   - [x] True - we wrote a deck constructor to do this.

     The for loops in the deck constructor initialize each card to its proper value.
   - [ ] False - we used the build_deck function with a few modifications to do this.

     Look at the active code.  How do we create the deck?
   - [ ] False - we wrote a deck constructor to do this.

     Look at the active code.

.. tb-parsons::
   :name: c192_deck_constructor_2

      Let's write a constructor for a deck of cards that uses 40 cards.
      This deck uses all 4 suits and ranks Ace through 10, omitting all
      face cards.

   .. code-block:: c++

      {{group}}
         card_deck::card_deck () {
      {{endgroup}}
      {{group}}
            std::vector<playing_card> temp (40);
      {{endgroup}}
      {{distractor}}
      {{group}}
            std::vector<playing_card> temp (52);
      {{endgroup}}
      {{group}}
            cards = temp;
            std::size_t i = 0;
      {{endgroup}}
      {{group}}
            for (int m_suit = clubs; m_suit <= spades; ++m_suit) {
      {{endgroup}}
      {{distractor}}
      {{group}}
            for (card_suit m_suit = clubs; m_suit < spades; m_suit = card_suit(m_suit+1)) {
      {{endgroup}}
      {{group}}
               for (card_rank m_rank = ace; m_rank <= ten; m_rank = card_rank(m_rank+1)) {
      {{endgroup}}
      {{distractor}}
      {{group}}
               for (int m_rank = ace; m_rank <= king; ++m_rank) {
      {{endgroup}}
      {{group}}
                 cards[i].m_suit = static_cast<card_suit>(m_suit);
                 cards[i].m_rank = static_cast<card_rank>(m_rank);
      {{endgroup}}
      {{distractor}}
      {{group}}
                 cards[i].m_suit = m_rank;
                 cards[i].m_rank = m_suit;
      {{endgroup}}
      {{group}}
                 i++;
               }
            }
         }
      {{endgroup}}

