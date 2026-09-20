Output
------

As usual when we define a new class, we want to be able to output
objects in a human-readable form. For ``complex_number`` objects, we could use
two functions:

::

   void complex_number::print_cartesian ()
   {
     std::cout << get_real() << " + " << get_imag() << "i" << std::endl;
   }

   void complex_number::print_polar ()
   {
     std::cout << get_mag() << " e^ " << get_theta() << "i" << std::endl;
   }

The nice thing here is that we can output any ``complex_number`` object in
either format without having to worry about the representation. Since
the output functions use the accessor functions, the program will
compute automatically any values that are needed.

The following code creates a ``complex_number`` object using the second
constructor. Initially, it is in Cartesian format only. When we invoke
``print_cartesian`` it accesses ``real`` and ``imag`` without having to
do any conversions.

::

     complex_number c1 (2.0, 3.0);

     c1.print_cartesian();
     c1.print_polar();

When we invoke ``print_polar``, and ``print_polar`` invokes ``get_mag``,
the program is forced to convert to polar coordinates and store the
results in the instance variables. The good news is that we only have to
do the conversion once. When ``print_polar`` invokes ``get_theta``, it
will see that the polar coordinates are valid and return ``theta``
immediately.

The output of this code is:

::

   2 + 3i
   3.60555 e^ 0.982794i

The active code below uses the print functions for ``complex_number`` objects.
Feel free to modify the code and experiment around!

.. tb-code:: cpp
   :name: c192_fourteensix-support
   :hidden:
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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
     std::cout << get_real() << " + " << get_imag() << "i" << std::endl;
   }

   void complex_number::print_polar () {
     std::cout << get_mag() << " e^ " << get_theta() << "i" << std::endl;
   }


.. tb-code:: cpp
   :name: c192_fourteensix
   :caption: Example c192_fourteensix
   :run-after: c192_fourteensix-support
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

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

   int main() {
     complex_number c1 (2.0, 3.0);
     c1.print_cartesian();
     c1.print_polar();
   }

.. tb-choice::
   :name: question14_5_1

   What is the correct output of the code below?

   .. code-block:: cpp

      int main() {
        Complex c1 (3.0, 4.0);
        // c1.printCartesian();
        c1.printPolar();
      }

   - [x] 5 e^ 0.927295i

     Correct!
   - [ ] 3 + 4i

     Incorrect! Try using the active code above.
   - [ ] 2 + 3i

     Incorrect! Try using the active code above.
   - [ ] 5 e^ 1

     Incorrect! Try using the active code above.

