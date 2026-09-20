.. _objects-vectors-subdecks:

Subdecks
--------

How should we represent a hand or some other subset of a full deck? One
easy choice is to make a ``card_deck`` object that has fewer than 52 cards.

We might want a function, ``subdeck``, that takes a vector of cards and
a range of indices, and that returns a new vector of cards that contains
the specified subset of the deck:

::

   card_deck card_deck::subdeck (std::ptrdiff_t low, std::ptrdiff_t high) const {
     card_deck sub (high - low + 1);

     for (std::size_t i = 0; i < sub.cards.size(); i++) {
       sub.cards[i] = cards[low + i];
     }
     return sub;
   }

To create the local variable named ``sub``, we use the ``card_deck``
constructor that takes a size and default-initializes its cards.
We then assign the corresponding cards
from the original deck over those defaults.

The length of the subdeck is ``high - low + 1`` because both the low card
and high card are included.

The endpoints use ``std::ptrdiff_t`` because an empty range can end at
``low - 1``, including ``-1`` when ``low`` is zero. Require
``0 <= low <= std::ssize(cards)`` and
``low - 1 <= high < std::ssize(cards)`` before subtracting or indexing.
The complete example below checks these conditions and rejects an invalid
range with ``std::out_of_range``. Its allocation size uses ``std::size_t``.

.. warning::
   This sort of computation can be confusing and can lead to “off-by-one”
   errors. Drawing a picture is usually the best way to avoid them.

As an exercise, write a version of ``find_bisect`` that takes a subdeck
as an argument, rather than a deck and an index range. Which version is
more error-prone? Which version do you think is more efficient?

Try writing the ``find_bisect`` function in the commented section
of the active code below. If done correctly, the program should output that
the Seven of Clubs is at index 6 and the King of Diamonds is at index -1.
If you get stuck, you can reveal the extra problem at the end for help.

.. tb-code:: cpp
   :name: c192_subdeck_cards_1-support
   :hidden:

   playing_card::playing_card () {
       suit = spades;  rank = ace;
   }

   playing_card::playing_card (card_suit s, card_rank r) {
       suit = s;  rank = r;
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

       cout << ranks[rank] << " of " << suits[suit] << '\n';
   }

   bool playing_card::is_greater (const playing_card& c2) const {
       if (suit > c2.suit) return true;
       if (suit < c2.suit) return false;
       if (rank > c2.rank) return true;
       if (rank < c2.rank) return false;
       return false;
   }

   bool playing_card::equals (const playing_card& c2) const {
       return (rank == c2.rank && suit == c2.suit);
   }

   card_deck::card_deck () {
       std::vector<playing_card> temp (52);
       cards = temp;

       std::size_t i = 0;
       for (int suit = clubs; suit <= spades; ++suit) {
           for (int rank = ace; rank <= king; ++rank) {
               cards[i].suit = static_cast<card_suit>(suit);
               cards[i].rank = static_cast<card_rank>(rank);
               i++;
           }
       }
   }

   card_deck::card_deck (std::size_t size) {
        std::vector<playing_card> temp (size);
        cards = temp;
   }

   void card_deck::print () const {
       for (std::size_t i = 0; i < cards.size(); i++) {
           cards[i].print ();
       }
   }

   std::size_t random_int(std::size_t low, std::size_t high) {
       static std::mt19937 engine(std::random_device{}());
       return std::uniform_int_distribution<std::size_t>{low, high}(engine);
   }

   void card_deck::swap_cards (std::size_t index1, std::size_t index2) {
       playing_card temp = cards[index1];
       cards[index1] = cards[index2];
       cards[index2] = temp;
   }

   std::size_t card_deck::find_lowest_card (std::size_t index) {
       std::size_t min = index;
       for (std::size_t i = index; i < cards.size(); ++i) {
           if (cards[min].is_greater(cards[i])) {
               min = i;
           }
      }
      return min;
   }

   void card_deck::shuffle_deck () {
       for (std::size_t i = 0; i < cards.size(); i++) {
           std::size_t x = random_int (i, cards.size() - 1);
           swap_cards (i, x);
       }
   }

   void card_deck::sort_deck () {
       for (std::size_t i = 0; i < cards.size(); i++) {
           std::size_t x = find_lowest_card (i);
           swap_cards (i, x);
       }
   }

   card_deck card_deck::subdeck (std::ptrdiff_t low, std::ptrdiff_t high) const {
       if (low < 0 || low > std::ssize(cards) || high < low - 1 || high >= std::ssize(cards)) {
           throw std::out_of_range("subdeck range");
       }
       card_deck sub (static_cast<std::size_t>(high - low + 1));

       for (std::size_t i = 0; i<sub.cards.size(); i++) {
           sub.cards[i] = cards[low+i];
       }
       return sub;
   }


.. tb-code:: cpp
   :name: c192_subdeck_cards_1
   :caption: Example c192_subdeck_cards_1
   :run-after: c192_subdeck_cards_1-support

   #include <iterator>
   #include <stdexcept>
   #include <cstddef>
   #include <random>
   #include <iostream>
   #include <string>
   #include <vector>
   #include <cstdlib>
   using std::cout;

   enum card_suit { clubs, diamonds, hearts, spades };

   enum card_rank { ace=1, two, three, four, five, six, seven, eight, nine,
   ten, jack, queen, king };

   std::size_t random_int(std::size_t low, std::size_t high);

   struct playing_card {
       card_rank rank;
       card_suit suit;
       playing_card ();
       playing_card (card_suit s, card_rank r);
       void print () const;
       bool is_greater (const playing_card& c2) const;
       bool equals (const playing_card& c2) const;
   };

   struct card_deck {
       std::vector<playing_card> cards;
       card_deck ();
       card_deck (std::size_t n);
       void print () const;
       void swap_cards (std::size_t index1, std::size_t index2);
       std::size_t find_lowest_card (std::size_t index);
       void shuffle_deck ();
       void sort_deck ();
       card_deck subdeck (std::ptrdiff_t low, std::ptrdiff_t high) const;
   };

   std::ptrdiff_t find_bisect (card_deck subdeck, playing_card card) {
       // ``find_bisect`` should search through the subdeck and
       // return the location of card. If card is not found in
       // subdeck, it should return -1.
       // Delete the return 0 and write your implementation here.
       return 0;
   }

   int main() {
       card_deck deck;
       card_deck club_cards = deck.subdeck(0, 12);
       club_cards.print();
       playing_card card1 (clubs, seven);
       playing_card card2 (diamonds, king);
       cout << '\n';
       cout << "The Seven of Clubs is at index " << find_bisect (club_cards, card1) << '\n';
       cout << "The King of Diamonds is at index " << find_bisect (club_cards, card2) << '\n';
   }

.. tb-reveal:: find_bisect Help
   :name: c192_subdecks_reveal_1

   .. tb-parsons::
      :name: c192_subdecks_help_1

      Return the index of the card in this sorted subdeck, or -1 if it is absent. The subdeck function accepts inclusive signed endpoints.

      .. code-block:: c++

         {{group}}
         std::ptrdiff_t find_bisect(card_deck subdeck, playing_card card) {
         {{endgroup}}
         {{group}}
             if (subdeck.cards.empty()) return -1;
         {{endgroup}}
         {{group}}
             const std::ptrdiff_t mid = std::ssize(subdeck.cards) / 2;
         {{endgroup}}
         {{group}}
             if (subdeck.cards[mid].equals(card)) return mid;
         {{endgroup}}
         {{group}}
             if (subdeck.cards[mid].is_greater(card)) {
                 return find_bisect(subdeck.subdeck(0, mid - 1), card);
             }
         {{endgroup}}
         {{group}}
             const std::ptrdiff_t found = find_bisect(
                 subdeck.subdeck(mid + 1, std::ssize(subdeck.cards) - 1), card);
         {{endgroup}}
         {{group}}
             return found == -1 ? -1 : mid + 1 + found;
         }
         {{endgroup}}

