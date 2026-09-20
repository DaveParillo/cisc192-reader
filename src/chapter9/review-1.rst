.. _more-structures-multiple-choice-exercises:

Multiple Choice Exercises
-------------------------

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: mce_9_1

         Which of the following are variables of type ``book``?

         .. code-block:: cpp

           struct book {
             string title, author;
             int year_published;
             double price;
           };

           int main() {
             book gatsby = { "The Great Gatsby", "F. Scott Fitzgerald", 1925, 4.75 };
             book frankenstein = { "Frankenstein", "Mary Shelley", 1823, 5.99 };
             string flies = "Lord of the Flies";
             int year = 1954;
           }

         - [x] ``gatsby``

           + ``gatsby`` is a ``book``. 

         - [x] ``frankenstein``

           + ``frankenstein`` is a ``book``. 

         - [ ] ``flies``

           - ``flies`` is a ``string``. 

         - [ ] ``year``

           - ``year`` is an ``int``.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: mce_9_2

         Which of the following are instance variables of type ``book``?

         .. code-block:: cpp

           struct book {
             string title, author;
             int year_published;
             double price;
           };

           int main() {
             book gatsby = { "The Great Gatsby", "F. Scott Fitzgerald", 1925, 4.75 };
             book frankenstein = { "Frankenstein", "Mary Shelley", 1823, 5.99 };
             string flies = "Lord of the Flies";
             int year = 1954;
           }

         - [ ] ``gatsby``

           - ``gatsby`` is a ``book``, not an instance variable of ``book``. 

         - [x] ``title``

           + ``title`` is an instance variable of ``book``. 

         - [ ] ``year``

           - ``year`` is an ``int`` declared in ``main``, not an instance variable of ``book``. 

         - [x] ``price``

           + ``price`` is an instance variable of ``book``. 

   .. tb-tab:: Q3

      .. tb-choice::
         :name: mce_9_3

         What is the output of the code below?

         .. code-block:: cpp

           struct book {
             string title, author;
             int year_published;
             double price;
           };

           void print_book (book& b) {
             cout << '"' << b.title << "\" by " << b.author << " (" << b.year_published << "), $" << b.price << '\n';
           }

           int main() {
             book mockingbird = { "To Kill a Mockingbird", "Harper Lee", 1960, 9.25 };
             double discounted_price = 7.19;
             b.price = discounted_price;
             print_book (mockingbird);
           }

         - [ ] To Kill a Mockingbird by Harper Lee (1960), $9.25

           - Take a closer look at ``main``. Was the price of the book modified? 

         - [ ] "To Kill a Mockingbird" by Harper Lee (1960), $9.25

           - Take a closer look at ``main``. Was the price of the book modified? 

         - [x] "To Kill a Mockingbird" by Harper Lee (1960), $7.19

           + The price was changed from $9.25 to $7.19. 

         - [ ] \"To Kill a Mockingbird\" by Harper Lee (1960), $7.19

           - The ``\`` are escape characters. Used in this context, they allow us to print quotation marks.

   .. tb-tab:: Q4

      .. tb-choice::
         :name: mce_9_4

         What kind of function is ``print_book``?

         .. code-block:: cpp

           struct book {
             string title, author;
             int year_published;
             double price;
           };

           void print_book (book& b) {
             cout << '"' << b.title << "\" by " << b.author << " (" << b.year_published << "), $" << b.price << '\n';
           }

           int main() {
             book dracula = { "Dracula", "Bram Stoker", 1897, 3.95 };
             print_book (dracula);
           }

         - [x] Pure function

           + ``print_book`` takes  a ``book`` as an object but it doesn't modify it.

         - [ ] Modifier function

           - Does ``print_book`` modify the ``book`` object?

         - [ ] Fill-in function

           - ``print_book`` takes one parameter, and its parameter is not an empty ``book`` object.

         - [ ] Fruitful function

           - ``print_book`` does not return anything.

   .. tb-tab:: Q5

      .. tb-choice::
         :name: mce_9_5

         What is wrong with the code below?

         .. code-block:: cpp

           struct book {
             string title, author;
             int year_published;
             double price;
           }

           void print_book (book& b) {
             cout << '"' << b.title << "\" by " << b.author << " (" << b.year_published << "), $" << b.price << '\n';
           }

           void apply_discount (const book& b, double discount) {
             b.price -= discount;
           }

           int main() {
             book godfather = { "The Godfather", "Mario Puzo", 1969, 10.90 };
             apply_discount (godfather, 5.40);
             print_book (godfather);
           }

         - [x] The ``struct`` definition is missing a semicolon at the end.

           + It's a common mistake to forget the semicolon at the end of ``struct`` definitions.

         - [ ] We are not allowed to pass in a ``book`` object by reference in ``print_book``.

           - We are allowed to do this. It's usually a good idea to pass structures by reference since it won't make copies of the structures, thus saving memory space.

         - [x] The keyword ``const`` needs to be removed in the function definition for ``apply_discount``.

           + Since the ``apply_discount`` function modifies the ``book`` passed into it, we don't it to be ``const``.

         - [ ] There are no errors with the code.

           - There are a couple errors. Can you find them?

   .. tb-tab:: Q6

      .. tb-choice::
         :name: mce_9_6

         What kind of function is ``apply_discount``?

         .. code-block:: cpp

           struct book {
             string title, author;
             int year_published;
             double price;
           };

           void print_book (book& b) {
             cout << '"' << b.title << "\" by " << b.author << " (" << b.year_published << "), $" << b.price << '\n';
           }

           void apply_discount (book& b, double discount) {
             b.price -= discount;
           }

           int main() {
             book godfather = { "The Godfather", "Mario Puzo", 1969, 10.90 };
             apply_discount (godfather, 5.40);
             print_book (godfather);
           }

         - [ ] Pure function

           - Does ``apply_discount`` modify the ``book`` object?

         - [x] Modifier function

           + ``apply_discount`` modifies the ``book`` object by updating the price.

         - [ ] Fill-in function

           - ``apply_discount`` does not take an empty ``book`` object as a parameter.

         - [ ] Fruitful function

           - ``apply_discount`` does not return anything.

   .. tb-tab:: Q7

      .. tb-choice::
         :name: mce_9_7

         What is the output of the code below?

         .. code-block:: cpp

           struct point_3d {
             double x, y, z;
           };

           void print_point_3d (const point_3d& p) {
             cout << '(' << p.x << ", " << p.y << ", " << p.z << ')' << '\n';
           }

           void midpoint (const point_3d& p1, const point_3d& p2, point_3d p3) {
             p3.x = (p1.x + p2.x) / 2;
             p3.y = (p1.y + p2.y) / 2;
             p3.z = (p1.z + p2.z) / 2;
           }

           int main() {
             point_3d p1 = { 3.0, 5.0, 2.0 };
             point_3d p2 = { 6.0, 3.5, 9.3 };
             point_3d p3 = { 0.0, 0.0, 0.0 };
             midpoint (p1, p2, p3);
             print_point_3d (p3);
           }

         - [ ] (4.5, 4.25, 5.65)

           - Look at the function declaration of ``midpoint`` carefully.

         - [ ] (3.0, 5.0, 2.0)

           - Look at the function declaration of ``midpoint`` carefully.

         - [ ] (9.0, 8.5, 11.3)

           - Look at the function declaration of ``midpoint`` carefully.

         - [x] (0, 0, 0)

           + The last parameter in ``midpoint`` is not passed by reference, so a copy is made and changes are made to the copy, not the original.

   .. tb-tab:: Q8

      .. tb-choice::
         :name: mce_9_8

         What kind of function is ``midpoint``?

         .. code-block:: cpp

           struct point_3d {
             double x, y, z;
           };

           void print_point_3d (const point_3d& p) {
             cout << '(' << p.x << ", " << p.y << ", " << p.z << ')' << '\n';
           }

           void midpoint (const point_3d& p1, const point_3d& p2, point_3d& p3) {
             p3.x = (p1.x + p2.x) / 2;
             p3.y = (p1.y + p2.y) / 2;
             p3.z = (p1.z + p2.z) / 2;
           }

           int main() {
             point_3d p1 = { 3.0, 5.0, 2.0 };
             point_3d p2 = { 6.0, 3.5, 9.3 };
             point_3d p3 = { 0.0, 0.0, 0.0 };
             midpoint (p1, p2, p3);
             print_point_3d (p3);
           }

         - [ ] Pure function

           - Does ``midpoint`` modify a ``point_3d`` object?

         - [x] Modifier function

           + ``midpoint`` modifies the last ``point_3d`` object.

         - [x] Fill-in function

           + ``midpoint`` takes an "empty" third ``point_3d`` and fills it with the average of the other two ``point_3d`` objects.

         - [ ] Fruitful function

           - ``midpoint`` does not return anything.

   .. tb-tab:: Q9

      .. tb-choice::
         :name: mce_9_9

         What is the output of the code below?

         .. code-block:: cpp

           struct point_3d {
             double x, y, z;
           };

           void print_point_3d (const point_3d& p) {
             cout << '(' << p.x << ", " << p.y << ", " << p.z << ')' << '\n';
           }

           void midpoint (const point_3d& p1, const point_3d& p2, point_3d& p3) {
             p3.x = (p1.x + p2.x) / 2;
             p3.y = (p1.y + p2.y) / 2;
             p3.z = (p1.z + p2.z) / 2;
           }

           point_3d reflect_xy_plane(const point_3d& p) {
             point_3d flipped = p;
             flipped.z = -flipped.z;
             return flipped;
           }

           int main() {
             point_3d p = { 11.3, 4.5, 2.9 };
             point_3d p_reflected = reflect_xy_plane (p);
             print_point_3d (p_reflected);
           }

         - [ ] (11.3, 4.5, 2.9)

           - Take a closer look at the implementation of ``reflect_xy_plane``.

         - [x] (11.3, 4.5, -2.9)

           + The point is reflected across the XY plane, so the z value is inverted.

         - [ ] (-11.3, -4.5, 2.9)

           - Take a closer look at the implementation of ``reflect_xy_plane``.

         - [ ] (5.65, 2.25, 1.45)

           - Take a closer look at the implementation of ``reflect_xy_plane``.

   .. tb-tab:: Q10

      .. tb-choice::
         :name: mce_9_10

         What is the output of the code below?

         .. code-block:: cpp

           struct point_3d {
             double x, y, z;
           };

           void print_point_3d (const point_3d& p) {
             cout << '(' << p.x << ", " << p.y << ", " << p.z << ')' << '\n';
           }

           void midpoint (const point_3d& p1, const point_3d& p2, point_3d& p3) {
             p3.x = (p1.x + p2.x) / 2;
             p3.y = (p1.y + p2.y) / 2;
             p3.z = (p1.z + p2.z) / 2;
           }

           point_3d reflect_xy_plane(const point_3d& p) {
             point_3d flipped = p;
             flipped.z = -flipped.z;
             return flipped;
           }

           int main() {
             point_3d p1 = { 7.0, 3.5, 6.7 };
             point_3d p2 = { 2.0, 1.0, 0.0 };
             point_3d p3 = { 3.9, 4.5, 10.0 };
             point_3d p4 = reflect_xy_plane (p1);
             midpoint (p4, p3, p2);
             print_point_3d (p2);
           }

         - [x] (5.45, 4, 1.65)

           + Take a closer look at the implementation of ``reflect_xy_plane``.

         - [ ] (5.45, 4, 8.35)

           - Check the arguments passed into ``midpoint``.

         - [ ] (7.0, 3.5, -6.7)

           - Take a closer look at which point is being printed.

         - [ ] (4.5, 2.25, 3.35)

           - Check the arguments passed into ``midpoint``.

