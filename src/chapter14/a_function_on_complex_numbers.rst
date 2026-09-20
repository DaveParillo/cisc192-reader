.. _classes-invariants-a-function-on-complexnumber-numbers:

A function on ``complex_number`` numbers
----------------------------------------

A natural operation we might want to perform on complex numbers is
addition. If the numbers are in Cartesian coordinates, addition is easy:
you just add the real parts together and the imaginary parts together.
If the numbers are in polar coordinates, it is easiest to convert them
to Cartesian coordinates and then add them.

Again, it is easy to deal with these cases if we use the accessor
functions:

::

   complex_number add (complex_number& a, complex_number& b)
   {
     double real = a.get_real() + b.get_real();
     double imag = a.get_imag() + b.get_imag();
     complex_number sum (real, imag);
     return sum;
   }

Notice that the arguments to ``add`` are not ``const`` because they
might be modified when we invoke the accessors. To invoke this function,
we would pass both operands as arguments:

::

     complex_number c1 (2.0, 3.0);
     complex_number c2 (3.0, 4.0);

     complex_number sum = add (c1, c2);
     sum.print_cartesian();

The output of this program is

::

   5 + 7i

The active code below uses the ``add`` function for ``complex_number`` objects.
As an exercise, write the ``subtract`` function for ``complex_number`` objects
in the commented area of the active code. If you get stuck, you can reveal
the extra problem at the end for help. Once you are finished, feel
free to modify the code and experiment around!

.. tb-code:: cpp
   :name: c192_fourteenseven-support
   :hidden:

   complex_number::complex_number () { cartesian = true;  polar = false; }

   complex_number::complex_number (double r, double i) {
     real = r;  imag = i;
     cartesian = true;  polar = false;
   }

   void complex_number::calculate_cartesian () {
     real = mag * std::cos (theta);
     imag = mag * std::sin (theta);
     cartesian = true;
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


.. tb-code:: cpp
   :name: c192_fourteenseven
   :caption: Example c192_fourteenseven
   :run-after: c192_fourteenseven-support

   #include <iostream>
   #include <cmath>

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
   };

   complex_number add (complex_number& a, complex_number& b);
   complex_number subtract (complex_number& a, complex_number& b) {
     // ``subtract`` should subtract b from a and return
     // the difference of the two ``complex_number`` objects.
     // Delete the existing code and write your implementation here.
     complex_number c (0,0); return c;
   }

   int main() {
     complex_number c1 (2.0, 3.0);
     complex_number c2 (3.0, 4.0);
     complex_number sum = add (c1, c2);
     sum.print_cartesian();

     // Difference should be 1 + 1i
     complex_number diff = subtract(c2, c1);
     diff.print_cartesian();
   }

.. tb-reveal:: Reveal Problem
   :name: c192_14_6_1

   .. tb-parsons::
      :name: c192_question14_6_1

      Let's write the code for the ``subtract`` function,
      which should return the difference of two ``complex_number`` objects.

      .. code-block:: c++

         {{group}}
         complex_number subtract (complex_number& a, complex_number& b) {
         {{endgroup}}
         {{distractor}}
         {{group}}
         complex_number subtract (complex_number& a) {
         {{endgroup}}
         {{group}}
            double real = a.get_real() - b.get_real();
         {{endgroup}}
         {{distractor}}
         {{group}}
            double real = a.get_real() + b.get_real();
         {{endgroup}}
         {{group}}
            double imag = a.get_imag() - b.get_imag();
         {{endgroup}}
         {{group}}
            complex_number diff (real, imag);
         {{endgroup}}
         {{distractor}}
         {{group}}
            complex_number diff (imag, real);
         {{endgroup}}
         {{group}}
            return diff;
         }
         {{endgroup}}
         {{distractor}}
         {{group}}
            return sum;
         }
         {{endgroup}}

.. tb-choice::
   :name: question14_6_2

   What is the correct output of the code below?

   .. code-block:: cpp

      int main() {
        complex c1 (2.5, 1.3);
        complex c2 (3.9, 4.4);
        complex c3 (9.5, 7.6);
        complex sum = add (c1, c2);
        complex diff = subtract(c3, sum);
        diff.print_cartesian();
      }

   - [ ] 3.1i + 1.9i

     Incorrect! Try using the active code above.
   - [ ] 1.9i + 3.1

     Incorrect! Try using the active code above.
   - [ ] 3.0 + 1.9i

     Incorrect! Try using the active code above.
   - [x] 3.1 + 1.9i

     Correct!

