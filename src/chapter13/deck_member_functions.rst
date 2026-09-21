.. _objects-vectors-carddeck-member-functions:

``card_deck`` member functions
------------------------------

Now that we have a ``card_deck`` object, it makes sense to put all the
functions that pertain to ``card_deck``\ s in the ``card_deck`` structure
definition. Looking at the functions we have written so far, one obvious
candidate is ``print_deck`` (:numref:`c192_printdeck`).
Here’s how it looks, rewritten as a ``card_deck`` member function:

::

   void card_deck::print () const {
     for (std::size_t i = 0; i < cards.size(); i++) {
       cards[i].print ();
     }
   }

As usual, we can refer to the instance variables of the current object
without using dot notation.

The active code below prints out the deck of cards like in the previous section. Notice we can just use ``deck.print ()``
to print out the deck instead of writing a for loop in main.

.. tb-code:: cpp
   :name: c192_deck_members_ac_1-support
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

   void card_deck::print () const {
       for (std::size_t i = 0; i < cards.size(); i++) {
           cards[i].print ();
       }
   }


.. tb-code:: cpp
   :name: c192_deck_members_ac_1
   :caption: Example c192_deck_members_ac_1
   :run-after: c192_deck_members_ac_1-support

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
      void print () const;
   };

   int main() {
       card_deck deck;
       deck.print ();
   }

For some of the other functions, it is not obvious whether they should
be member functions of ``playing_card``, member functions of ``card_deck``, or
nonmember functions that take ``playing_card``\ s and ``card_deck``\ s as parameters.
For example, the version of ``find`` in the previous chapter takes a
``playing_card`` and a ``card_deck`` as arguments, but you could reasonably make it a
member function of either type. As an exercise, rewrite ``find`` as a
``card_deck`` member function that takes a ``playing_card`` as a parameter.

Writing ``find`` as a ``playing_card`` member function is a little tricky.
Here’s my version:

::

   std::ptrdiff_t playing_card::find (const card_deck& deck) const {
     for (std::size_t i = 0; i < deck.cards.size(); i++) {
       if (equals (deck.cards[i], *this)) return static_cast<std::ptrdiff_t>(i);
     }
     return -1;
   }

The first trick is that we have to use the keyword ``this`` to refer to
the ``playing_card`` the function is invoked on.

The second trick is that C++ does not make it easy to write structure
definitions that refer to each other. The problem is that when the
compiler is reading the first structure definition, it doesn’t know
about the second one yet.

One solution is to declare ``card_deck`` before ``playing_card`` and then define
``card_deck`` afterwards:

::

   // declare that card_deck is a structure, without defining it
   struct card_deck;

   // that way we can refer to it in the definition of playing_card
   struct playing_card {
     int m_suit, m_rank;

     playing_card ();
     playing_card (int s, int r);

     void print () const;
     bool is_greater (const playing_card& c2) const;
     std::ptrdiff_t find (const card_deck& deck) const;
   };

   // and then later we provide the definition of card_deck
   struct card_deck {
     std::vector<playing_card> cards;

     card_deck ();
     card_deck (std::size_t n);
     void print () const;
     std::ptrdiff_t find (const playing_card& card) const;
   };

.. _c192_shuffle:

.. tb-choice::
   :name: deck_members_1

   Multiple Response: What are some tricks we can use to write ``find`` as a ``card`` member function?

   - [x] Use the keyword this.

     We use this to refer to the card that the function is invoked on.
   - [ ] Define deck before card.

     We don't have to define deck before card.
   - [ ] Pass a card parameter in the card member function find.

     What do we pass as a parameter in find?
   - [x] Declare deck before card and then define deck afterwards.

     This is how we implemented our code!

.. tb-parsons::
   :name: c192_deck_members_2

   Write find as a card_deck member function that takes a playing_card as a parameter.

   .. code-block:: c++

      {{group}}
      std::ptrdiff_t card_deck::find (playing_card card) const {
      {{endgroup}}
      {{distractor}}
      {{group}}
      std::ptrdiff_t find (playing_card) {
      {{endgroup}}
      {{group}}
         for (std::size_t i = 0; i < cards.size(); i++) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         for (std::size_t i = 0; i < deck.cards.size(); i++) {
      {{endgroup}}
      {{group}}
            if (cards[i].equals(card)) {
               return static_cast<std::ptrdiff_t>(i);
            }
      {{endgroup}}
      {{distractor}}
      {{group}}
            if (equals (deck.cards[i], *this)) {
               return static_cast<std::ptrdiff_t>(i);
            }
      {{endgroup}}
      {{group}}
         }
         return -1;
      }
      {{endgroup}}

The active code below uses the ``find`` function that we just wrote.

.. tb-code:: cpp
   :name: c192_deck_members_ac_2-support
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

   void card_deck::print () const {
       for (std::size_t i = 0; i < cards.size(); i++) {
           cards[i].print ();
       }
   }

   std::ptrdiff_t card_deck::find (playing_card card) const {
       for (std::size_t i = 0; i < cards.size(); i++) {
           if (cards[i].equals(card)) {
               return static_cast<std::ptrdiff_t>(i);
           }
       }
       return -1;
   }

   bool playing_card::equals (const playing_card& c2) const {
       return (m_rank == c2.m_rank && m_suit == c2.m_suit);
   }


.. tb-code:: cpp
   :name: c192_deck_members_ac_2
   :caption: Example c192_deck_members_ac_2
   :run-after: c192_deck_members_ac_2-support

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
       bool equals (const playing_card& c2) const;
   };

   struct card_deck {
       std::vector<playing_card> cards;
       card_deck ();
       void print () const;
       std::ptrdiff_t find (playing_card card) const;
   };

   int main() {
       card_deck deck;
       playing_card card (clubs, ace);
       playing_card card2 (diamonds, ace);
       // Should output 0 and 13
       std::cout << deck.find(card) << '\n';
       std::cout << deck.find(card2) << '\n';
   }

