Multiple Choice Exercises
-------------------------
.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: mce_9_1
          :practice: T

          Which of the following are variables of type ``Book``?

          .. code-block:: cpp

            struct Book {
              string title, author;
              int yearPublished;
              double price;
            };

            int main() {
              Book gatsby = { "The Great Gatsby", "F. Scott Fitzgerald", 1925, 4.75 };
              Book frankenstein = { "Frankenstein", "Mary Shelley", 1823, 5.99 };
              string flies = "Lord of the Flies";
              int year = 1954;
            }
              
          - ``gatsby``

            + ``gatsby`` is a ``Book``. 

          - ``frankenstein``

            + ``frankenstein`` is a ``Book``. 

          - ``flies``

            - ``flies`` is a ``string``. 

          - ``year``

            - ``year`` is an ``int``.

   .. tab:: Q2

      .. mchoice:: mce_9_2
          :practice: T

          Which of the following are instance variables of type ``Book``?

          .. code-block:: cpp

            struct Book {
              string title, author;
              int yearPublished;
              double price;
            };

            int main() {
              Book gatsby = { "The Great Gatsby", "F. Scott Fitzgerald", 1925, 4.75 };
              Book frankenstein = { "Frankenstein", "Mary Shelley", 1823, 5.99 };
              string flies = "Lord of the Flies";
              int year = 1954;
            }
              
          - ``gatsby``

            - ``gatsby`` is a ``Book``, not an instance variable of ``Book``. 

          - ``title``

            + ``title`` is an instance variable of ``Book``. 

          - ``year``

            - ``year`` is an ``int`` declared in ``main``, not an instance variable of ``Book``. 

          - ``price``

            + ``price`` is an instance variable of ``Book``. 

   .. tab:: Q3

      .. mchoice:: mce_9_3
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

            struct Book {
              string title, author;
              int yearPublished;
              double price;
            };

            void printBook (Book& b) {
              cout << "\"" << b.title << "\" by " << b.author << " (" << b.yearPublished << "), $" << b.price << endl;
            }

            int main() {
              Book mockingbird = { "To Kill a Mockingbird", "Harper Lee", 1960, 9.25 };
              double discountedPrice = 7.19;
              b.price = discountedPrice;
              printBook (mockingbird);
            }
              
          - To Kill a Mockingbird by Harper Lee (1960), $9.25

            - Take a closer look at ``main``. Was the price of the book modified? 

          - "To Kill a Mockingbird" by Harper Lee (1960), $9.25

            - Take a closer look at ``main``. Was the price of the book modified? 

          - "To Kill a Mockingbird" by Harper Lee (1960), $7.19

            + The price was changed from $9.25 to $7.19. 

          - \"To Kill a Mockingbird\" by Harper Lee (1960), $7.19

            - The ``\`` are escape characters. Used in this context, they allow us to print quotation marks.

   .. tab:: Q4

      .. mchoice:: mce_9_4
          :practice: T

          What kind of function is ``printBook``?

          .. code-block:: cpp

            struct Book {
              string title, author;
              int yearPublished;
              double price;
            };

            void printBook (Book& b) {
              cout << "\"" << b.title << "\" by " << b.author << " (" << b.yearPublished << "), $" << b.price << endl;
            }

            int main() {
              Book dracula = { "Dracula", "Bram Stoker", 1897, 3.95 };
              printBook (dracula);
            }
              
          - Pure function

            + ``printBook`` takes  a ``Book`` as an object but it doesn't modify it.

          - Modifier function

            - Does ``printBook`` modify the ``Book`` object?

          - Fill-in function

            - ``printBook`` takes one parameter, and its parameter is not an empty ``Book`` object.

          - Fruitful function

            - ``printBook`` does not return anything.

   .. tab:: Q5

      .. mchoice:: mce_9_5
          :practice: T

          What is wrong with the code below?

          .. code-block:: cpp

            struct Book {
              string title, author;
              int yearPublished;
              double price;
            }

            void printBook (Book& b) {
              cout << "\"" << b.title << "\" by " << b.author << " (" << b.yearPublished << "), $" << b.price << endl;
            }

            void applyDiscount (const Book& b, double discount) {
              b.price -= discount;
            }

            int main() {
              Book godfather = { "The Godfather", "Mario Puzo", 1969, 10.90 };
              applyDiscount (godfather, 5.40);
              printBook (godfather);
            }
              
          - The ``struct`` definition is missing a semicolon at the end.

            + It's a common mistake to forget the semicolon at the end of ``struct`` definitions.

          - We are not allowed to pass in a ``Book`` object by reference in ``printBook``.

            - We are allowed to do this. It's usually a good idea to pass structures by reference since it won't make copies of the structures, thus saving memory space.

          - The keyword ``const`` needs to be removed in the function definition for ``applyDiscount``.

            + Since the ``applyDiscount`` function modifies the ``Book`` passed into it, we don't it to be ``const``.

          - There are no errors with the code.

            - There are a couple errors. Can you find them?

   .. tab:: Q6

      .. mchoice:: mce_9_6
          :practice: T

          What kind of function is ``applyDiscount``?

          .. code-block:: cpp

            struct Book {
              string title, author;
              int yearPublished;
              double price;
            };

            void printBook (Book& b) {
              cout << "\"" << b.title << "\" by " << b.author << " (" << b.yearPublished << "), $" << b.price << endl;
            }

            void applyDiscount (Book& b, double discount) {
              b.price -= discount;
            }

            int main() {
              Book godfather = { "The Godfather", "Mario Puzo", 1969, 10.90 };
              applyDiscount (godfather, 5.40);
              printBook (godfather);
            }
              
          - Pure function

            - Does ``applyDiscount`` modify the ``Book`` object?

          - Modifier function

            + ``applyDiscount`` modifies the ``Book`` object by updating the price.

          - Fill-in function

            - ``applyDiscount`` does not take an empty ``Book`` object as a parameter.

          - Fruitful function

            - ``applyDiscount`` does not return anything.

   .. tab:: Q7

      .. mchoice:: mce_9_7
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

            struct Point3D {
              double x, y, z;
            };

            void printPoint3D (const Point3D& p) {
              cout << "(" << p.x << ", " << p.y << ", " << p.z << ")" << endl;
            }

            void midpoint (const Point3D& p1, const Point3D& p2, Point3D p3) {
              p3.x = (p1.x + p2.x) / 2;
              p3.y = (p1.y + p2.y) / 2;
              p3.z = (p1.z + p2.z) / 2;
            }

            int main() {
              Point3D p1 = { 3.0, 5.0, 2.0 };
              Point3D p2 = { 6.0, 3.5, 9.3 };
              Point3D p3 = { 0.0, 0.0, 0.0 };
              midpoint (p1, p2, p3);
              printPoint3D (p3);
            }
              
          - (4.5, 4.25, 5.65)

            - Look at the function declaration of ``midpoint`` carefully.

          - (3.0, 5.0, 2.0)

            - Look at the function declaration of ``midpoint`` carefully.

          - (9.0, 8.5, 11.3)

            - Look at the function declaration of ``midpoint`` carefully.

          - (0, 0, 0)

            + The last parameter in ``midpoint`` is not passed by reference, so a copy is made and changes are made to the copy, not the original.
            
   .. tab:: Q8

      .. mchoice:: mce_9_8
          :practice: T

          What kind of function is ``midpoint``?

          .. code-block:: cpp

            struct Point3D {
              double x, y, z;
            };

            void printPoint3D (const Point3D& p) {
              cout << "(" << p.x << ", " << p.y << ", " << p.z << ")" << endl;
            }

            void midpoint (const Point3D& p1, const Point3D& p2, Point3D& p3) {
              p3.x = (p1.x + p2.x) / 2;
              p3.y = (p1.y + p2.y) / 2;
              p3.z = (p1.z + p2.z) / 2;
            }

            int main() {
              Point3D p1 = { 3.0, 5.0, 2.0 };
              Point3D p2 = { 6.0, 3.5, 9.3 };
              Point3D p3 = { 0.0, 0.0, 0.0 };
              midpoint (p1, p2, p3);
              printPoint3D (p3);
            }
              
          - Pure function

            - Does ``midpoint`` modify a ``Point3D`` object?

          - Modifier function

            + ``midpoint`` modifies the last ``Point3D`` object.

          - Fill-in function

            + ``midpoint`` takes an "empty" third ``Point3D`` and fills it with the average of the other two ``Point3D`` objects.

          - Fruitful function

            - ``midpoint`` does not return anything.

   .. tab:: Q9

      .. mchoice:: mce_9_9
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

            struct Point3D {
              double x, y, z;
            };

            void printPoint3D (const Point3D& p) {
              cout << "(" << p.x << ", " << p.y << ", " << p.z << ")" << endl;
            }

            void midpoint (const Point3D& p1, const Point3D& p2, Point3D& p3) {
              p3.x = (p1.x + p2.x) / 2;
              p3.y = (p1.y + p2.y) / 2;
              p3.z = (p1.z + p2.z) / 2;
            }

            Point3D reflectXYPlane(const Point3D& p) {
              Point3D flipped = p;
              flipped.z = -flipped.z;
              return flipped;
            }

            int main() {
              Point3D p = { 11.3, 4.5, 2.9 };
              Point3D pReflected = reflectXYPlane (p);
              printPoint3D (pReflected);
            }
              
          - (11.3, 4.5, 2.9)

            - Take a closer look at the implementation of ``reflectXYPlane``.

          - (11.3, 4.5, -2.9)

            + The point is reflected across the XY plane, so the z value is inverted.

          - (-11.3, -4.5, 2.9)

            - Take a closer look at the implementation of ``reflectXYPlane``.

          - (5.65, 2.25, 1.45)

            - Take a closer look at the implementation of ``reflectXYPlane``.

   .. tab:: Q10

      .. mchoice:: mce_9_10
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

            struct Point3D {
              double x, y, z;
            };

            void printPoint3D (const Point3D& p) {
              cout << "(" << p.x << ", " << p.y << ", " << p.z << ")" << endl;
            }

            void midpoint (const Point3D& p1, const Point3D& p2, Point3D& p3) {
              p3.x = (p1.x + p2.x) / 2;
              p3.y = (p1.y + p2.y) / 2;
              p3.z = (p1.z + p2.z) / 2;
            }

            Point3D reflectXYPlane(const Point3D& p) {
              Point3D flipped = p;
              flipped.z = -flipped.z;
              return flipped;
            }

            int main() {
              Point3D p1 = { 7.0, 3.5, 6.7 };
              Point3D p2 = { 2.0, 1.0, 0.0 };
              Point3D p3 = { 3.9, 4.5, 10.0 };
              Point3D p4 = reflectXYPlane (p1);
              midpoint (p4, p3, p2);
              printPoint3D (p2);
            }
              
          - (5.45, 4, 1.65)

            + Take a closer look at the implementation of ``reflectXYPlane``.

          - (5.45, 4, 8.35)

            - Check the arguments passed into ``midpoint``.

          - (7.0, 3.5, -6.7)

            - Take a closer look at which point is being printed.

          - (4.5, 2.25, 3.35)

            - Check the arguments passed into ``midpoint``.

