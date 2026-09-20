Multiple Choice Exercises
-------------------------

.. tb-choice::
   :name: mce_14_1

   What is one use of data encapsulation?

   - [ ] To wrap up a sequence of code in a function.

     - This is one use of functional encapsulation, not data encapsulation.

   - [x] To hide implementation details from users or programmers that don't need to know them.

     +  Data encapsulation is the separation of the implementation of data from the interface of a structure.

   - [ ] To keep all data in a container like a vector.

     - This is not related to encapsulation.

   - [ ] To make all data public and accessible to everyone.

     - Data encapsulation is based on the idea that each estructure should prevent unrestricted access to internal representation.

.. tb-choice::
   :name: mce_14_2

   Which of the following are accessor functions?

   .. code-block:: cpp

       struct Student {
         private:
           int id;
         public:
           string name;
           int year;

           int getID () { return id; }
           int setID (int i) { id = i; }
           void printInfo () { cout << "Student: " << name << ", " << year; }
       };

   - [ ] ``Student ()``

     - This is the ``Student`` constructor.

   - [x] ``getID ()``

     + This is a "getter" function, which is an accessor function since it accesses and returns a private member variable.

   - [x] ``setID ()``

     + This is a "setter" function, which is an accessor function since it accesses and modifies a private member variable.

   - [ ] ``printInfo ()``

     - This function does not access a private member variable.

.. tb-choice::
   :name: mce_14_3

   Which of the following are true?

   - [ ] By default, ``struct`` member variables are private.

     - By default, ``struct`` member variables are public. This is the main difference between a ``class`` and a ``struct``.

   - [x] By default, ``class`` member variables are private.

     + This is different from a ``struct``, whose member variables default to be public.

   - [x] Private member variables can be accessed within the class.

     + Private member variables are private to things outside of the class.

   - [x] Public member variables can be accessed within the class.

     + Public member variables can be accessed anywhere, including within the class.

.. tb-choice::
   :name: mce_14_4

   What should replace the question marks in the code below? Use accessor functions.

   .. code-block:: cpp

       class rightTriangle {
         int base;
         int height;

         public:
           int getBase () { return base; }
           int getHeight () { return height; }
           double calculateHypotenuse () { 
             ???
           }
       };

   - [x] ``return sqrt(pow(getBase, 2) + pow(getHeight, 2));``

     + We use the Pythagorean Theorem and ``getBase`` and ``getHeight`` to calculate and return the hypotenuse. 

   - [ ] ``return pow(getBase, 2) + pow(getHeight, 2);``

     - Use the Pythagorean Theorem!

   - [ ] ``return sqrt(pow(base, 2) + pow(height, 2));``

     - Although this would work, we want to use accessor functions.

   - [ ] ``cout << sqrt(pow(getBase, 2) + pow(getHeight, 2));``

     - Take a look at the return type of ``calculateHypotenuse``.

.. tb-choice::
   :name: mce_14_5

   What is wrong with the code below?

   .. code-block:: cpp

       class Plane {
         int flightNumber;
         string model;
         string origin;
         string destination;

         public:
           void printInfo () { 
             cout << "Flight " << flightNumber << " (" << model 
                  << ") from " << origin << " to " << destination << endl;
           }
       };

       int main() {
         Plane p;
         p.flightNumber = 1846;
         p.model = "Boeing 787";
         p.origin = "Los Angeles";
         p.destination = "Detroit";
         p.printInfo ();
       }

   - [ ] The ``Plane`` class is missing the keyword ``private:``.

     - By default, ``class`` member variables are private, so we don't need to explicitly write ``private:``.

   - [ ] ``printInfo`` cannot access ``Plane``\'s private member variables.

     - The private member variables of ``Plane`` are only inaccessible to those outside of the class.

   - [x] We cannot assign the private member variables of ``p`` in ``main``.

     + We are trying to access the private member variables of a ``Plane`` object outside of the ``Plane`` class.

   - [ ] We cannot call ``printInfo`` in ``main``.

     - ``printInfo`` is a public member function, so we are allowed to call it in ``main``.

.. tb-choice::
   :name: mce_14_6

   What is the output of the code below?

   .. code-block:: cpp

       class Temp {
         private: 
           double fahrenheit;
           double celsius;
           bool is_fahrenheit;
           bool is_celsius;

         public:
           double getFahrenheit () { return fahrenheit; }
           double getCelsius () { return celsius; }
           void setFahrenheit (double f) { fahrenheit = f; is_fahrenheit = true; is_celsius = false; }
           void setCelsius (double c) { celsius = c; is_celsius = true; is_fahrenheit = false; }
           void printTemp () { 
             if (is_fahrenheit) {
               cout << "It is " << getFahrenheit() << " degrees Fahrenheit" << endl;
             }
             else {
               cout << "It is " << getCelsius() << " degrees Celsius" << endl;
             }
           }
       };

       int main() {
         Temp t;
         t.setFahrenheit (125);
         t.setCelsius (30);
         t.printTemp ();
       }

   - [ ] It is 125 degrees Fahrenheit

     - Since we called ``setCelsius`` last, ``is_celsius`` is ``true`` and ``is_fahrenheit`` is false.

   - [ ] It is 30 degrees Fahrenheit

     - Since we called ``setCelsius`` last, ``is_celsius`` is ``true`` and ``is_fahrenheit`` is false.

   - [ ] It is 125 degrees Celsius

     - What was the value that we set ``celsius`` equal to?

   - [x] It is 30 degrees Celsius

     + Since we called ``setCelsius`` last, we print out 30 degrees Celsius.


.. tb-choice::
   :name: mce_14_7

   Which of the following are true about invariants?

   - [x] Data encapsulation helps enforce invariants by preventing unrestricted access to private member variables.

     + By limiting access to private member variables, data encapsulation can control what values these variables can take on.

   - [ ] If an invariant is true at the start of a function, it can be false at the end.

     - If an invariant is true at the start of a function, it must also be true at the end.

   - [ ] An invariant cannot be false in the middle of a function, even if it is true at the start and the end.

     - An invariant can be false in the middle of a function, and it is sometimes unavoidable. 

   - [x] Maintaining invariants can reduce the number of bugs in a program.

     + By maintaining invariants, you can guarantee that all values are what they should be. 

.. tb-choice::
   :name: mce_14_8

   Take a look at the class definition of ``Date``. What are some invariants we must maintain?

   .. code-block:: cpp

       class Date {
         private:
           int day;
           int month;
           int year;
           bool is_birthday;
           string message;

         public:
           Date (int hour, int d, int m, int y, bool b, string m) { 
             day = d;
             month = m;
             year = y;
             is_birthday = b;
             message = m;
           }
       };

   - [x] ``day`` must be between 1 and 31.

     + There is a maximum of 31 possible days in a month.

   - [x] ``month`` must be between 1 and 12.

     + There are 12 months in a year.

   - [ ] ``is_birthday`` must be ``true`` or ``false``.

     - This isn't an invariant since ``is_birthday`` being a ``bool`` isn't really a condition.

   - [ ] ``year`` must be greater than 2000.

     - ``year`` can be less than 2000, so this isn't a correct invariant to maintain.

.. tb-choice::
   :name: mce_14_9

   Take a look at the function below. What are its preconditions and postconditions?

   .. code-block:: cpp

       int calculateRectangleArea (int length, int width) {
         return length * width;
       }

   - [x] Precondition: ``length`` and ``width`` must both be positive.

     + A rectangle can't have negative dimensions, or dimensions of 0.

   - [ ] Precondition: ``length`` must be greater than ``width``.

     - A rectangle can be wider than it is long. 

   - [x] Postcondition: ``calculateRectangleArea`` must return a positive number.

     + Since ``length`` and ``width`` must both be positive, their product muast also be positive.

   - [ ] Postcondition: ``calculateRectangleArea`` must return a nonnegative number.

     - ``calculateRectangleArea`` cannot return 0, which is a nonnegative number but not a valid area.

.. tb-choice::
   :name: mce_14_10

   What are private functions and what do they do?

   - [ ] Functions that return the type ``private``.

     - There is no return type of ``private``.

   - [ ] Functions that are used to retrieve and modify private member variables.

     - These are called accessor functions, not private functions.

   - [ ] Functions written outside of a class that accesses a class's private member variables.

     - No function outside of a class can access that class's private member variables.

   - [x] Functions that are declared private which cannot be invoked by client programs.

     + We would make functions private if we wanted to restrict their usage outside of the class.

