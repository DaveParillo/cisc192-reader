Multiple Choice Exercises
-------------------------

.. tb-choice::
   :name: mce_12_1

   Select all of the true statements.

   - [x] You can have a vector that stores a vector of objects.

     + C++ allows for a variety of different compositions.

   - [ ] In order to check to see if two ``card``\s are equal, we can use the ``==`` operator.

     - We have to write a function that compares two ``card``\s.

   - [x] There is no faster way to search through an unsorted vector than using a linear search.

     + If the ``vector`` were sorted, then there are faster search methods.

   - [x] There is no such thing as an empty object.

     + All variables are given default values unless otherwise specified by the user.

.. tb-choice::
   :name: mce_12_2

   What is the correct way to declare a ``vector`` of ``vector``\s of ``int``\s called ``vec``?

   - [ ] ``vector<int> vec;``

     - This declares a ``vector`` of ``int``\s.

   - [ ] ``vector<int> vec<int>;``

     - This is not the proper way to declare ``vec``. 

   - [ ] ``vector<vector<int> vec;``

     - Close! Look closely at the answer choices again.

   - [x] ``vector<vector<int> > vec;``

     + This is the proper way to declare a ``vector`` of ``vector``\s of ``int``\s.

.. tb-choice::
   :name: mce_12_3

   What is the value of ``card``?

   .. code-block:: cpp

       struct card {
         int suit, rank;
         card ();
         card (int s, int r);
       };

       card::card () {
         suit = 0;  rank = 0;
       }

       card::card (int s, int r) {
         suit = s;  rank = r;
       }

       int main() {
         card card (2, 8);
       }

   - [ ] Ace of Clubs

     - How did we define our mapping earlier in the chapter?

   - [x] 8 of Hearts

     + ``card`` has a ``suit`` value of 2 corresponding to Hearts, and a ``rank`` value of 8.

   - [ ] King of Hearts

     - How did we define our mapping earlier in the chapter?

   - [ ] ``card`` does not have a value.

     - We initialized ``card`` with a ``suit`` value of 2 and a ``rank`` value of 8.

.. tb-choice::
   :name: mce_12_4

   There is an error with the code below. Can you find it?

   .. code-block:: cpp

       struct card {
         int suit, rank;
         card ();
         card (int s, int r);
         void print () const;
       };

       int main() {
         card card (1,3);
         print (card);
       }

   - [ ] ``card`` is not a valid ``card``.

     - A ``suit`` of 1 and a ``rank`` of 3 maps to the 3 of Diamonds.

   - [ ] There shouldn't be a semicolon after the ``struct`` definition.

     - A ``struct`` definition always ends with a semicolon.

   - [x] ``print`` is a member function.

     + Since ``print`` is a member function, we need to use the dot operator.

   - [ ] There is nothing wrong with the code.

     - There is an error with the code. Can you find it?

.. tb-choice::
   :name: mce_12_5

   What is the output of the code below?

   .. code-block:: cpp

      struct card {
        int suit, rank;
        card ();
        card (int s, int r);
        void print () const;
        bool is_greater (const card& c2) const;
      };

      int main() {
        card card1 (2,12);
        card card2 (2,2);
        cout << card1.is_greater (card2) << '\n';
      }

   - [ ] True

     - The output of a ``bool`` is either a 0 or 1.

   - [ ] False

     - The output of a ``bool`` is either a 0 or 1.

   - [ ] 0

     - Is ``card1`` greater than ``card2``?

   - [x] 1

     + The Queen of Hearts is greater than the 2 of Hearts.

.. tb-choice::
   :name: mce_12_6

   What is the output of the code below?

   .. code-block:: cpp

      struct card {
        int suit, rank;
        card ();
        card (int s, int r);
        void print () const;
        bool is_greater (const card& c2) const;
      };

      vector<card> build_deck();

      bool equals (const card& c1, const card& c2){
        return (c1.rank == c2.rank && c1.suit == c2.suit);
      }

      void print_deck(const vector<card>& deck);

      int find (const card& card, const vector<card>& deck);

      int main() {
        vector<card> deck = build_deck();
        card card (3, 13);
        cout << find(card, deck);
      }

   - [x] 51

     + The ``card`` is the King of Spades, which is located at the end of the deck.

   - [ ] 52

     - Since the ``vector`` is size 52, it cannot have an index of 52.

   - [ ] 12

     - What is the value of ``card``?

   - [ ] -1

     - What is the value of ``card``?

.. tb-choice::
   :name: mce_12_7

   What is true about ``deck``?

   .. code-block:: cpp

      struct card {
        int suit, rank;
        card ();
        card (int s, int r);
        void print () const;
        bool is_greater (const card& c2) const;
      };

      vector<card> create_deck() {
        vector<card> deck (12);
        int i = 0;
        for (int suit = 0; suit <= 3; suit++) {
          for (int rank = 1; rank < 4; rank++) {
            deck[i].suit = suit;
            deck[i].rank = rank;
            i++;
          }
        }
        return deck;
      }

      int main() {
        vector<card> deck = create_deck();
      }

   - [x] It contains 12 ``card``\s.

     + ``create_deck`` returns a ``vector`` of size 12, corresponding to 12 ``card``\s.

   - [ ] The highest ``rank`` is 4.

     - The ``rank`` goes up to but does not include 4.

   - [ ] There are no spades in the deck.

     - The ``suit`` goes up to and include the ``suit`` value 3 which corresponds to spades.

   - [x] The ``deck`` has 3 cards in each suit.

     + Each suit has an Ace, 2, and 3.

.. tb-choice::
   :name: mce_12_8

   How many times does ``find_bisect`` need to call itself in order to find the King of Diamonds?

   .. code-block:: cpp

       struct card {
         int suit, rank;
         card ();
         card (int s, int r);
         void print () const;
         bool is_greater (const card& c2) const;
       };

       vector<card> build_deck();
       bool equals (const card& c1, const card& c2);
       void print_deck(const vector<card>& deck);
       int find (const card& card, const vector<card>& deck);
       int find_bisect (const card& card, const vector<card>& deck, int low, int high);

       int main() {
         vector<card> deck = build_deck();
         card card (1, 13);
         cout << find_bisect(card, deck, 0, 51);
       }

   - [x] 0

     + The King of Diamonds is right in the middle of the deck, so it doesn't need to call itself.

   - [ ] 1

     - Where is the King of Diamonds located relative to the sorted deck?

   - [ ] 3

     - Where is the King of Diamonds located relative to the sorted deck?

   - [ ] 4

     - Where is the King of Diamonds located relative to the sorted deck?

.. tb-choice::
   :name: mce_12_9

   We want to write the function ``find_all_queens``, which searches through a deck and 
   prints out the location of all 4 queens in the ``deck``. What should go in the blanks?

   .. code-block:: cpp

       struct card {
         int suit, rank;
         card ();
         card (int s, int r);
         void print () const;
         bool is_greater (const card& c2) const;
       };

       vector<card> build_deck();
       bool equals (const card& c1, const card& c2);
       void print_deck(const vector<card>& deck);

       void find_all_queens (const vector<card>& deck) {
         for (size_t i = 0; i < deck.____; ++i) {
           if (deck[i].____ == 12) {
             cout << ____ << ' ';
           }
         }
       }

       int main() {
         vector<card> deck = build_deck();
         find_all_queens (deck);
       }

   - [ ] ``push_back()``, ``suit``, ``i``

     - What value should ``i`` go up to?

   - [x] ``size()``, ``rank``, ``i``

     + These are the correct variables and functions.

   - [ ] ``size``, ``rank``, ``deck[i]``

     - We want to print the index, not the card.

   - [ ] ``front()``, ``suit``, ``deck``

     - What value should ``i`` go up to?

.. tb-choice::
   :name: mce_12_10

   What is the process of modeling a complex system with a simplified description in order to suppress unnecessary details while capturing relevant behavior?

   - [ ] Generalization

     - Generalization means to take something specific and make it more general.

   - [ ] Encapsulation

     - Encapsulation means taking a piece of code and wrapping it up in a function.

   - [x] Abstraction

     + Using this process, we can remove unnecessary details to focus on the more important aspects.

   - [ ] Implementation

     - Implementation is the process of taking an idea and making it real.

