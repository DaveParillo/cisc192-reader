.. _vectors-objects-the-isgreater-function:

The ``is_greater`` function
---------------------------

For basic types like ``int`` and ``double``, there are comparison
operators that compare values and determine when one is greater or less
than another. These operators (``<`` and ``>`` and the others) don’t
work for user-defined types. Just as we did for the ``==`` operator, we
will write a comparison function that plays the role of the ``>``
operator. Later, we will use this function to sort a deck of cards.

Some sets are totally ordered, which means that you can compare any two
elements and tell which is bigger. For example, the integers and the
floating-point numbers are totally ordered. Some sets are unordered,
which means that there is no meaningful way to say that one element is
bigger than another. For example, the fruits are unordered, which is why
we cannot compare apples and oranges. As another example, the ``bool``
type is unordered; we cannot say that ``true`` is greater than
``false``.

The set of playing cards is partially ordered, which means that
sometimes we can compare cards and sometimes not. For example, I know
that the 3 of Clubs is higher than the 2 of Clubs because it has higher
rank, and the 3 of Diamonds is higher than the 3 of Clubs because it has
higher suit. But which is better, the 3 of Clubs or the 2 of Diamonds?
One has a higher rank, but the other has a higher suit.

In order to make cards comparable, we have to decide which is more
important, rank or suit. To be honest, the choice is completely
arbitrary. For the sake of choosing, I will say that suit is more
important, because when you buy a new deck of cards, it comes sorted
with all the Clubs together, followed by all the Diamonds, and so on.

With that decided, we can write ``is_greater``. Again, the arguments (two
``playing_card``\ s) and the return type (boolean) are obvious, and again we
have to choose between a member function and a nonmember function. This
time, the arguments are not symmetric. It matters whether we want to
know “Is A greater than B?” or “Is B greater than A?” Therefore I think
it makes more sense to write ``is_greater`` as a member function:

::

   bool playing_card::is_greater (const playing_card& c2) const {
     // first check the suits
     if (m_suit > c2.m_suit) return true;
     if (m_suit < c2.m_suit) return false;

     // if the suits are equal, check the ranks
     if (m_rank > c2.m_rank) return true;
     if (m_rank < c2.m_rank) return false;

     // if the ranks are also equal, return false
     return false;
   }

Then when we invoke it, it is obvious from the syntax which of the two
possible questions we are asking:

::

     playing_card card1 (2, 10);
     playing_card card2 (2, 4);

     if (card1.is_greater (card2)) {
       card1.print ();
       std::cout << "is greater than" << '\n';
       card2.print ();
     }

You can almost read it like English: “If card1 is_greater card2 ...” The
output of this program is

::

   10 of Hearts
   is greater than
   4 of Hearts

According to ``is_greater``, aces are less than deuces (2s). As an
exercise, fix it so that aces are ranked higher than Kings, as they are
In most card games.

Take a look at the active code below, which uses the ``is_greater`` function.
Feel free to change the values of the cards.

.. tb-code:: cpp
   :name: c192_12_5-support
   :hidden:


   playing_card::playing_card () {
     m_suit = 0;  m_rank = 1;
   }

   playing_card::playing_card (int s, int r) {
     m_suit = s;  m_rank = r;
   }

   bool playing_card::equals (const playing_card& c2) const {
     bool boolean = (m_rank == c2.m_rank && m_suit == c2.m_suit);
     if (boolean == true) {
       cout << "Yup, that's the same card." << '\n';
     }
     else {
       cout << "Nope, those cards are different." << '\n';
     }
     return boolean;
   }

   bool playing_card::is_greater (const playing_card& c2) const {
     if (m_suit > c2.m_suit) return true;
     if (m_suit < c2.m_suit) return false;

     if (m_rank > c2.m_rank) return true;
     if (m_rank < c2.m_rank) return false;

     return false;
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


.. tb-code:: cpp
   :name: c192_12_5
   :caption: Example c192_12_5
   :run-after: c192_12_5-support

   #include <iostream>
   #include <string>
   #include <vector>
   using std::cout;

   struct playing_card {
       int m_suit, m_rank;

       playing_card ();
       playing_card (int s, int r);
       void print () const;
       bool equals (const playing_card& c2) const;
       bool is_greater (const playing_card& c2) const;
   };

   int main() {
       playing_card card1 (2,10);
       playing_card card2 (2,4);
       if (card1.is_greater (card2)) {
           card1.print ();
           cout << "is greater than" << '\n';
           card2.print ();
       }
       else {
           card2.print ();
           cout << "is greater than" << '\n';
           card1.print ();
       }
   }

.. tb-choice::
   :name: is_greater_function_1

   Select all **totally ordered** sets.

   - [ ] bool

     Incorrect! We cannot say true is greater than false, or vice versa.
   - [x] string

     Correct! Strings are ordered lexiographically.
   - [x] int

     Correct! It is quite obvious how integers are ordered.
   - [ ] Animal

     Incorrect! We cannot say that one animal is greater than another.
   - [ ] card

     Incorrect! Cards are partially ordered.

.. tb-blank::
   :name: c192_is_greater_function_2

   ::

    playing_card card1 (2,12);
    playing_card card2 (1,12);
    if (card1.is_greater (card2)) {
       card1.print ();
       std::cout << "is greater than" << '\n';
       card2.print ();
    }
    else {
       card2.print ();
       std::cout << "is greater than" << '\n';
       card1.print ();
    }
   
   If the above code is run, the terminal will print:
   "Queen of Hearts"
   {{blank}}
   "Queen of Diamonds"
   Type your answer exactly as it would appear in the terminal.

   .. tb-answer::
      :match: is greater than
      :feedback: Correct!
      :incorrect: Incorrect!  Try this input on the code above!
