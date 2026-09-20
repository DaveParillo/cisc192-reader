Operations on structures
------------------------

Most of the operators we have been using on other types, like
mathematical operators ( ``+``, ``%``, etc.) and comparison operators
(``==``, ``>``, etc.), do not work on structures by default. It is
possible to define the meaning of these operators for the new type, but
we won’t do that in this book.

A structure can be initialized with a braced list of member values:

.. code-block:: cpp

   struct point {
       double x, y;
   };

   point blank = {3.0, 4.0};

The members are initialized in declaration order: ``x`` receives 3.0 and
``y`` receives 4.0. Initialization creates an object; assignment replaces
an existing object's value. In C++20, we can use a braced list in an
assignment as well:

.. code-block:: cpp

   blank = {12.0, 3.2};

We can also copy one structure to another:

.. tb-code:: cpp
   :name: operations_structures_AC_1
   :caption: Example operations_structures_AC_1
   :compileargs: ['-Wall', '-std=c++20']

   #include <iostream>

   struct point {
       double x, y;
   };

   int main() {
       point p1 = {3.0, 4.0};
       point p2 = p1;          // copy initialization
       p1 = {12.0, 3.2};      // assignment from a braced list
       p2 = p1;              // copy assignment
       std::cout << p2.x << ", " << p2.y << '\n';
   }

The output is ``12, 3.2``. Copying or assigning a ``point`` copies the
values of both members.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-click::
         :name: operations_structures_1

         Click on all incorrect statements in C++20. Assume point is the structure defined above.

         .. code-block:: cpp

            int main() {
                point blank = { 3.0, 4.0 };
                point hello;
                hello = { 3.0, 4.0 };
                point foo;
                foo = hello;
                foo = {3.0, 4.0};
                bool same = (blank == foo);
            }


         .. tb-miss:: text:int main() {

            Braced lists work for initialization and assignment. This point type has no equality operator.

         .. tb-miss:: text:point blank = { 3.0, 4.0 };

            Braced lists work for initialization and assignment. This point type has no equality operator.

         .. tb-miss:: text:point hello;

            Braced lists work for initialization and assignment. This point type has no equality operator.

         .. tb-miss:: text:hello = { 3.0, 4.0 };

            Braced lists work for initialization and assignment. This point type has no equality operator.

         .. tb-miss:: text:point foo;

            Braced lists work for initialization and assignment. This point type has no equality operator.

         .. tb-miss:: text:foo = hello;

            Braced lists work for initialization and assignment. This point type has no equality operator.

         .. tb-miss:: text:foo = {3.0, 4.0};

            Braced lists work for initialization and assignment. This point type has no equality operator.

         .. tb-hit:: text:bool same = (blank == foo);

            Correct.

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: operations_structures_2

         Construct a block of code that correctly initializes the instance variables of a structure.

         .. code-block:: cpp

            {{group}}
            struct point {
            {{endgroup}}
            {{group}}
               double x, y;
            };
            {{endgroup}}
            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               point blank;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int blank; #distractor
            {{endgroup}}
            {{group}}
               blank = { 12.0, 3.2 };
            {{endgroup}}
            {{distractor}}
            {{group}}
               blank = { 12.0, 3.2 } #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               blank = 12.0; #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-choice::
         :name: operations_structures_3



         - [x] %

           The modulo operator does not work on structures.
         - [ ] =

           The assignment operator does work on structures.
         - [x] >

           The greater than operator does not work on structures.
         - [x] ==

           The equality operator does not work on structures.
         - [x] +

           The addition operator does not work on structures.

