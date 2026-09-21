.. _vectors-objects-the-print-deck-function:
.. _c192_printdeck:

The ``print_deck`` function
---------------------------

Whenever you are working with vectors, it is convenient to have a
function that prints the contents of the vector. We have seen the
pattern for traversing a vector several times, so the following function
should be familiar:

::

   void print_deck (const std::vector<playing_card>& deck) {
     for (std::size_t i = 0; i < deck.size(); i++) {
       deck[i].print ();
     }
   }

By now it should come as no surprise that we can compose the syntax for
vector access with the syntax for invoking a function.

Since ``deck`` has type ``vector<playing_card>``, an element of ``deck`` has
type ``playing_card``. Therefore, it is legal to invoke ``print`` on
``deck[i]``.

A Euchre card_deck contains 9's, 10's, Jacks, Queens, Kings, and Aces of all four suits.
Modify the ``build_deck`` function below to create a Euchre deck. The ``print_deck``
function will allow you to verify that you have done this correctly.

.. tb-code:: cpp
   :name: c192_12_7-support
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


.. tb-code:: cpp
   :name: c192_12_7
   :caption: Example c192_12_7
   :run-after: c192_12_7-support

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

   void print_deck(const std::vector<playing_card>& deck);

   int main() {
       std::vector<playing_card> deck = build_deck();
       print_deck(deck);
   }

Hopefully you took some time to try and figure out the code yourself.  The solution
below is just one of several correct solutions for creating the Euchre deck:

::

  std::vector<playing_card> build_euchre_deck() {
    std::vector<playing_card> deck (24);
    std::size_t i = 0;
    for (int m_suit = 0; m_suit <= 3; m_suit++) {
        for (int m_rank = 1; m_rank <= 13; m_rank++) {
          if (m_rank == 1 || m_rank >= 9){
            deck[i].m_suit = m_suit;
            deck[i].m_rank = m_rank;
            i++;
          }
        }
    }
    return deck;
  }

