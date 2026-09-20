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
     double real = 0.0, imag = 0.0;
     double mag = 0.0, theta = 0.0;
     bool cartesian, polar;

     void calculate_cartesian ();
     void calculate_polar ();

   public:
     complex_number () { cartesian = true;  polar = false; }

     complex_number (double r, double i)
     {
       real = r;  imag = i;
       cartesian = true;  polar = false;
     }

     void print_cartesian ();
     void print_polar ();

     double get_real ();
     double get_imag ();
     double get_mag ();
     double get_theta ();

     void set_cartesian (double r, double i);
     void set_polar (double m, double t);
   };

The ``private`` label at the beginning is not necessary, but it is a
useful reminder.

The active code below updates ``calculate_polar`` and ``calculate_cartesian``
to be private functions. Notice how we are no longer able to call
``calculate_cartesian`` in main. Feel free to modify the code and experiment around!

.. tb-code:: cpp
   :name: c192_fourteeneleven-support
   :hidden:

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
     std::cout << get_real() << " + " << get_imag() << 'i' << '\n';
   }

   void complex_number::print_polar () {
     std::cout << get_mag() << " e^ " << get_theta() << 'i' << '\n';
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
   :name: c192_fourteeneleven
   :caption: Example c192_fourteeneleven
   :run-after: c192_fourteeneleven-support

   #include <iostream>
   #include <cmath>
   #include <cassert>

   class complex_number
   {
     double real = 0.0, imag = 0.0;
     double mag = 0.0, theta = 0.0;
     bool cartesian, polar;
     void calculate_cartesian ();
     void calculate_polar ();

   public:
     complex_number ();
     complex_number (double r, double i);
     double get_real ();
     double get_imag ();
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
     complex_number c1(-4.0, 0.0);
     c1.set_polar(4.0, 3.1415);
     // ``calculate_cartesian`` can't be called in main because
     // it is now a private member function
     c1.calculate_cartesian();
   }

