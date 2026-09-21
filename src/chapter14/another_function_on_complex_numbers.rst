.. _classes-invariants-another-function-on-complexnumber-numbers:

Another function on ``complex_number`` numbers
----------------------------------------------

Another operation we might want is multiplication. Unlike addition,
multiplication is easy if the numbers are in polar coordinates and hard
if they are in Cartesian coordinates (well, a little harder, anyway).

In polar coordinates, we can just multiply the magnitudes and add the
angles. As usual, we can use the accessor functions without worrying
about the representation of the objects.

::

   complex_number mult (complex_number& a, complex_number& b)
   {
     double m_mag = a.mag() * b.mag();
     double m_theta = a.theta() + b.theta();
     complex_number product;
     product.polar (m_mag, m_theta);
     return product;
   }

A small problem we encounter here is that we have no constructor that
accepts polar coordinates. It would be nice to write one, but remember
that we can only overload a function (even a constructor) if the
different versions take different parameters. In this case, we would
like a second constructor that also takes two ``double``\ s, and we
can’t have that.

An alternative it to provide an accessor function that *sets* the
instance variables. In order to do that properly, though, we have to
make sure that when ``mag`` and ``theta`` are set, we also set the
``polar`` flag. At the same time, we have to make sure that the
``cartesian`` flag is unset. That’s because if we change the polar
coordinates, the cartesian coordinates are no longer valid.

::

   void complex_number::polar (double m, double t)
   {
     m_mag = m;  m_theta = t;
     m_cartesian = false;  m_polar = true;
   }

As an exercise, write the corresponding function named ``cartesian``.

To test the ``mult`` function, we can try something like:

::

     complex_number c1 (2.0, 3.0);
     complex_number c2 (3.0, 4.0);

     complex_number product = mult (c1, c2);
     product.print_cartesian();

The output of this program is

::

   -6 + 17i

The active code below uses the ``mult`` and ``polar`` functions.
Feel free to modify the code and experiment around!

.. tb-code:: cpp
   :name: c192_fourteeneight-support
   :hidden:

   complex_number::complex_number () { m_cartesian = true;  m_polar = false; }

   complex_number::complex_number (double r, double i) {
     m_real = r;  m_imag = i;
     m_cartesian = true;  m_polar = false;
   }

   void complex_number::calculate_cartesian () {
     m_real = m_mag * std::cos (m_theta);
     m_imag = m_mag * std::sin (m_theta);
     m_cartesian = true;
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


.. tb-code:: cpp
   :name: c192_fourteeneight
   :caption: Example c192_fourteeneight
   :run-after: c192_fourteeneight-support

   #include <iostream>
   #include <cmath>

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
   };

   complex_number add (complex_number& a, complex_number& b);
   complex_number subtract (complex_number& a, complex_number& b);
   complex_number mult (complex_number& a, complex_number& b);

   int main() {
     complex_number c1 (2.0, 3.0);
     complex_number c2 (3.0, 4.0);
     complex_number product = mult (c1, c2);
     product.print_cartesian();
   }

There is a lot of conversion going on in this program behind the scenes.
When we call ``mult``, both arguments get converted to polar
coordinates. The result is also in polar format, so when we invoke
``print_cartesian`` it has to get converted back. Really, it’s amazing
that we get the right answer!

.. tb-choice::
   :name: question14_7_1

   What is the correct output of the code below?

   .. code-block:: cpp

      int main() {
        complex c1 (2.0, 3.0);
        complex c2 (3.0, 4.0);
        complex c3 (1.0, 0.0);
        complex c4 (3.5, 2.5);
        complex product = mult (c1, c2);
        complex diff = subtract (c4, c3);
        complex sum = add (product, diff);
        sum.print_cartesian();
      }

   - [ ] 3.5 + 19.5i

     Incorrect! Try using the active code above.
   - [x] -3.5 + 19.5i

     Correct!
   - [ ] -3.5 - 19.5i

     Incorrect! Try using the active code above.
   - [ ] -3.5 + 19.5

     Incorrect! Try using the active code above.

Now let's try implementing the ``cartesian`` function. Write your
implementation in the commented area of the active code below.
Read the comments in ``main`` to test out your code! If you get stuck,
you can reveal the extra problem at the end for help.

.. tb-code:: cpp
   :name: c192_fourteennine-support
   :hidden:

   complex_number::complex_number () { m_cartesian = true;  m_polar = false; }

   complex_number::complex_number (double r, double i) {
     m_real = r;  m_imag = i;
     m_cartesian = true;  m_polar = false;
   }

   void complex_number::calculate_cartesian () {
     m_real = m_mag * std::cos (m_theta);
     m_imag = m_mag * std::sin (m_theta);
     m_cartesian = true;
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


.. tb-code:: cpp
   :name: c192_fourteennine
   :caption: Example c192_fourteennine
   :run-after: c192_fourteennine-support

   #include <iostream>
   #include <cmath>

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

   void complex_number::cartesian (double r, double i) {
     // ``cartesian`` should set real and imag to
     // r and i respectively and set the cartesian flag.
     // Write your implementation here.
   }

   complex_number add (complex_number& a, complex_number& b);
   complex_number subtract (complex_number& a, complex_number& b);
   complex_number mult (complex_number& a, complex_number& b);

   int main() {
     complex_number c1 (2.0, 3.0);
     complex_number c2 (3.0, 4.0);
     complex_number product = mult (c1, c2);
     product.print_cartesian();
     // Should output 1.5 + 2.7i
     product.cartesian(1.5, 2.7);
     product.print_cartesian();
   }

.. tb-reveal:: Reveal Problem
   :name: c192_14_7_1

   .. tb-parsons::
      :name: c192_question14_7_2

      Let's write the code for the ``cartesian`` function.

      .. code-block:: c++

         {{group}}
         void complex_number::cartesian (double r, double i) {
         {{endgroup}}
         {{distractor}}
         {{group}}
         complex_number complex_number::cartesian (double r, double i) {
         {{endgroup}}
         {{group}}
            m_real = r;    m_imag = i;
         {{endgroup}}
         {{distractor}}
         {{group}}
            m_real = i;    m_imag = r;
         {{endgroup}}
         {{group}}
            m_cartesian = true;  m_polar = false;
         {{endgroup}}
         {{distractor}}
         {{group}}
            m_cartesian = false;  m_polar = true;
         {{endgroup}}
         {{group}}
         }
         {{endgroup}}

