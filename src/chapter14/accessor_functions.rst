.. _classes-invariants-accessor-functions:

Accessor functions
------------------

Accessor functions should use the value name directly; the function signature
shows whether the operation reads or writes the value. The return type,
naturally, is the type of the corresponding instance variable.

In this case, the accessor functions give us an opportunity to make sure
that the value of the variable is valid before we return it. Here’s what
``real`` looks like:

::

   double complex_number::real ()
   {
     if (m_cartesian == false) calculate_cartesian ();
     return m_real;
   }

If the ``cartesian`` flag is true then ``real`` contains valid data, and
we can just return it. Otherwise, we have to call ``calculate_cartesian``
to convert from polar coordinates to Cartesian coordinates:

::

   void complex_number::calculate_cartesian ()
   {
     m_real = m_mag * std::cos (m_theta);
     m_imag = m_mag * std::sin (m_theta);
     m_cartesian = true;
   }

Assuming that the polar coordinates are valid, we can calculate the
Cartesian coordinates using the formulas from the previous section. Then
we set the ``cartesian`` flag, indicating that ``real`` and ``imag`` now
contain valid data.

As an exercise, write a corresponding function called ``calculate_polar``
and then write ``mag`` and ``theta``. One unusual thing about
these accessor functions is that they are not ``const``, because
invoking them might modify the instance variables.

Take a look at the active code below, which uses the ``real``
accessor function.

.. tb-code:: cpp
   :name: c192_fourteenfour
   :caption: Example c192_fourteenfour

   #include <iostream>
   #include <cmath>

   class complex_number
   {
     double m_real = 0.0, m_imag = 0.0;
     double m_mag = 0.0, m_theta = 0.0;
     bool m_cartesian, m_polar;

   public:
     complex_number () { m_cartesian = true;  m_polar = false; }
     complex_number (double r, double i)
     {
       m_real = r;  m_imag = i;
       m_cartesian = true;  m_polar = false;
     }
     void calculate_cartesian ()
     {
       m_real = m_mag * std::cos (m_theta);
       m_imag = m_mag * std::sin (m_theta);
       m_cartesian = true;
     }
     double real ()
     {
       if (m_cartesian == false) calculate_cartesian ();
       return m_real;
     }
     double imag ()
     {
       if (m_cartesian == false) calculate_cartesian ();
       return m_imag;
     }
   };

   int main() {
     complex_number c1 (5.0, 3.5);
     std::cout << c1.real() << ", " << c1.imag() << '\n';
   }

Write your implementation of ``calculate_polar`` in the commented area of the active
code below. Once you're done with that, write the ``mag`` and ``theta``
accessor functions. Read the comments in ``main`` to see how we'll test if your
functions works. If you get stuck, you can reveal the extra problem at the end for help.

.. tb-code:: cpp
   :name: c192_fourteenfive-support
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


.. tb-code:: cpp
   :name: c192_fourteenfive
   :caption: Example c192_fourteenfive
   :run-after: c192_fourteenfive-support

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
   };

   void complex_number::calculate_polar () {
     // ``calculate_polar`` should convert the real and imaginary parts
     // into magnitude and theta. Use the formula in the previous section.
     // Write your implementation here.
   }

   double complex_number::mag () {
     // ``mag`` should return the magnitude.
     // Delete the return 0 and write your implementation here.
     return 0;
   }

   double complex_number::theta () {
     // ``mag`` should return the theta.
     // Delete the return 0 and write your implementation here.
     return 0;
   }

   int main() {
     complex_number c1 (0.0, 1.0);
     // Magnitude should be 1, theta should be pi/2, or about 1.5708
     std::cout << c1.mag() << ", " << c1.theta() << '\n';
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
            m_mag = std::sqrt(std::pow(m_real, 2) + std::pow(m_imag, 2));
         {{endgroup}}
         {{distractor}}
         {{group}}
            m_mag = std::pow(m_real, 2) + std::pow(m_imag, 2);
         {{endgroup}}
         {{group}}
            m_theta = std::atan2(m_imag, m_real);
         {{endgroup}}
         {{group}}
            m_polar = true;
         }
         {{endgroup}}
         {{distractor}}
         {{group}}
            m_cartesian = true;
         }
         {{endgroup}}

.. tb-reveal:: Reveal Problem
   :name: c192_14_4_2

   .. tb-parsons::
      :name: c192_question14_4_2

      Let's write the code for the ``mag`` function,
      which should return the magnitude of a ``complex_number`` object.

      .. code-block:: c++

         {{group}}
         double complex_number::mag () {
         {{endgroup}}
         {{distractor}}
         {{group}}
         void complex_number::mag () {
         {{endgroup}}
         {{group}}
            if (m_polar == false) {
         {{endgroup}}
         {{group}}
               calculate_polar ();
            }
         {{endgroup}}
         {{group}}
            return m_mag;
         }
         {{endgroup}}

.. tb-reveal:: Reveal Problem
   :name: c192_14_4_3

   .. tb-parsons::
      :name: c192_question14_4_3

      Let's write the code for the ``theta`` function,
      which should return the magnitude of a ``complex_number`` object.

      .. code-block:: c++

         {{group}}
         double complex_number::theta () {
         {{endgroup}}
         {{distractor}}
         {{group}}
         double complex_number::mag () {
         {{endgroup}}
         {{group}}
            if (m_polar == false) {
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
            return m_theta;
         }
         {{endgroup}}

