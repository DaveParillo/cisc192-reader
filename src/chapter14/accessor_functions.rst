Accessor functions
------------------

By convention, accessor functions have names that begin with ``get`` and
end with the name of the instance variable they fetch. The return type,
naturally, is the type of the corresponding instance variable.

In this case, the accessor functions give us an opportunity to make sure
that the value of the variable is valid before we return it. Here’s what
``get_real`` looks like:

::

   double complex_number::get_real ()
   {
     if (cartesian == false) calculate_cartesian ();
     return real;
   }

If the ``cartesian`` flag is true then ``real`` contains valid data, and
we can just return it. Otherwise, we have to call ``calculate_cartesian``
to convert from polar coordinates to Cartesian coordinates:

::

   void complex_number::calculate_cartesian ()
   {
     real = mag * std::cos (theta);
     imag = mag * std::sin (theta);
     cartesian = true;
   }

Assuming that the polar coordinates are valid, we can calculate the
Cartesian coordinates using the formulas from the previous section. Then
we set the ``cartesian`` flag, indicating that ``real`` and ``imag`` now
contain valid data.

As an exercise, write a corresponding function called ``calculate_polar``
and then write ``get_mag`` and ``get_theta``. One unusual thing about
these accessor functions is that they are not ``const``, because
invoking them might modify the instance variables.

Take a look at the active code below, which uses the ``get_real``
accessor function.

.. tb-code:: cpp
   :name: c192_fourteenfour
   :caption: Example c192_fourteenfour
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <iostream>
   #include <cmath>

   class complex_number
   {
     double real = 0.0, imag = 0.0;
     double mag = 0.0, theta = 0.0;
     bool cartesian, polar;

   public:
     complex_number () { cartesian = true;  polar = false; }
     complex_number (double r, double i)
     {
       real = r;  imag = i;
       cartesian = true;  polar = false;
     }
     void calculate_cartesian ()
     {
       real = mag * std::cos (theta);
       imag = mag * std::sin (theta);
       cartesian = true;
     }
     double get_real ()
     {
       if (cartesian == false) calculate_cartesian ();
       return real;
     }
     double get_imag ()
     {
       if (cartesian == false) calculate_cartesian ();
       return imag;
     }
   };

   int main() {
     complex_number c1 (5.0, 3.5);
     std::cout << c1.get_real() << ", " << c1.get_imag() << std::endl;
   }

Write your implementation of ``calculate_polar`` in the commented area of the active
code below. Once you're done with that, write the ``get_mag`` and ``get_theta``
accessor functions. Read the comments in ``main`` to see how we'll test if your
functions works. If you get stuck, you can reveal the extra problem at the end for help.

.. tb-code:: cpp
   :name: c192_fourteenfive-support
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


.. tb-code:: cpp
   :name: c192_fourteenfive
   :caption: Example c192_fourteenfive
   :run-after: c192_fourteenfive-support
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
   };

   void complex_number::calculate_polar () {
     // ``calculate_polar`` should convert the real and imaginary parts
     // into magnitude and theta. Use the formula in the previous section.
     // Write your implementation here.
   }

   double complex_number::get_mag () {
     // ``get_mag`` should return the magnitude.
     // Delete the return 0 and write your implementation here.
     return 0;
   }

   double complex_number::get_theta () {
     // ``get_mag`` should return the theta.
     // Delete the return 0 and write your implementation here.
     return 0;
   }

   int main() {
     complex_number c1 (0.0, 1.0);
     // Magnitude should be 1, theta should be pi/2, or about 1.5708
     std::cout << c1.get_mag() << ", " << c1.get_theta() << std::endl;
   }

.. tb-reveal:: Reveal Problem
   :name: c192_14_4_1

   .. tb-parsons::
      :name: c192_question14_4_1

      Let's write the code for the ``calculate_polar`` function.
      Follow the format of the function ``calculate_cartesian``.

      .. code-block:: c++

         {{group}}
         void complex_number::calculate_polar () {
         {{endgroup}}
         {{distractor}}
         {{group}}
         void complex_number::calculate_cartesian () {
         {{endgroup}}
         {{group}}
            mag = std::sqrt(std::pow(real, 2) + std::pow(imag, 2));
         {{endgroup}}
         {{distractor}}
         {{group}}
            mag = std::pow(real, 2) + std::pow(imag, 2);
         {{endgroup}}
         {{group}}
            theta = std::atan2(imag, real);
         {{endgroup}}
         {{group}}
            polar = true;
         }
         {{endgroup}}
         {{distractor}}
         {{group}}
            cartesian = true;
         }
         {{endgroup}}

.. tb-reveal:: Reveal Problem
   :name: c192_14_4_2

   .. tb-parsons::
      :name: c192_question14_4_2

      Let's write the code for the ``get_mag`` function,
      which should return the magnitude of a ``complex_number`` object.

      .. code-block:: c++

         {{group}}
         double complex_number::get_mag () {
         {{endgroup}}
         {{distractor}}
         {{group}}
         void complex_number::get_mag () {
         {{endgroup}}
         {{group}}
            if (polar == false) {
         {{endgroup}}
         {{group}}
               calculate_polar ();
            }
         {{endgroup}}
         {{group}}
            return mag;
         }
         {{endgroup}}

.. tb-reveal:: Reveal Problem
   :name: c192_14_4_3

   .. tb-parsons::
      :name: c192_question14_4_3

      Let's write the code for the ``get_theta`` function,
      which should return the magnitude of a ``complex_number`` object.

      .. code-block:: c++

         {{group}}
         double complex_number::get_theta () {
         {{endgroup}}
         {{distractor}}
         {{group}}
         double complex_number::get_mag () {
         {{endgroup}}
         {{group}}
            if (polar == false) {
         {{endgroup}}
         {{group}}
               calculate_polar ();
            }
         {{endgroup}}
         {{distractor}}
         {{group}}
               calculate_cartesian ();
            }
         {{endgroup}}
         {{group}}
            return theta;
         }
         {{endgroup}}

