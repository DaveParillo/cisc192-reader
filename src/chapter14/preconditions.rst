Preconditions
-------------

.. index::
   single: precondition

Often when you write a function you make implicit assumptions about the
parameters you receive. If those assumptions turn out to be true, then
everything is fine; if not, your program might crash.

To make your programs more robust, it is a good idea to think about your
assumptions explicitly, document them as part of the program, and maybe
write code that checks them.

For example, let’s take another look at ``calculate_cartesian``. Is there
an assumption we make about the current object? Yes, we assume that the
``polar`` flag is set and that ``mag`` and ``theta`` contain valid data.
If that is not true, then this function will produce meaningless
results.

One option is to add a comment to the function that warns programmers
about the **precondition**.

::

   void complex_number::calculate_cartesian ()
   // precondition: the current object contains valid polar coordinates
   //  and the polar flag is set
   // postcondition: the current object will contain valid Cartesian
   //  coordinates and valid polar coordinates, and both the cartesian
   //  flag and the polar flag will be set
   {
     real = mag * std::cos (theta);
     imag = mag * std::sin (theta);
     cartesian = true;
   }

.. index::
   single: postcondition

At the same time, I also commented on the **postconditions**, the things
we know will be true when the function completes.

These comments are useful for people reading your programs, but it is an
even better idea to add code that *checks* the preconditions, so that we
can print an appropriate error message:

::

   void complex_number::calculate_cartesian ()
   {
     if (polar == false) {
       std::cout <<
       "calculate_cartesian failed because the polar representation is invalid"
        << std::endl;
       std::exit (1);
     }
     real = mag * std::cos (theta);
     imag = mag * std::sin (theta);
     cartesian = true;
   }

The ``exit`` function causes the program to quit immediately. The return
value is an error code that tells the system (or whoever executed the
program) that something went wrong.

This kind of error-checking is so common that C++ provides a built-in
macro to check conditions and print diagnostic messages. If you include
the ``cassert`` header file, you get a macro called ``assert`` that
takes a boolean value (or a conditional expression) as an argument. As
long as the argument is true, ``assert`` does nothing. If the argument
is false, assert prints an error message and quits. Here’s how to use
it:

::

   void complex_number::calculate_cartesian ()
   {
     assert (polar);
     real = mag * std::cos (theta);
     imag = mag * std::sin (theta);
     cartesian = true;
     assert (polar && cartesian);
   }

Assertions are disabled when ``NDEBUG`` is defined. Use ordinary error
handling to validate external input; do not rely on assertions for that.

The first ``assert`` statement checks the precondition (actually just
part of it); the second ``assert`` statement checks the postcondition.

In my development environment, I get the following message when I
violate an assertion:

::

   complex_number.cpp:63: void complex_number::calculate_polar(): Assertion `cartesian' failed.
   Abort

There is a lot of information here to help me track down the error,
including the file name and line number of the assertion that failed,
the function name and the contents of the assert statement.

The active code below uses the updated ``calculate_cartesian`` with assert statements.
Notice how because ``c1`` is not in polar, the assert statement in ``calculate_cartesian``
fails and thus we get an error.

.. tb-code:: cpp
   :name: c192_fourteenten-support
   :hidden:
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   complex_number::complex_number () { cartesian = true;  polar = false; }

   complex_number::complex_number (double r, double i) {
     real = r;  imag = i;
     cartesian = true;  polar = false;
   }

   void complex_number::calculate_cartesian () {
     assert (polar);
     real = mag * std::cos (theta);
     imag = mag * std::sin (theta);
     cartesian = true;
     assert (polar && cartesian);
   }

   double complex_number::get_real () {
     if (cartesian == false) calculate_cartesian ();
     return real;
   }

   double complex_number::get_imag () {
     if (cartesian == false) calculate_cartesian ();
     return imag;
   }

   void complex_number::calculate_polar () {
     mag = std::sqrt(std::pow(real, 2) + std::pow(imag, 2));
     theta = std::atan2(imag, real);
     polar = true;
   }

   double complex_number::get_mag () {
     if (polar == false) {
       calculate_polar ();
     }
     return mag;
   }

   double complex_number::get_theta () {
     if (polar == false) {
       calculate_polar ();
     }
     return theta;
   }

   void complex_number::print_cartesian () {
     std::cout << get_real() << " + " << get_imag() << "i" << std::endl;
   }

   void complex_number::print_polar () {
     std::cout << get_mag() << " e^ " << get_theta() << "i" << std::endl;
   }

   complex_number add (complex_number& a, complex_number& b) {
     double real = a.get_real() + b.get_real();
     double imag = a.get_imag() + b.get_imag();
     complex_number sum (real, imag);
     return sum;
   }

   complex_number subtract (complex_number& a, complex_number& b) {
     double real = a.get_real() - b.get_real();
     double imag = a.get_imag() - b.get_imag();
     complex_number diff (real, imag);
     return diff;
   }

   void complex_number::set_polar (double m, double t) {
     mag = m;  theta = t;
     cartesian = false;  polar = true;
   }

   complex_number mult (complex_number& a, complex_number& b) {
     double mag = a.get_mag() * b.get_mag();
     double theta = a.get_theta() + b.get_theta();
     complex_number product;
     product.set_polar (mag, theta);
     return product;
   }

   void complex_number::set_cartesian (double r, double i) {
     real = r;    imag = i;
     cartesian = true;  polar = false;
   }


.. tb-code:: cpp
   :name: c192_fourteenten
   :caption: Example c192_fourteenten
   :run-after: c192_fourteenten-support
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <iostream>
   #include <cmath>
   #include <cassert>

   class complex_number
   {
     double real = 0.0, imag = 0.0;
     double mag = 0.0, theta = 0.0;
     bool cartesian, polar;

   public:
     complex_number ();
     complex_number (double r, double i);
     void calculate_cartesian ();
     double get_real ();
     double get_imag ();
     void calculate_polar ();
     double get_mag ();
     double get_theta ();
     void print_cartesian ();
     void print_polar ();
     void set_polar (double m, double t);
     void set_cartesian (double r, double i);
   };

   complex_number add (complex_number& a, complex_number& b);
   complex_number subtract (complex_number& a, complex_number& b);
   complex_number mult (complex_number& a, complex_number& b);

   int main() {
     complex_number c1 (5.4, 3.2);
     // This will output an error statement stating that
     // "Assertion 'polar' failed."
     c1.calculate_cartesian();
   }

.. tb-choice::
   :name: question14_9_1

   Which of the following are ways that we can make our code more robust?

   - [ ] Assume assumptions are always true.

     Incorrect! Assumptions can turn out to be true or false.
   - [ ] Only check the preconditions.

     Incorrect! In order to maintain invariance, we must ensure that postconditions are met as well.
   - [x] Document assumptions explicitly as part of the program.

     Correct!
   - [x] Write code that checks assumptions, like using assert statements.

     Correct!

.. tb-blank::
   :name: c192_question14_9_2

   What function causes the program to quit immediately?

   {{blank}}

   .. tb-answer::
      :match: Exit|exit
      :feedback: Correct!
      :incorrect: Incorrect! Try again.

