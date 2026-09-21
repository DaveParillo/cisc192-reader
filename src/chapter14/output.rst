.. _classes-invariants-output:

Output
------

As usual when we define a new class, we want to be able to output
objects in a human-readable form. For ``complex_number`` objects, we could use
two functions:

::

   void complex_number::print_cartesian ()
   {
     std::cout << real() << " + " << imag() << 'i' << '\n';
   }

   void complex_number::print_polar ()
   {
     std::cout << mag() << " e^ " << theta() << 'i' << '\n';
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

When we invoke ``print_polar``, and ``print_polar`` invokes ``mag``,
the program is forced to convert to polar coordinates and store the
results in the instance variables. The good news is that we only have to
do the conversion once. When ``print_polar`` invokes ``theta``, it
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


.. tb-code:: cpp
   :name: c192_fourteensix
   :caption: Example c192_fourteensix
   :run-after: c192_fourteensix-support

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
        complex c1 (3.0, 4.0);
        // c1.print_cartesian();
        c1.print_polar();
      }

   - [x] 5 e^ 0.927295i

     Correct!
   - [ ] 3 + 4i

     Incorrect! Try using the active code above.
   - [ ] 2 + 3i

     Incorrect! Try using the active code above.
   - [ ] 5 e^ 1

     Incorrect! Try using the active code above.

