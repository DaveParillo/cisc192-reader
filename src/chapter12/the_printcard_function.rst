The ``print_card`` function
---------------------------

When you create a new type, the first step is usually to declare the
instance variables and write constructors. The second step is often to
write a function that prints the object in human-readable form.

In the case of ``playing_card`` objects, “human-readable” means that we have to
map the internal representation of the rank and suit onto words. A
natural way to do that is with a vector of ``string``\ s. You can
create a vector of ``string``\ s the same way you create an vector of
other types:

::

     std::vector<std::string> suits (4);

Of course, in order to use ``vector``\ s and ``string``\ s, you will
have to include the header files for both.

To initialize the elements of the vector, we can use a series of
assignment statements.

::

     suits[0] = "Clubs";
     suits[1] = "Diamonds";
     suits[2] = "Hearts";
     suits[3] = "Spades";

A state diagram for this vector looks like this:

We can build a similar vector to decode the ranks. Then we can select
the appropriate elements using the ``suit`` and ``rank`` as indices.
Finally, we can write a function called ``print`` that outputs the card
on which it is invoked:

::

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

The expression ``suits[suit]`` means “use the instance variable ``suit``
from the current object as an index into the vector named ``suits``, and
select the appropriate string.”

Because ``print`` is a ``playing_card`` member function, it can refer to the
instance variables of the current object implicitly (without having to
use dot notation to specify the object). The output of this code

::

     playing_card card (1, 11);
     card.print ();

is ``Jack of Diamonds``.

The active code below uses the ``playing_card::print()`` function.  Feel free to modify
the values that ``card`` is being initialized to in the constructor:  this will
change the output from the ``playing_card::print()`` function.

.. tb-code:: cpp
   :name: c192_12_3-support
   :hidden:
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']


   playing_card::playing_card () {
     suit = 0;  rank = 1;
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
   :name: c192_12_3
   :caption: Example c192_12_3
   :run-after: c192_12_3-support
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <iostream>
   #include <string>
   #include <vector>

   struct playing_card {
       int suit, rank;

       playing_card ();
       playing_card (int s, int r);
       void print () const;
   };

   int main() {
       playing_card card (1,11);
       card.print ();
   }

You might notice that we are not using the zeroeth element of the
``ranks`` vector. That’s because the only valid ranks are 1–13. By
leaving an unused element at the beginning of the vector, we get an
encoding where 2 maps to “2”, 3 maps to “3”, etc. From the point of view
of the user, it doesn’t matter what the encoding is, since all input and
output uses human-readable formats. On the other hand, it is often
helpful for the programmer if the mappings are easy to remember.

.. tb-choice::
   :name: printCard_function_1

   How would we select the appropriate string for the instance variable ``rank``?

   - [ ] rank.ranks

     Incorrect! Remember, ranks is a vector!
   - [ ] ranks.rank

     Incorrect! Remember, ranks is a vector!
   - [x] ranks[rank]

     Correct! This is an example of how we use mapping!
   - [ ] rank[ranks]

     Incorrect! This is using the vector "ranks" as an index to a single "rank".

.. tb-blank::
   :name: c192_print_card_function_2

   ::

    playing_card card (3, 1);
    card.print ();
   
   What is printed by card.print()? Type your answer exactly as it would appear in the terminal.

   {{blank}}

   .. tb-answer::
      :match: ace of spades
      :feedback: Correct!
      :incorrect: Incorrect!  Try this input on the code above!

.. tb-choice::
   :name: printCard_function_3

   Does it matter how we encode a mapping?

   - [x] Yes, because the mappings should be easy for the programmer to remember.

     Correct! The programmer should uses mappings that are easy to remember (even if this means we don't use the zeroeth element of the ranks vector).
   - [ ] Yes, because the mappings should be easy for the user to remember.

     Incorrect! The user doesn't need to know how things are mapped.
   - [ ] No! All input and output uses human-readable formats, so the programmer doesn't need to understand what is going on behind the scenes.

     Incorrect! The programmer should always know what is going on with their code.
   - [x] No! All input and output uses human-readable formats, so the user doesn't need to understand what is going on behind the scenes.

     Correct! The user doesn't need to know how the programmer coded things.
