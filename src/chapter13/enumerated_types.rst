Enumerated types
----------------

In the previous chapter I talked about mappings between real-world
values like rank and suit, and internal representations like integers
and strings. Although we created a mapping between ranks and integers,
and between suits and integers, I pointed out that the mapping itself
does not appear as part of the program.

.. index::
   single: enumerated type

Actually, C++ provides a feature called an **enumerated type** that
makes it possible to (1) include a mapping as part of the program, and
(2) define the set of values that make up the mapping. For example, here
is the definition of the enumerated types ``card_suit`` and ``card_rank``:

::

   enum card_suit { clubs, diamonds, hearts, spades };

   enum card_rank { ace = 1, two, three, four, five, six, seven, eight, nine,
   ten, jack, queen, king };

.. note::
   By default, the first value in the enumerated type maps to 0, the
   second to 1, and so on.

Within the ``card_suit`` type, the value ``clubs`` is represented by the integer
0, ``diamonds`` is represented by 1, etc.

The definition of ``card_rank`` overrides the default mapping and specifies
that ``ace`` should be represented by the integer 1. The other values
follow in the usual way.

Once we have defined these types, we can use them anywhere. For example,
the instance variables ``rank`` and ``suit`` can be declared with
type ``card_rank`` and ``card_suit``:

::

   struct playing_card {
     card_rank rank;
     card_suit suit;

     playing_card (card_suit s, card_rank r);
   };

The types of the parameters for the constructor have changed, too.
Now, to create a card, we can use the values from the enumerated type as
arguments:

::

     playing_card card (diamonds, jack);

We use snake_case for enumerator names, just as for other identifiers.
Named values communicate more than bare integers. The following call worked
with the previous integer-based constructor, but does not compile with the
new enumerated parameter types:

::

     playing_card card (1, 11);

The active code below uses the enumerated types created above to construct ``playing_card`` objects.
Feel free to modify the values that the cards are being initialized to in the constructor:  this will
change the output from the ``print`` function. Notice how this is much clearer than using integers.

.. tb-code:: cpp
   :name: c192_enum_type_ac_1-support
   :hidden:
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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


.. tb-code:: cpp
   :name: c192_enum_type_ac_1
   :caption: Example c192_enum_type_ac_1
   :run-after: c192_enum_type_ac_1-support
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <iostream>
   #include <string>
   #include <vector>

   enum card_suit { clubs, diamonds, hearts, spades };

   enum card_rank { ace=1, two, three, four, five, six, seven, eight, nine,
   ten, jack, queen, king };

   struct playing_card {
       card_rank rank;
       card_suit suit;
       playing_card (card_suit s, card_rank r);
       void print () const;
   };

   int main() {
       playing_card card1 (diamonds, jack);
       card1.print ();
       playing_card card2 (hearts, queen);
       card2.print ();
       playing_card card3 (clubs, three);
       card3.print ();
   }

Because we know that the values in the enumerated types are represented
as integers, we can use them as indices for a vector. Therefore the old
``print`` function will work without modification. We have to make some
changes in ``build_deck``, though:

::

     std::size_t index = 0;
     for (int suit = clubs; suit <= spades; ++suit) {
       for (int rank = ace; rank <= king; ++rank) {
         deck[index].suit = static_cast<card_suit>(suit);
         deck[index].rank = static_cast<card_rank>(rank);
         index++;
       }
     }

The loop counters are integers. Each value is checked against the last
valid enumerator before it is converted with ``static_cast``. This avoids
creating an out-of-range enum when the loop advances past the final suit.
An unscoped enum can convert to an integer in an expression such as
``suit + 1``, but ``++`` is not defined for it automatically.

.. tb-choice::
   :name: enum_type_1

   Multiple Response: What can we do with enumerated types?


   - [ ] Perform arithmetic.

     We are not allowed to do arithmetic with enumerated types.
   - [x] Include a mapping as part of the program.

     This is the purpose of an enumerated type.
   - [ ] Use the same set of values in multiple mappings.

     Variables in one enumeration type cannot be used in another enumeration type.
   - [x] Define the set of values that make up a mapping.

     This is the purpose of an enumerated type.
   - [x] Use them as indices for a vector.

     Since the values in enumerated types are represented as integers, we can use them as vector indices.

.. tb-choice::
   :name: enum_type_2

   Assume we have the following struct defined by this enumerated
   type.  What will be printed by the print function?

   ::

       enum Scoops { SINGLE = 1, DOUBLE, TRIPLE };
       enum Flavor { VANILLA, CHOCOLATE, STRAWBERRY, COOKIESNCREAM, MINTCHIP, COOKIEDOUGH };
       enum Order { CUP, CAKECONE, SUGARCONE, WAFFLECONE }

       struct iceCream {
          Scoops scoops;
          Flavor flavor;
          Order order;

          iceCream (Scoops s, Flavor f, Order o);
          printOrder () {
            // To save space, I didn't include the mapping.  I'm sure you can still figure it out.
            cout << "Who ordered a " << scoops[scoop] << " scoop of " << flavors[flavor] << " in a " << orders[order] << ?;
          }
       };

       int main () {
         iceCream icecream (2, 3, 2);
         iceCream.printOrder();
       }


   - [ ] Who ordered a triple scoop of Cookies 'n' Cream in a sugar cone?

     Remember that we performed an override for one of the enumerated types!
   - [ ] Who ordered a double scoop of Strawberry in a cake cone?

     Remember that the default enumeration starts at 0.
   - [x] Who ordered a double scoop of Cookies 'n' Cream in a sugar cone?

     2 corresponds to "double", 3 corresponds to "Cookies 'n' Cream", and 2 corresponds to "sugar cone".
   - [ ] Who ordered a triple scoop of Strawberry in a cake cone?

     Remember that we performed an override for one of the enumerated types!  The default enumeration starts at 0.
   - [ ] Who ordered a triple scoop of Mint Chocolate Chip in a Waffle Cone?

     Take another look at how we defined our enumerated types.

.. tb-blank::
   :name: c192_enum_type_3

   Based on the ``card_rank`` enumerated type, what integer value does ``queen`` have?

   {{blank}}

   .. tb-answer::
      :regex:
      :match: 12|twelve
      :feedback: Correct!
      :incorrect: Incorrect! Try again.

Scoped enumerations
~~~~~~~~~~~~~~~~~~~

C++20 also supports scoped enumerations, introduced in C++11. For example::

   enum class suit { clubs, diamonds, hearts, spades };
   suit chosen = suit::hearts;

The qualified name prevents collisions with other names, and a scoped enum
does not implicitly convert to an integer. Use ``static_cast`` when an integer
representation is actually needed. The card examples in this chapter retain
unscoped enums to demonstrate their rules; both forms are valid C++20.

