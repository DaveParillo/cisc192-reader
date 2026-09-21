.. _objects-vectors-mergesort:

Mergesort
---------

In :numref:`c192_sorting`, we saw a simple sorting algorithm that
turns out not to be very efficient. In order to sort :math:`n` items, it
has to traverse the vector :math:`n` times, and each traversal takes an
amount of time that is proportional to :math:`n`. The total time,
therefore, is proportional to :math:`n^2`.

.. index::
   single: mergesort

In this section I will sketch a more efficient algorithm called
**mergesort**. To sort :math:`n` items, mergesort takes time
proportional to :math:`n \log n`. That may not seem impressive, but as
:math:`n` gets big, the difference between :math:`n^2` and
:math:`n \log n` can be enormous. Try out a few values of :math:`n` and
see.

The basic idea behind mergesort is this: if you have two subdecks, each
of which has been sorted, it is easy (and fast) to merge them into a
single, sorted deck. Try this out with a deck of cards:

#. Form two subdecks with about 10 cards each and sort them so that when
   they are face up the lowest cards are on top. Place both decks face
   up in front of you.

#. compare the top card from each deck and choose the lower one. Flip it
   over and add it to the merged deck.

#. Repeat step two until one of the decks is empty. Then take the
   remaining cards and add them to the merged deck.

The result should be a single sorted deck. Here’s what this looks like
In pseudocode:

::

     card_deck merge (const card_deck& d1, const card_deck& d2) {
       // create a new deck big enough for all the cards
       card_deck result (d1.cards.size() + d2.cards.size());

       // use the index i to keep track of where we are in
       // the first deck, and the index j for the second deck
       std::size_t i = 0;
       std::size_t j = 0;

       // the index k traverses the result deck
       for (std::size_t k = 0; k<result.cards.size(); k++) {

         // if d1 is empty, d2 wins; if d2 is empty, d1 wins;
         // otherwise, compare the two cards

         // add the winner to the new deck
       }
       return result;
     }

I chose to make ``merge`` a nonmember function because the two arguments
are symmetric.

The best way to test ``merge`` is to build and shuffle a deck, use
subdeck to form two (small) hands, and then use the sort routine from
the previous chapter to sort the two halves. Then you can pass the two
halves to ``merge`` to see if it works.

If you can get that working, try a simple implementation of
``merge_sort``:

::

   card_deck card_deck::merge_sort () const {
     // find the midpoint of the deck
     // divide the deck into two subdecks
     // sort the subdecks using sort
     // merge the two halves and return the result
   }

Notice that the current object is declared ``const`` because
``merge_sort`` does not modify it. Instead, it creates and returns a new
``card_deck`` object.

If you get that version working, the real fun begins! The magical thing
about mergesort is that it is recursive. At the point where you sort the
subdecks, why should you invoke the old, slow version of ``sort``? Why
not invoke the spiffy new ``merge_sort`` you are in the process of
writing?

Not only is that a good idea, it is *necessary* in order to achieve the
performance advantage I promised. In order to make it work, though, you
have to add a base case so that it doesn’t recurse forever. A simple
base case is a subdeck with 0 or 1 cards. If ``mergesort`` receives such
a small subdeck, it can return it unmodified, since it is already
sorted.

The recursive version of ``mergesort`` should look something like this:

::

   card_deck card_deck::merge_sort (card_deck deck) const {
     // if the deck is 0 or 1 cards, return it

     // find the midpoint of the deck
     // divide the deck into two subdecks
     // sort the subdecks using mergesort
     // merge the two halves and return the result
   }

As usual, there are two ways to think about recursive programs: you can
think through the entire flow of execution, or you can make the “leap of
faith.” I have deliberately constructed this example to encourage you to
make the leap of faith.

When you were using ``sort`` to sort the subdecks, you didn’t feel
compelled to follow the flow of execution, right? You just assumed that
the ``sort`` function would work because you already debugged it. Well,
all you did to make ``merge_sort`` recursive was replace one sort
algorithm with another. There is no reason to read the program
differently.

Well, actually you have to give some thought to getting the base case
right and making sure that you reach it eventually, but other than that,
writing the recursive version should be no problem. Good luck!


.. tb-choice::
   :name: mergesort_1

   The efficiency of a simple sorting algorithm is __________.  The
   efficiency of mergesort is __________.  Mergesort is __________ than
   the simple sorting algorithm.


   - [ ] n, nlogn, more efficient

     Simple sort traverses the vector n times, and each traversal takes additional time.
   - [x] n^2, nlogn, more efficient

     Simple sort takes time proporitonal to n^2, mergesort takes time proportional to nlogn (which is more efficient).
   - [ ] nlogn, n, less efficient

     You might be confused about which algorithm is which.  Also, what is the efficiency of simple sort?
   - [ ] nlogn, n^2, less efficient

     You might be confused about which algorithm is which.
   - [ ] n^2, nlogn, less efficient

     Which algorithm is more efficient? (Which function grows more slowly?)

Write your implementation of ``merge`` in the commented area of the active
code below. Read the comments in ``main`` to see how we'll test if your
``merge`` function works. If you get stuck, you can reveal the extra problem
at the end for help.

.. tb-code:: cpp
   :name: c192_mergesort_2-support
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
   :name: c192_mergesort_2
   :caption: Example c192_mergesort_2
   :run-after: c192_mergesort_2-support

   #include <stdexcept>
   #include <iterator>
   #include <cstddef>
   #include <random>
   #include <iostream>
   #include <string>
   #include <vector>
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

   card_deck merge (const card_deck& d1, const card_deck& d2) {
       // ``merge`` should merge d1 with d2 and return
       // a merged deck. Follow the pseudocode above,
       // delete the existing code, and write your
       // implementation here.
       card_deck deck(0); return deck;
   }

   int main() {
       card_deck deck;

       // Shuffle a deck of cards and split it in half
       deck.shuffle_deck();
       card_deck d1 = deck.subdeck(0, 25);
       card_deck d2 = deck.subdeck(26, 51);

       // Sort each half
       d1.sort_deck();
       d2.sort_deck();
       cout << "Sorted first half:" << '\n';
       d1.print();
       cout << '\n';
       cout << "Sorted second half:" << '\n';
       d2.print();
       cout << '\n';

       // Merge sorted decks together
       card_deck finished = merge(d1, d2);

       // We should see a sorted standard deck of 52 cards
       cout << "Merged sorted full deck:" << '\n';
       finished.print();
   }

.. tb-reveal:: merge Help
   :name: c192_mergesort_reveal_1

   .. tb-parsons::
      :name: c192_mergesort_help_1

      First, let's write the code for the merge function. merge should
      take two decks as parameters and return a deck with the deck merged.

      .. code-block:: c++

         {{group}}
         card_deck merge (const card_deck& d1, const card_deck& d2) {
         {{endgroup}}
         {{distractor}}
         {{group}}
         void merge (const card_deck& d1, const card_deck& d2) {
         {{endgroup}}
         {{group}}
          card_deck result (d1.cards.size() + d2.cards.size());
         {{endgroup}}
         {{group}}
          std::size_t i = 0;
          std::size_t j = 0;
         {{endgroup}}
         {{group}}
          for (std::size_t k = 0; k < result.cards.size(); ++k) {
         {{endgroup}}
         {{group}}
           if (d1.cards.empty()) {
            result.cards[k] = d2.cards[j];
            ++j;
           }
         {{endgroup}}
         {{distractor}}
         {{group}}
           if (d1.cards.empty()) {
            result.cards[k] = d1.cards[i];
            ++i;
           }
         {{endgroup}}
         {{group}}
           else if (d2.cards.empty()) {
            result.cards[k] = d1.cards[i];
            ++i;
           }
         {{endgroup}}
         {{distractor}}
         {{group}}
           else if (d1.cards.empty()) {
            result.cards[k] = d2.cards[j];
            ++j;
           }
         {{endgroup}}
         {{group}}
           else {
         {{endgroup}}
         {{group}}
            if (j >= d2.cards.size()) {
             result.cards[k] = d1.cards[i];
             ++i;
            }
         {{endgroup}}
         {{group}}
            else if (i >= d1.cards.size() || d1.cards[i].is_greater(d2.cards[j])) {
             result.cards[k] = d2.cards[j];
             ++j;
            }
         {{endgroup}}
         {{group}}
            else {
             result.cards[k] = d1.cards[i];
             ++i;
            }
           }
         {{endgroup}}
         {{group}}
          }
          return result;
         }
         {{endgroup}}

Now that we've written ``merge``, it's time to write the ``merge_sort`` function. Try writing
the non-recursive version of ``merge_sort`` first before writing the recursive version. Follow the
comments in ``main`` to test your functions. If done correctly, the program should output a sorted
deck of cards. If you get stuck, you can reveal the extra problems at the end for help.

.. tb-code:: cpp
   :name: c192_mergesort_3-support
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

   card_deck merge (const card_deck& d1, const card_deck& d2) {
       card_deck result (d1.cards.size() + d2.cards.size());
       std::size_t i = 0;
       std::size_t j = 0;
       for (std::size_t k = 0; k < result.cards.size(); ++k) {
           if (d1.cards.empty()) {
               result.cards[k] = d2.cards[j];
               ++j;
           }
           else if (d2.cards.empty()) {
               result.cards[k] = d1.cards[i];
               ++i;
           }
           else {
               if (j >= d2.cards.size()) {
                   result.cards[k] = d1.cards[i];
                   ++i;
               }
               else if (i >= d1.cards.size() || d1.cards[i].is_greater(d2.cards[j])) {
                   result.cards[k] = d2.cards[j];
                   ++j;
               }
               else {
                   result.cards[k] = d1.cards[i];
                   ++i;
               }
           }
       }
       return result;
   }


.. tb-code:: cpp
   :name: c192_mergesort_3
   :caption: Example c192_mergesort_3
   :run-after: c192_mergesort_3-support

   #include <stdexcept>
   #include <iterator>
   #include <cstddef>
   #include <random>
   #include <iostream>
   #include <string>
   #include <vector>

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
       card_deck merge_sort () const;
       card_deck merge_sort (card_deck deck) const;
   };

   std::ptrdiff_t find_bisect (card_deck subdeck, playing_card card);
   card_deck merge (const card_deck& d1, const card_deck& d2);

   card_deck card_deck::merge_sort () const {
       // This version of ``merge_sort`` is the non-recursive version.
       // Follow the pseudocode above delete the existing code,
       // and write your implementation here.
       card_deck deck(0); return deck;
   }

   card_deck card_deck::merge_sort (card_deck deck) const {
       // This version of ``merge_sort`` is the recursive version.
       // Follow the pseudocode above delete the existing code,
       // and write your implementation here.
       card_deck deck1(0); return deck;
   }

   int main() {
       card_deck deck1;
       deck1.shuffle_deck();
       card_deck sorted1 = deck1.merge_sort();
       sorted1.print();

       // Once you get the above code to work, comment it
       // out and uncomment the code below to test the
       // recursive version of ``merge_sort``.

       /*
       card_deck deck2;
       deck2.shuffle_deck();
       card_deck sorted2 = deck2.merge_sort(deck2);
       sorted2.print();
       */
   }

.. tb-reveal:: merge_sort Help
   :name: c192_mergesort_reveal_2

   .. tb-parsons::
      :name: c192_mergesort_help_2

      Let's write the code for the merge_sort function. merge_sort
      should be a card_deck member function that returns a sorted deck.

      .. code-block:: c++

         {{group}}
         card_deck card_deck::merge_sort () const {
         {{endgroup}}
         {{distractor}}
         {{group}}
         card_deck merge_sort () {
         {{endgroup}}
         {{group}}
          std::ptrdiff_t mid = std::ssize(cards) / 2;
         {{endgroup}}
         {{group}}
          card_deck d1 = subdeck(0, mid - 1);
          card_deck d2 = subdeck(mid, std::ssize(cards) - 1);
         {{endgroup}}
         {{group}}
          d1.sort_deck();
          d2.sort_deck();
         {{endgroup}}
         {{group}}
          return merge(d1, d2);
         }
         {{endgroup}}

.. tb-reveal:: merge_sort Recursion Help
   :name: c192_mergesort_reveal_3

   .. tb-parsons::
      :name: c192_mergesort_help_3

      Let's take it one step further and rewrite ``merge_sort`` as a
      recursive function.

      .. code-block:: c++

         {{group}}
         card_deck card_deck::merge_sort (card_deck deck) const {
         {{endgroup}}
         {{group}}
          if (deck.cards.size() == 0 || deck.cards.size() == 1) {
           return deck;
          }
         {{endgroup}}
         {{group}}
          std::ptrdiff_t mid = std::ssize(deck.cards) / 2;
         {{endgroup}}
         {{group}}
          card_deck d1 = subdeck(0, mid - 1);
          card_deck d2 = subdeck(mid, std::ssize(deck.cards) - 1);
         {{endgroup}}
         {{group}}
          card_deck merged1 = d1.merge_sort(d1);
          card_deck merged2 = d2.merge_sort(d2);
         {{endgroup}}
         {{group}}
          return merge(merged1, merged2);
         }
         {{endgroup}}

