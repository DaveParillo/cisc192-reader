Private data and classes
------------------------

.. index::
   single: encapsulation
   single: function encapsulation

I have used the word **encapsulation** in this book to refer to the
process of wrapping up a sequence of instructions in a function, in
order to separate the function’s interface (how to use it) from its
implementation (how it does what it does).

.. index::
   single: data encapsulation

This kind of encapsulation might be called “functional encapsulation,”
to distinguish it from “data encapsulation,” which is the topic of this
chapter. Data encapsulation is based on the idea that each structure
definition should provide a set of functions that apply to the
structure, and prevent unrestricted access to the internal
representation.

One use of data encapsulation is to hide implementation details from
users or programmers that don’t need to know them.

For example, there are many possible representations for a ``playing_card``,
including two integers, two strings and two enumerated types. The
programmer who writes the ``playing_card`` member functions needs to know which
implementation to use, but someone using the ``playing_card`` structure should
not have to know anything about its internal structure.

As another example, we have been using ``string`` and ``vector``
objects without ever discussing their implementations. There are many
possibilities, but as “clients” of these libraries, we don’t need to
know.

In C++, the most common way to enforce data encapsulation is to prevent
client programs from accessing the instance variables of an object. The
keyword ``private`` is used to protect parts of a structure definition.
For example, we could have written the ``playing_card`` definition:

::

   struct playing_card
   {
   private:
     int suit, rank;

   public:
     playing_card ();
     playing_card (int s, int r);

     int get_rank () const { return rank; }
     int get_suit () const { return suit; }
     void set_rank (int r) { rank = r; }
     void set_suit (int s) { suit = s; }
   };

.. index::
   single: private

.. index::
   single: public

There are two sections of this definition, a **private** part and a **public**
part. The functions are public, which means that they can be invoked by
client programs. The instance variables are private, which means that
they can be read and written only by ``playing_card`` member functions.

.. index::
   single: accessor function

It is still possible for client programs to read and write the instance
variables using the **accessor functions** (the ones beginning with
``get`` and ``set``). On the other hand, it is now easy to control which
operations clients can perform on which instance variables. For example,
it might be a good idea to make cards “read only” so that after they are
constructed, they cannot be changed. To do that, all we have to do is
remove the ``set`` functions.

Another advantage of using accessor functions is that we can change the
internal representations of cards without having to change any client
programs.

Run the active code below. Uncomment the commented out code to see what happens!

.. tb-code:: cpp
   :name: c192_priv_data_ac_1-support
   :hidden:
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   playing_card::playing_card () {
       suit = 3;  rank = 0;
   }

   playing_card::playing_card (int s, int r) {
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


.. tb-code:: cpp
   :name: c192_priv_data_ac_1
   :caption: Example c192_priv_data_ac_1
   :run-after: c192_priv_data_ac_1-support
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <iostream>
   #include <string>
   #include <vector>

   struct playing_card {
       private:
           int suit, rank;
       public:
           playing_card ();
           playing_card (int s, int r);
           int get_rank () const { return rank; }
           int get_suit () const { return suit; }
           void set_rank (int r) { rank = r; }
           void set_suit (int s) { suit = s; }
           void print () const;
   };

   int main() {
       playing_card card (3, 8);
       card.print();
       std::cout << "card_rank: " << card.get_rank() << "    card_suit: " << card.get_suit() << std::endl;
       card.set_rank(12);
       card.set_suit(2);
       card.print();
       std::cout << "card_rank: " << card.get_rank() << "    card_suit: " << card.get_suit() << std::endl;

       // If you uncomment the following code, you'll get an error! We cannot directly
       // access the private data members of playing_card, which is why we use accessor functions.

       /*
       cout << "card_rank: " << card.rank << "\t card_suit: " << card.suit << endl;
       card.rank = 4;
       card.suit = 0;
       */
   }

.. tb-choice::
   :name: c192_question14_1_1




   - [ ] True

     Incorrect! Data encapsulation should hide implementation details.
   - [x] False

     Correct! Data encapsulation prevents unrestricted access to internal representations.

.. tb-blank::
   :name: c192_question14_1_2

   What type of data member cannot be directly accessed outside of the structure?

   {{blank}}

   .. tb-answer::
      :match: (Pp)rivate||((Pp)rivate (Dd)ata (Mm)ember)
      :feedback: Correct!
      :incorrect: Incorrect! Try again.

.. tb-choice::
   :name: c192_question14_1_3


   - [x] get_suit

     Correct!
   - [x] set_rank

     Correct! "Setter" functions are also known as "mutator" functions.
   - [ ] print

     Incorrect!
   - [x] get_rank

     Correct!

