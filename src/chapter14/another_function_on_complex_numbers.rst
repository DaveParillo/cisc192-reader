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
     double mag = a.get_mag() * b.get_mag();
     double theta = a.get_theta() + b.get_theta();
     complex_number product;
     product.set_polar (mag, theta);
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

   void complex_number::set_polar (double m, double t)
   {
     mag = m;  theta = t;
     cartesian = false;  polar = true;
   }

As an exercise, write the corresponding function named ``set_cartesian``.

To test the ``mult`` function, we can try something like:

::

     complex_number c1 (2.0, 3.0);
     complex_number c2 (3.0, 4.0);

     complex_number product = mult (c1, c2);
     product.print_cartesian();

The output of this program is

::

   -6 + 17i

The active code below uses the ``mult`` and ``set_polar`` functions.
Feel free to modify the code and experiment around!

.. tb-code:: cpp
   :name: c192_fourteeneight-support
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


.. tb-code:: cpp
   :name: c192_fourteeneight
   :caption: Example c192_fourteeneight
   :run-after: c192_fourteeneight-support
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
     void set_polar (double m, double t);
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
        Complex c1 (2.0, 3.0);
        Complex c2 (3.0, 4.0);
        Complex c3 (1.0, 0.0);
        Complex c4 (3.5, 2.5);
        Complex product = mult (c1, c2);
        Complex diff = subtract (c4, c3);
        Complex sum = add (product, diff);
        sum.printCartesian();
      }

   - [ ] 3.5 + 19.5i

     Incorrect! Try using the active code above.
   - [x] -3.5 + 19.5i

     Correct!
   - [ ] -3.5 - 19.5i

     Incorrect! Try using the active code above.
   - [ ] -3.5 + 19.5

     Incorrect! Try using the active code above.

Now let's try implementing the ``set_cartesian`` function. Write your
implementation in the commented area of the active code below.
Read the comments in ``main`` to test out your code! If you get stuck,
you can reveal the extra problem at the end for help.

.. tb-code:: cpp
   :name: c192_fourteennine-support
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


.. tb-code:: cpp
   :name: c192_fourteennine
   :caption: Example c192_fourteennine
   :run-after: c192_fourteennine-support
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
     void set_polar (double m, double t);
     void set_cartesian (double r, double i);
   };

   void complex_number::set_cartesian (double r, double i) {
     // ``set_cartesian`` should set real and imag to
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
     product.set_cartesian(1.5, 2.7);
     product.print_cartesian();
   }

.. tb-reveal:: Reveal Problem
   :name: c192_14_7_1

   .. tb-parsons::
      :name: c192_question14_7_2

      Let's write the code for the ``set_cartesian`` function.

      .. code-block:: c++

         {{group}}
         void complex_number::set_cartesian (double r, double i) {
         {{endgroup}}
         {{distractor}}
         {{group}}
         complex_number complex_number::set_cartesian (double r, double i) {
         {{endgroup}}
         {{group}}
            real = r;    imag = i;
         {{endgroup}}
         {{distractor}}
         {{group}}
            real = i;    imag = r;
         {{endgroup}}
         {{group}}
            cartesian = true;  polar = false;
         {{endgroup}}
         {{distractor}}
         {{group}}
            cartesian = false;  polar = true;
         {{endgroup}}
         {{group}}
         }
         {{endgroup}}

