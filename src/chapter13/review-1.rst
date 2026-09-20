Multiple Choice Exercises
-------------------------

.. tb-choice::
   :name: mce_13_1

   What is the output of the code below?

   .. code-block:: cpp

       enum Month { JAN = 1, FEB, MAR, APR, 
       MAY, JUN, JUL, AUG, SEP, OCT, NOV, DEC };

       int main() {
         Month m1 = JUL;
         Month m2 = NOV;
         cout << m1 << ' ' << m2 << '\n';
       }

   - [ ] JULY NOVEMBER

     - What are the actual values of ``JUL`` and ``NOV``?

   - [ ] JUL NOV

     - What do the values of enumerated types map to?

   - [x] 7 11

     + Since we defined ``JAN`` to start at 1, ``JUL`` and ``NOV`` map to 7 and 11.

   - [ ] 6 10

     - Take a closer look at our enumerated type definition.

.. tb-choice::
   :name: mce_13_2

   What is the output of the code below?

   .. code-block:: cpp

       int main() {
         string s = "summer";
         switch (s) {
           case "spring":
             cout << "It's spring!";
             break;
           case "summer":
             cout << "It's summer!";
           case "fall":
             cout << "It's fall!";
             break;
           case "winter":
             cout << "It's winter!";
           default:
             cout << "Invalid season!";
             break;
         }
       }

   - [ ] summer

     - Although that is the value of ``s``, is that printed?

   - [ ] It's summer!It's fall!

     - This would be the correct answer if this ``switch`` statement worked.

   - [ ] It's summer!It's fall!It's winter!Invalid season!

     - Where are the ``break`` statements?

   - [x] Compile error.

     + ``switch`` statements can't be used on ``string``\s.

.. tb-choice::
   :name: mce_13_3

   What is the output of the code below?

   .. code-block:: cpp

       enum Season { SPRING, SUMMER, FALL, WINTER };

       int main() {
         Season s = SUMMER;
         switch (s) {
           case SPRING:
             cout << "It's spring!";
             break;
           case SUMMER:
             cout << "It's summer!";
           case FALL:
             cout << "It's fall!";
             break;
           case WINTER:
             cout << "It's winter!";
           default:
             cout << "Invalid season!";
             break;
         }
       }

   - [ ] SUMMER

     - Although that is the value of ``s``, is that printed?

   - [x] It's summer!It's fall!

     + Since there is no ``break`` statement after the case for summer but there is one after fall, this is correct.

   - [ ] It's summer!It's fall!It's winter!Invalid season!

     - Where are the ``break`` statements?

   - [ ] Compile error.

     - Since ``s`` is an enumerated type, the ``Season``\s are mapped to ``int``\s, which are valid for ``switch`` statements.

.. tb-choice::
   :name: mce_13_4

   Take a look at the ``struct`` definition of ``entry``. If we wanted to make a
   ``struct`` called ``Dictionary``, how can we create a ``vector`` of ``entry``\s
   as a member variable?

   .. code-block:: cpp

       struct entry {
         string word;
         int page;
       }

   - [x] ``vector<entry> entries;``

     + We create a ``vector`` with type ``entry``.

   - [ ] ``entry entries``

     - This only creates one ``entry``.

   - [ ] ``vector<Dictionary> entry``

     - This creates a ``vector`` of ``Dictionary``\s called ``entry``.

   - [ ] We can't make an object that contains a ``vector``.

     - We can have ``vector``\s inside objects.

.. tb-choice::
   :name: mce_13_5

   What is wrong with the code below?

   .. code-block:: cpp

       struct card {
         int suit, rank;

         card ();
         card (int s, int r);

         void print () const;
         bool is_greater (const card& c2) const;
         int find (const deck& deck) const;
       };

       struct deck {
         vector<card> cards;

         deck ();
         deck (int n);
         void print () const;
         int find (const card& card) const;
       };

   - [ ] We can't have a ``vector`` in ``deck``.

     - We are allowed to have ``vector``\s in objects.

   - [x] The definition of ``card::find()`` is invalid.

     + The definition references ``deck``, but ``deck`` is defined after ``card``.

   - [ ] We can't define ``print()`` in both ``card`` and in ``deck``.

     - Although they have the same name, these are two different ``print()`` functions.

   - [ ] Nothing is wrong with the code.

     - There is an error in the code. Can you find it?

.. tb-choice::
   :name: mce_13_6

   Why can't we code our ``shuffle`` function to work the exact same way humans shuffle cards?

   - [ ] Our code can't split the deck exactly in half.

     - We can split the deck exactly in half.

   - [ ] The way our code would shuffle cards would be unpredictable.

     - Part of the problem is that the cards would be shuffled in a predictable manner.

   - [ ] Our code would result in an infinite loop.

     - There's no reason to loop infinitely.

   - [x] Our code would perform a perfect shuffle.

     + Because the cards are shuffled perfectly, the exact ordering of the cards is predictable and thus the cards aren't really shuffled.

.. tb-choice::
   :name: mce_13_7

   What is true about helper functions?

   - [ ] They are longer than the bigger functions since they do all the work.

     - Most helper functions are shorter than the bigger function.

   - [x] They are simpler functions that help the bigger function.

     + As the name implies, they help a bigger function.

   - [x] They shorten the code used in bigger functions.

     + Usually the bigger function has repetitive code, which is then put into a helper function to help shorten the bigger function.

   - [x] They make debugging easier.

     + Since helper functions break down the bigger function into smaller parts, it's easier to isolate and identify issues.

.. tb-choice::
   :name: mce_13_8

   Using pseudocode to figure out what helper functions are needed is a characteristic of what?

   - [ ] Encapsulation

     - This is the process of wrapping up a sequence of instructions in a function.

   - [ ] Generalization

     - This is the process of taking something specific and making it more general.

   - [x] Top-down design

     + This is the process of using pseudocode to sketch solutions to large problems and design the interfaces of helper functions.

   - [ ] Bottom-up design

     - This is the process of writing small, useful functions and then assembling them into larger solutions.

.. tb-choice::
   :name: mce_13_9

   Which of the following can lead to off by one errors?

   - [ ] Running a for loop too little or too many times.

     - This can lead to too few iterations or too many iterations.

   - [ ] Forgetting that indexing starts at 0.

     - This can lead you to have values that are shifted by one.

   - [ ] Using less than instead of less than or equal to in a while loop.

     - This can lead to running the while loop one less times than what you wanted.

   - [x] All of the above.

     + These can all lead to off by one errors.

.. tb-choice::
   :name: mce_13_10

   What is the amount of time that merge_sort takes?

   - [x] n log n

     + This makes merge_sort faster than our previous version of selection sort.

   - [ ] n!

     - merge_sort runs faster than factorial time.

   - [ ] logn

     - merge_sort runs slower than logarithmic time.

   - [ ] n^2

     - This is the time complexity of selection sort.

.. tb-choice::
   :name: mce_13_11

   What kind of sorting algorithm is our ``sort_deck`` function? You are encouraged to search up these different sorting algorithms!

   - [ ] Bubble sort

     - Bubble sort swaps adjacent items and "bubbles" the lightest items to the top.

   - [ ] Insertion sort

     - Insertion sort selects an item from the unsorted section and puts it in the right location in the sorted section.

   - [x] Selection sort

     + Selection sort finds the smallest item at each iteration i and puts it at the ith location.

   - [ ] Quicksort

     - Quicksort uses recursive calls to partition a list.

