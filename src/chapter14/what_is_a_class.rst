What is a class?
----------------

.. index::
   single: class

In most object-oriented programming languages, a **class** is a
user-defined type that includes a set of functions. As we have seen,
structures in C++ meet the general definition of a class.

But there is another feature in C++ that also meets this definition;
confusingly, it is called a ``class``. in C++, a class is just a
structure whose instance variables are private by default. For example,
I could have written the ``playing_card`` definition:

::

   class playing_card
   {
     int suit, rank;

   public:
     playing_card ();
     playing_card (int s, int r);

     int get_rank () const { return rank; }
     int get_suit () const { return suit; }
     void set_rank (int r) { rank = r; }
     void set_suit (int s) { suit = s; }
   };

I replaced the word ``struct`` with the word ``class`` and removed the
``private:`` label. This result of the two definitions is exactly the
same.

In fact, anything that can be written as a ``struct`` can also be
written as a ``class``, just by adding or removing labels. There is no
real reason to choose one over the other, except that as a stylistic
choice, most C++ programmers use ``class``.

Also, it is common to refer to all user-defined types in C++ as
“classes,” regardless of whether they are defined as a ``struct`` or a
``class``.

.. tb-choice::
   :name: question14_2_1

   By default, the data members of a ``class`` are private. 

   - [x] True

     Correct! We can omit the ``private:`` label because the data members are private by default
   - [ ] False

     Incorrect! Try again.

.. tb-choice::
   :name: question14_2_2

   How can we change ``Deck``, which is currently a ``struct``, into a ``class``? 

   .. code-block:: cpp

      struct Deck {
      private:
        vector<Card> cards;

      public:
        Deck ();
        Deck (int n);

        void print () const;
        void swapCards (int index1, int index2);
        int findLowestCard (int index);
        void shuffleDeck ();
        void sortDeck ();
        Deck subdeck (int low, int high) const;
        Deck mergeSort () const;
        Deck mergeSort (Deck deck) const;
      };

   - [ ] Remove the ``private:`` label.

     Incorrect! ``Deck`` is still a ``struct``.
   - [ ] Change ``struct`` to ``class`` and remove the ``public:`` label.

     Incorrect! We don't want to make the constructors and all member functions private.
   - [ ] Remove the ``public:`` label.

     Incorrect! We don't want to make the constructors and all member functions private.
   - [x] Change ``struct`` to ``class``.

     Correct! ``Deck`` is now a ``class`` and it's okay that we kept the ``private:`` label.

.. tb-choice::
   :name: question14_2_3

   Private data members can be accessed within the class.

   - [x] True

     Correct! However, they cannot be accessed outside of the class.
   - [ ] False

     Incorrect! We can access private data members as long as we are in the class.

