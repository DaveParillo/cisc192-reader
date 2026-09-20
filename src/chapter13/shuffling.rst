
.. _c192_shuffling:

Shuffling
---------

For most card games you need to be able to shuffle the deck; that is,
put the cards in a random order. In :doc:`../chapter11/random_numbers` we
saw how to generate random numbers, but it is not obvious how to use
them to shuffle a deck.

One possibility is to model the way humans shuffle, which is usually by
dividing the deck in two and then reassembling the deck by choosing
alternately from each deck. Since humans usually don’t shuffle
perfectly, after about 7 iterations the order of the deck is pretty well
randomized. But a computer program would have the annoying property of
doing a perfect shuffle every time, which is not really very random. in
fact, after 8 perfect shuffles, you would find the deck back in the same
order you started in. For a discussion of that claim, see
``http://www.wiskit.com/marilyn/craig.html`` or do a web search with the
keywords “perfect shuffle.”

A better shuffling algorithm is to traverse the deck one card at a time,
and at each iteration choose two cards and swap them.

Here is an outline of how this algorithm works. To sketch the program, I
am using a combination of C++ statements and English words that is
sometimes called **pseudocode**:

::

     for (std::size_t i = 0; i < cards.size(); i++) {
       // choose a random number between i and cards.size() - 1
       // swap the ith card and the randomly-chosen card
     }

The nice thing about using pseudocode is that it often makes it clear
what functions you are going to need. In this case, we need something
like ``random_int``, which chooses a random integer between the
parameters ``low`` and ``high``, and ``swap_cards`` which takes two
indices and switches the cards at the indicated positions.

.. index::
   single: pseudocode

.. note::
   If you are even the slightest bit unsure on how to begin coding
   your program, **pseudocode** is a great place to start!

You can probably figure out how to write ``random_int`` by looking at
:doc:`../chapter11/random_numbers`, although you will have to be careful
about possibly generating indices that are out of range.

You can also figure out ``swap_cards`` yourself. I will leave the
remaining implementation of these functions as an exercise to the
reader.

.. tb-choice::
   :name: shuffling_1

   Which library should we include to create random numbers?

   - [x] cstdlib

     Correct!
   - [ ] iostream

     This is the library for streaming cin and cout.
   - [ ] strings

     This is the library for strings.
   - [ ] cmath

     This is the library for math functions.

The ``random_int`` helper is provided. Write ``swap_cards`` in its commented section, then
try using them to implement the ``card_deck`` member function ``shuffle_deck``. If done correctly,
the program should output a shuffled deck of cards. If you stuck, you can reveal the
extra problems at the end for help.

.. tb-code:: cpp
   :name: c192_shuffling_2-support
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


.. tb-code:: cpp
   :name: c192_shuffling_2
   :caption: Example c192_shuffling_2
   :run-after: c192_shuffling_2-support
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

   std::size_t random_int(std::size_t low, std::size_t high) {
       static std::mt19937 engine(std::random_device{}());
       return std::uniform_int_distribution<std::size_t>{low, high}(engine);
   }

   struct playing_card {
       card_rank rank;
       card_suit suit;
       playing_card ();
       playing_card (card_suit s, card_rank r);
       void print () const;
   };

   struct card_deck {
       std::vector<playing_card> cards;
       card_deck ();
       void print () const;
       void swap_cards (std::size_t index1, std::size_t index2);
       void shuffle_deck ();
   };

   void card_deck::swap_cards (std::size_t index1, std::size_t index2) {
       // ``swap_cards`` should take two indices and switch the cards
       // at the indicated positions. Write your implementation here.
   }

   void card_deck::shuffle_deck () {
       // Follow the pseudocode from above and use ``random_int`` and
       // ``swap_cards`` to write the ``shuffle`` member function.
       // Write your implementation here.
   }

   int main() {
       card_deck deck;
       deck.shuffle_deck ();
       deck.print ();
   }

.. tb-reveal:: random_int Help
   :name: c192_shuffle_reveal_1

   .. tb-parsons::
      :name: c192_shuffling_help_1

      Return a uniformly distributed index between low and high, inclusive. Assume low <= high. Include <random> and <cstddef>.

      .. code-block:: c++

         {{group}}
         std::size_t random_int(std::size_t low, std::size_t high) {
         {{endgroup}}
         {{group}}
             static std::mt19937 engine(std::random_device{}());
         {{endgroup}}
         {{group}}
             std::uniform_int_distribution<std::size_t> distribution(low, high);
         {{endgroup}}
         {{group}}
             return distribution(engine);
         }
         {{endgroup}}

.. tb-reveal:: swap_cards Help
   :name: c192_shuffle_reveal_2

   .. tb-parsons::
      :name: c192_shuffling_help_2

      Let's write the code for the swap_cards function. We'll write swap_cards
      as a card_deck member function that takes two indices as parameters.

      .. code-block:: c++

         {{group}}
         void card_deck::swap_cards (std::size_t index1, std::size_t index2) {
         {{endgroup}}
         {{distractor}}
         {{group}}
         void playing_card::swap_cards (std::size_t index1, std::size_t index2) {
         {{endgroup}}
         {{group}}
          playing_card temp = cards[index1];
         {{endgroup}}
         {{group}}
          cards[index1] = cards[index2];
         {{endgroup}}
         {{distractor}}
         {{group}}
          cards[index2] = cards[index1];
         {{endgroup}}
         {{group}}
          cards[index2] = temp;
         }
         {{endgroup}}

.. tb-reveal:: shuffle_deck Help
   :name: c192_shuffle_reveal_3

   .. tb-parsons::
      :name: c192_shuffling_help_3

      Let's write the code for the shuffle_deck function. We'll use random_int
      and swap_cards in our implementation of shuffle_deck.

      .. code-block:: c++

         {{group}}
         void card_deck::shuffle_deck () {
         {{endgroup}}
         {{distractor}}
         {{group}}
         card_deck card_deck::shuffle_deck (card_deck deck) {
         {{endgroup}}
         {{group}}
          for (std::size_t i = 0; i < cards.size(); i++) {
         {{endgroup}}
         {{group}}
           std::size_t x = random_int (i, cards.size() - 1);
         {{endgroup}}
         {{distractor}}
         {{group}}
           std::size_t x = random_int (i, cards.size());
         {{endgroup}}
         {{group}}
           swap_cards (i, x);
          }
         }
         {{endgroup}}

