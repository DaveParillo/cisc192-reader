
.. _c192_sorting:

Sorting
-------

Now that we have messed up the deck, we need a way to put it back in
order. Ironically, there is an algorithm for sorting that is very
similar to the algorithm for shuffling.

Again, we are going to traverse the deck and at each location choose
another card and swap. The only difference is that this time instead of
choosing the other card at random, we are going to find the lowest card
remaining in the deck.

By “remaining in the deck,” I mean cards that are at or to the right of
the index ``i``.

::

     for (std::size_t i = 0; i < cards.size(); i++) {
       // find the lowest card at or to the right of i
       // swap the ith card and the lowest card
     }

.. index::
   single: helper function

Again, the pseudocode helps with the design of the **helper functions**.

.. note::
   **Helper functions** do exactly what it seems like they would do.  They
   are shorter, simpler functions that *help* the bigger functions accomplish
   a task.  As a result, they shorten the code used in the bigger functions,
   and they make the debugging process easier.

In this case we can use ``swap_cards`` again, so we only need one new
one, called ``find_lowest_card``, that takes an index where it should start
looking in the vector of cards.

.. index::
   single: top-down design

This process, using pseudocode to figure out what helper functions are
needed, is sometimes called **top-down design**, in contrast to the
bottom-up design I discussed In :doc:`../chapter11/counting`.

Once again, I am going to leave the implementation up to the reader.


.. tb-blank::
   :name: c192_sorting_deck_1

   If I'm writing a long, complex function with many steps, a(n) {{blank:blank1}} {{blank:blank2}}
   would help me condense the function's code and make it easier to understand.

   .. tb-answer:: blank1
      :match: [Hh][Ee][Ll][Pp][Ee][Rr]
      :feedback: Correct!
      :incorrect: Try again!

   .. tb-answer:: blank2
      :match: [Ff][Uu][Nn][Cc][Tt][Ii][Oo][Nn]
      :incorrect: Try again!

Try writing the ``find_lowest_card`` function in the commented section
of the active code below. Once you're done with ``find_lowest_card``,
try using it along with ``swap_cards`` to implement the ``card_deck`` member
function ``sort_deck``. If done correctly, the program should output a
sorted deck of cards. If you get stuck, you can reveal the extra problems
at the end for help.

.. tb-code:: cpp
   :name: c192_sorting_deck_2-support
   :hidden:
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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

       std::cout << ranks[rank] << " of " << suits[suit] << std::endl;
   }

   bool playing_card::is_greater (const playing_card& c2) const {
       if (suit > c2.suit) return true;
       if (suit < c2.suit) return false;
       if (rank > c2.rank) return true;
       if (rank < c2.rank) return false;
       return false;
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

   void card_deck::shuffle_deck () {
       for (std::size_t i = 0; i < cards.size(); i++) {
           std::size_t x = random_int (i, cards.size() - 1);
           swap_cards (i, x);
       }
   }


.. tb-code:: cpp
   :name: c192_sorting_deck_2
   :caption: Example c192_sorting_deck_2
   :run-after: c192_sorting_deck_2-support
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <cstddef>
   #include <random>
   #include <iostream>
   #include <string>
   #include <vector>
   #include <cstdlib>

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
   };

   struct card_deck {
       std::vector<playing_card> cards;
       card_deck ();
       void print () const;
       void swap_cards (std::size_t index1, std::size_t index2);
       std::size_t find_lowest_card (std::size_t index);
       void shuffle_deck ();
       void sort_deck ();
   };

   std::size_t card_deck::find_lowest_card (std::size_t index) {
       // ``find_lowest_card`` should search through the vector of cards
       // starting at index and return the index of the smallest card.
       // Delete the return 0 and write your implementation here.
       return 0;
   }

   void card_deck::sort_deck () {
       // Follow the pseudocode from above and use ``find_lowest_card`` and
       // ``swap_cards`` to write the ``sort`` member function.
       // Write your implementation here.
   }

   int main() {
       card_deck deck;
       deck.shuffle_deck ();
       deck.sort_deck ();
       deck.print ();
   }

.. tb-reveal:: find_lowest_card Help
   :name: c192_sorting_reveal_1

   .. tb-parsons::
      :name: c192_sorting_help_1

      Let's write the code for the find_lowest_card function. find_lowest_card
      should take an index as a parameter and return an int.

      .. code-block:: c++

         {{group}}
         std::size_t card_deck::find_lowest_card (std::size_t index) {
         {{endgroup}}
         {{distractor}}
         {{group}}
         void card_deck::find_lowest_card (std::size_t index) {
         {{endgroup}}
         {{group}}
          std::size_t min = index;
         {{endgroup}}
         {{group}}
          for (std::size_t i = index; i < cards.size(); ++i) {
         {{endgroup}}
         {{distractor}}
         {{group}}
          for (std::size_t i = 0; i < cards.size(); ++i) {
         {{endgroup}}
         {{group}}
           if (cards[min].is_greater(cards[i])) {
         {{endgroup}}
         {{distractor}}
         {{group}}
           if (cards[i].is_greater(cards[min])) {
         {{endgroup}}
         {{group}}
            min = i;
           }
          }
         {{endgroup}}
         {{group}}
          return min;
         }
         {{endgroup}}
         {{distractor}}
         {{group}}
          return cards[min];
         }
         {{endgroup}}

.. tb-reveal:: sort_deck Help
   :name: c192_sorting_reveal_2

   .. tb-parsons::
      :name: c192_sorting_help_2

      Let's write the code for the sort_deck function. We'll use find_lowest_card
      and swap_cards in our implementation of sort_deck.

      .. code-block:: c++

         {{group}}
         void card_deck::sort_deck () {
         {{endgroup}}
         {{distractor}}
         {{group}}
         card_deck::sort_deck () {
         {{endgroup}}
         {{group}}
          for (std::size_t i = 0; i < cards.size(); i++) {
         {{endgroup}}
         {{group}}
           std::size_t x = find_lowest_card (i);
         {{endgroup}}
         {{distractor}}
         {{group}}
           std::size_t x = find_lowest_card (cards.size());
         {{endgroup}}
         {{group}}
           swap_cards (i, x);
          }
         }
         {{endgroup}}

