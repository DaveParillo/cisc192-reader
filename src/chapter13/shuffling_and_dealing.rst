.. _objects-vectors-shuffling-and-dealing:

Shuffling and dealing
---------------------

In :numref:`c192_shuffling`, I wrote pseudocode for a shuffling
algorithm. Assuming that we have a function called ``shuffle_deck`` that
takes a deck as an argument and shuffles it, we can create and shuffle a
deck:

::

     card_deck deck;               // create a standard 52-card deck
     deck.shuffle_deck ();     // shuffle it

Then, to deal out several hands, we can use ``subdeck``:

::

     card_deck hand1 = deck.subdeck (0, 4);
     card_deck hand2 = deck.subdeck (5, 9);
     card_deck pack = deck.subdeck (10, 51);

This code puts the first 5 cards in one hand, the next 5 cards in the
other, and the rest into the pack.

When you thought about dealing, did you think we should give out one
card at a time to each player in the round-robin style that is common in
real card games? I thought about it, but then realized that it is
unnecessary for a computer program. The round-robin convention is
intended to mitigate imperfect shuffling and make it more difficult for
the dealer to cheat. Neither of these is an issue for a computer.

This example is a useful reminder of one of the dangers of engineering
metaphors: sometimes we impose restrictions on computers that are
unnecessary, or expect capabilities that are lacking, because we
unthinkingly extend a metaphor past its breaking point. Beware of
misleading analogies.

The active code below deals a deck of cards among three players for a game
of Go Fish. Feel free to experiment with the code and deal decks for other
games like War, Poker, and Egyptian Ratscrew.

.. tb-code:: cpp
   :name: c192_shuffle_deal_ac_1-support
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

       cout << ranks[m_rank] << " of " << suits[m_suit] << '\n';
   }

   bool playing_card::is_greater (const playing_card& c2) const {
       if (m_suit > c2.m_suit) return true;
       if (m_suit < c2.m_suit) return false;
       if (m_rank > c2.m_rank) return true;
       if (m_rank < c2.m_rank) return false;
       return false;
   }

   bool playing_card::equals (const playing_card& c2) const {
       return (m_rank == c2.m_rank && m_suit == c2.m_suit);
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

   std::ptrdiff_t find_bisect(card_deck subdeck, playing_card card) {
       if (subdeck.cards.empty()) return -1;
       const std::ptrdiff_t mid = std::ssize(subdeck.cards) / 2;
       if (subdeck.cards[mid].equals(card)) return mid;
       if (subdeck.cards[mid].is_greater(card)) {
           return find_bisect(subdeck.subdeck(0, mid - 1), card);
       }
       const std::ptrdiff_t found = find_bisect(
           subdeck.subdeck(mid + 1, std::ssize(subdeck.cards) - 1), card);
       return found == -1 ? -1 : mid + 1 + found;
   }

   void card_deck::shuffle_deck () {
       for (std::size_t i = 0; i < cards.size(); i++) {
           std::size_t m_x = random_int (i, cards.size() - 1);
           swap_cards (i, m_x);
       }
   }

   void card_deck::sort_deck () {
       for (std::size_t i = 0; i < cards.size(); i++) {
           std::size_t m_x = find_lowest_card (i);
           swap_cards (i, m_x);
       }
   }


.. tb-code:: cpp
   :name: c192_shuffle_deal_ac_1
   :caption: Example c192_shuffle_deal_ac_1
   :run-after: c192_shuffle_deal_ac_1-support

   #include <stdexcept>
   #include <iterator>
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
       card_rank m_rank;
       card_suit m_suit;
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

   std::ptrdiff_t find_bisect (card_deck subdeck, playing_card card);

   int main() {
       card_deck deck;
       deck.shuffle_deck();
       card_deck hand1 = deck.subdeck(0, 6);
       card_deck hand2 = deck.subdeck(7, 13);
       card_deck hand3 = deck.subdeck(14, 20);
       card_deck pack = deck.subdeck(21, 51);
       cout << "Player 1's hand:" << '\n';
       hand1.print();
       cout << '\n';
       cout << "Player 2's hand:" << '\n';
       hand2.print();
       cout << '\n';
       cout << "Player 3's hand:" << '\n';
       hand3.print();
   }

