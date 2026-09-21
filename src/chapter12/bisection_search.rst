.. _vectors-objects-bisection-search:

Bisection search
----------------

If the cards in the deck are not in order, there is no way to search
that is faster than the linear search. We have to look at every card,
since otherwise there is no way to be certain the card we want is not
there.

.. index::
   single: bisection search

But when you look for a word in a dictionary, you don’t search linearly
through every word. The reason is that the words are in alphabetical
order. As a result, you probably use an algorithm that is similar to a
**bisection search**:

#. Start in the middle somewhere.

#. Choose a word on the page and compare it to the word you are looking
   for.

#. If you found the word you are looking for, stop.

#. If the word you are looking for comes after the word on the page,
   flip to somewhere later in the dictionary and go to step 2.

#. If the word you are looking for comes before the word on the page,
   flip to somewhere earlier in the dictionary and go to step 2.

If you ever get to the point where there are two adjacent words on the
page and your word comes between them, you can conclude that your word
is not in the dictionary. The only alternative is that your word has
been misfiled somewhere, but that contradicts our assumption that the
words are in alphabetical order.

In the case of a deck of cards, if we know that the cards are in order,
we can write a version of ``find`` that is much faster. The best way to
write a bisection search is with a recursive function. That’s because
bisection is naturally recursive.

The trick is to write a function called ``find_bisect`` that takes two
indices as parameters, ``low`` and ``high``, indicating the segment of
the vector that should be searched (including both ``low`` and
``high``).

#. To search the vector, choose an index between ``low`` and ``high``,
   and call it ``mid``. compare the card at ``mid`` to the card you are
   looking for.

#. If you found it, stop.

#. If the card at ``mid`` is higher than your card, search in the range
   from ``low`` to ``mid-1``.

#. If the card at ``mid`` is lower than your card, search in the range
   from ``mid+1`` to ``high``.

Steps 3 and 4 look suspiciously like recursive invocations. Here’s what
this all looks like translated into C++:

::

   std::ptrdiff_t find_bisect (const playing_card& card, const std::vector<playing_card>& deck,
                   std::ptrdiff_t low, std::ptrdiff_t high) {
     std::ptrdiff_t mid = low + (high - low) / 2;

     // if we found the card, return its index
     if (equals (deck[mid], card)) return mid;

     // otherwise, compare the card to the middle card
     if (deck[mid].is_greater (card)) {
       // search the first half of the deck
       return find_bisect (card, deck, low, mid-1);
     } else {
       // search the second half of the deck
       return find_bisect (card, deck, mid+1, high);
     }
   }

Although this code contains the kernel of a bisection search, it is
still missing a piece. As it is currently written, if the card is not in
the deck, it will recurse forever. We need a way to detect this
condition and deal with it properly (by returning ``-1``).

The easiest way to tell that your card is not in the deck is if there
are *no* cards in the deck, which is the case if ``high`` is less than
``low``. Well, there are still cards in the deck, of course, but what I
mean is that there are no cards in the segment of the deck indicated by
``low`` and ``high``.

With that line added, the function works correctly:

::

   std::ptrdiff_t find_bisect (const playing_card& card, const std::vector<playing_card>& deck,
                   std::ptrdiff_t low, std::ptrdiff_t high) {

     std::cout << low << ", " << high << '\n';

     if (high < low) return -1;

     std::ptrdiff_t mid = low + (high - low) / 2;

     if (equals (deck[mid], card)) return mid;

     if (deck[mid].is_greater (card)) {
       return find_bisect (card, deck, low, mid-1);
     } else {
       return find_bisect (card, deck, mid+1, high);
     }
   }

I added an output statement at the beginning so I could watch the
sequence of recursive calls and convince myself that it would eventually
reach the base case. I tried out the following code:

::

     std::cout << find_bisect (deck[23], deck, 0, 51);

And got the following output:

::

   0, 51
   0, 24
   13, 24
   19, 24
   22, 24
   I found the card at index = 23

Then I made up a card that is not in the deck (the 15 of Diamonds), and
tried to find it. I got the following:

::

   0, 51
   0, 24
   13, 24
   13, 17
   13, 14
   13, 12
   I found the card at index = -1

These tests don’t prove that this program is correct. In fact, no amount
of testing can prove that a program is correct. On the other hand, by
looking at a few cases and examining the code, you might be able to
convince yourself.

The code below searches finds the same card from the same deck we used on the previous page.
This time, it uses bisection search to locate the card.

.. tb-code:: cpp
   :name: c192_12_9-support
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

    void print_deck (const std::vector<playing_card>& deck) {
      for (std::size_t i = 0; i < deck.size(); i++) {
        deck[i].print ();
      }
    }

   std::ptrdiff_t find (const playing_card& card, const std::vector<playing_card>& deck) {
      for (std::size_t i = 0; i < deck.size(); i++) {
       if (equals (deck[i], card)) return static_cast<std::ptrdiff_t>(i);
      }
      return -1;
   }

   std::ptrdiff_t find_bisect (const playing_card& card, const std::vector<playing_card>& deck, std::ptrdiff_t low, std::ptrdiff_t high) {

      std::cout << low << ", " << high << '\n';

      if (high < low) return -1;

      std::ptrdiff_t mid = low + (high - low) / 2;

      if (equals (deck[mid], card)) return mid;

      if (deck[mid].is_greater (card)) {
         return find_bisect (card, deck, low, mid-1);
      } else {
         return find_bisect (card, deck, mid+1, high);
      }
   }
   bool playing_card::is_greater (const playing_card& c2) const {
     if (m_suit > c2.m_suit) return true;
     if (m_suit < c2.m_suit) return false;

     if (m_rank > c2.m_rank) return true;
     if (m_rank < c2.m_rank) return false;

     return false;
   }


.. tb-code:: cpp
   :name: c192_12_9
   :caption: Example c192_12_9
   :run-after: c192_12_9-support

   #include <iterator>
   #include <cstddef>
   #include <iostream>
   #include <string>
   #include <vector>

   struct playing_card {
       int m_suit, m_rank;

       playing_card ();
       playing_card (int s, int r);
       void print () const;
       bool is_greater (const playing_card& c2) const;
   };

   std::vector<playing_card> build_deck();

   bool equals (const playing_card& c1, const playing_card& c2){
       return (c1.m_rank == c2.m_rank && c1.m_suit == c2.m_suit);
   }

   void print_deck(const std::vector<playing_card>& deck);
   std::ptrdiff_t find (const playing_card& card, const std::vector<playing_card>& deck);
   std::ptrdiff_t find_bisect (const playing_card& card, const std::vector<playing_card>& deck, std::ptrdiff_t low, std::ptrdiff_t high);

   int main() {
       std::vector<playing_card> deck = build_deck();
       playing_card card (3, 6);
       // We need to sort from the first card (0) to the last card (size-1)
       std::cout << find_bisect(card, deck, 0, std::ssize(deck) - 1);
   }

The number of recursive calls is fairly small, typically 6 or 7. That
means we only had to call ``equals`` and ``is_greater`` 6 or 7 times,
compared to up to 52 times if we did a linear search. In general,
bisection is much faster than a linear search, especially for large
vectors.

Two common errors in recursive programs are forgetting to include a base
case and writing the recursive call so that the m_base case is never
reached. Either error will cause an infinite recursion, in which case
C++ will (eventually) generate a run-time error.

.. tb-choice::
   :name: bisection_search_1

   You are given a list of spelling words where the words are **not sorted** in any way.
   What search method should you use?

   - [x] linear search

     Correct! No search is faster than linear search when elements are not sorted.
   - [ ] bisection search

     Incorrect! Bisection sort does not work on unsorted elements.
   - [ ] both methods will work, but linear search is more efficient

     Incorrect! Bisection sort does not work on unsorted elements.
   - [ ] both methods will work, but bisection search is more efficient

     Incorrect! Bisection sort does not work on unsorted elements.

.. tb-choice::
   :name: bisection_search_2

   You are given the same list of spelling words, but this time the words are **sorted alphabetically**.
   What search method should you use this time?

   - [ ] linear search

     Incorrect! You could use linear search, but it is not the only option.
   - [ ] bisection search

     Incorrect! You could use bisection search, but it is not the only option.
   - [ ] both methods will work, but linear search is more efficient

     Incorrect! Both methods will work, but linear search is not the most efficient method.
   - [x] both methods will work, but bisection search is more efficient

     Correct! When elements are sorted, bisection search is much quicker.

.. tb-choice::
   :name: bisection_search_3

   When writing a recursive function, which of the following will result in infinite recursion?

   - [ ] having more than one recursive call

     Incorrect! You are allowed to make multiple recursive calls inside of a function! You might do this if there is more than one condition.
   - [x] not including a base case

     Correct! You always need a base case!
   - [x] writing recursive calls such that the base case is never reached

     Correct! If you never reach the base case, the program will never stop making recursive calls.
   - [ ] having more than one base case

     Incorrect! You are allowed to have multiple base cases. This is often necessary!

.. tb-blank::
   :name: c192_bisection_search_4

   How many recursive calls are used to locate the King of Hearts? (Hearts = suit 2, King = rank 13).

   {{blank}}

   .. tb-answer::
      :match: 2
      :feedback: Correct!
      :match: x

