.. _classes-invariants-private-functions:

Private functions
-----------------

In some cases, there are member functions that are used internally by a
class, but that should not be invoked by client programs. For example,
``calculate_polar`` and ``calculate_cartesian`` are used by the accessor
functions, but there is probably no reason clients should call them
directly (although it would not do any harm). If we wanted to protect
these functions, we could declare them ``private`` the same way we do
with instance variables. In that case the complete class definition for
``complex_number`` would look like:

::

   class complex_number
   {
   private:
     double m_real = 0.0, m_imag = 0.0;
     double m_mag = 0.0, m_theta = 0.0;
     bool m_cartesian, m_polar;

     void calculate_cartesian ();
     void calculate_polar ();

   public:
     complex_number () { m_cartesian = true;  m_polar = false; }

     complex_number (double r, double i)
     {
       m_real = r;  m_imag = i;
       m_cartesian = true;  m_polar = false;
     }

     void print_cartesian ();
     void print_polar ();

     double real ();
     double imag ();
     double mag ();
     double theta ();

     void cartesian (double r, double i);
     void polar (double m, double t);
   };

The ``private`` label at the beginning is not necessary, but it is a
useful reminder.

The active code below updates ``calculate_polar`` and ``calculate_cartesian``
to be private functions. Notice how we are no longer able to call
``calculate_cartesian`` in main. Feel free to modify the code and experiment around!

.. tb-code:: cpp
   :name: c192_fourteeneleven-support
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
   :name: c192_fourteeneleven
   :caption: Example c192_fourteeneleven
   :run-after: c192_fourteeneleven-support

   #include <iostream>
   #include <cmath>
   #include <cassert>

   class complex_number
   {
     double m_real = 0.0, m_imag = 0.0;
     double m_mag = 0.0, m_theta = 0.0;
     bool m_cartesian, m_polar;
     void calculate_cartesian ();
     void calculate_polar ();

   public:
     complex_number ();
     complex_number (double r, double i);
     double real ();
     double imag ();
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
     complex_number c1(-4.0, 0.0);
     c1.polar(4.0, 3.1415);
     // ``calculate_cartesian`` can't be called in main because
     // it is now a private member function
     c1.calculate_cartesian();
   }

