.. _classes-invariants-preconditions:

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
     m_real = m_mag * std::cos (m_theta);
     m_imag = m_mag * std::sin (m_theta);
     m_cartesian = true;
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
     if (m_polar == false) {
       std::cout <<
       "calculate_cartesian failed because the polar representation is invalid"
        << '\n';
       std::exit (1);
     }
     m_real = m_mag * std::cos (m_theta);
     m_imag = m_mag * std::sin (m_theta);
     m_cartesian = true;
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
     assert (m_polar);
     m_real = m_mag * std::cos (m_theta);
     m_imag = m_mag * std::sin (m_theta);
     m_cartesian = true;
     assert (m_polar && m_cartesian);
   }

Assertions are disabled when ``NDEBUG`` is defined. Use ordinary error
handling to validate external input; do not rely on assertions for that.

The first ``assert`` statement checks the precondition (actually just
part of it); the second ``assert`` statement checks the postcondition.

In my development environment, I get the following message when I
violate an assertion:

.. code-block:: text

   complex_number.cpp:63: void complex_number::calculate_polar(): Assertion `m_cartesian' failed.
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

   complex_number::complex_number () { m_cartesian = true;  m_polar = false; }

   complex_number::complex_number (double r, double i) {
     m_real = r;  m_imag = i;
     m_cartesian = true;  m_polar = false;
   }

   void complex_number::calculate_cartesian () {
     assert (m_polar);
     m_real = m_mag * std::cos (m_theta);
     m_imag = m_mag * std::sin (m_theta);
     m_cartesian = true;
     assert (m_polar && m_cartesian);
   }

   double complex_number::real () {
     if (m_cartesian == false) calculate_cartesian ();
     return m_real;
   }

   double complex_number::imag () {
     if (m_cartesian == false) calculate_cartesian ();
     return m_imag;
   }

   void complex_number::calculate_polar () {
     m_mag = std::sqrt(std::pow(m_real, 2) + std::pow(m_imag, 2));
     m_theta = std::atan2(m_imag, m_real);
     m_polar = true;
   }

   double complex_number::mag () {
     if (m_polar == false) {
       calculate_polar ();
     }
     return m_mag;
   }

   double complex_number::theta () {
     if (m_polar == false) {
       calculate_polar ();
     }
     return m_theta;
   }

   void complex_number::print_cartesian () {
     std::cout << real() << " + " << imag() << 'i' << '\n';
   }

   void complex_number::print_polar () {
     std::cout << mag() << " e^ " << theta() << 'i' << '\n';
   }

   complex_number add (complex_number& a, complex_number& b) {
     double m_real = a.real() + b.real();
     double m_imag = a.imag() + b.imag();
     complex_number sum (m_real, m_imag);
     return sum;
   }

   complex_number subtract (complex_number& a, complex_number& b) {
     double m_real = a.real() - b.real();
     double m_imag = a.imag() - b.imag();
     complex_number diff (m_real, m_imag);
     return diff;
   }

   void complex_number::polar (double m, double t) {
     m_mag = m;  m_theta = t;
     m_cartesian = false;  m_polar = true;
   }

   complex_number mult (complex_number& a, complex_number& b) {
     double m_mag = a.mag() * b.mag();
     double m_theta = a.theta() + b.theta();
     complex_number product;
     product.polar (m_mag, m_theta);
     return product;
   }

   void complex_number::cartesian (double r, double i) {
     m_real = r;    m_imag = i;
     m_cartesian = true;  m_polar = false;
   }


.. tb-code:: cpp
   :name: c192_fourteenten
   :caption: Example c192_fourteenten
   :run-after: c192_fourteenten-support

   #include <iostream>
   #include <cmath>
   #include <cassert>

   class complex_number
   {
     double m_real = 0.0, m_imag = 0.0;
     double m_mag = 0.0, m_theta = 0.0;
     bool m_cartesian, m_polar;

   public:
     complex_number ();
     complex_number (double r, double i);
     void calculate_cartesian ();
     double real ();
     double imag ();
     void calculate_polar ();
     double mag ();
     double theta ();
     void print_cartesian ();
     void print_polar ();
     void polar (double m, double t);
     void cartesian (double r, double i);
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
      :regex:
      :match: exit
      :feedback: Correct!
      :incorrect: Incorrect! Try again.
