..  Copyright (C)  Dave Parillo.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, and Preface,
    no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".
   
.. index::
   single: constants
   pair: keyword; const

Constants
=========
As useful as variables are, sometimes we need to ensure
a values does **not** change after initialization.
We use :cref:`const` to instruct the compiler to hold something constant.

Programs typically use a lot of constants.
Mathematical constants like :math:`\pi`, or :math:`e`, and unit conversions are common.
Obviously, it would be bad if a program changed the value of :math:`\pi` in the middle
of its execution.
As programmers, we can make a promise to never change those variables that should
not change.
But the language allows a way to enforce the idea.
For example:

.. code-block:: cpp

   const double pi = 3.14159265359;

   double area = pi * r * r;           // OK to read pi like any other variable

There are two restrictions when using constants:

#. Constants cannot be changed after initialization.

   .. code-block:: cpp

      const double pi = 3.14159265359;
      pi = 3;                        // this is a compile error

#. Constants must be initialized when declared.

   .. code-block:: cpp

      const double pi;               // this is a compile error
      pi = 3.14159265359;

.. index::
   pair: parameter passing; const reference

.. index:: const vs define

**Prefer ``const`` to ``#define``**

Before C++ created the ``const`` keyword, a feature in the
C pre-processor: ``#define`` was used instead:

.. code-block:: cpp

   #define PI 3.14159265359;

C++ inherits this feature from C and you'll see it used in lots
of legacy code, so you should know it exists.
Although C++ allows us to define symbols in this way,
we prefer using ``const`` over ``#define`` when possible.

There are good reasons to avoid ``#define`` when alternatives exist.

``#define`` is parsed by the *C pre-processor*, not the compiler.
This mean that all ``#define`` directives are just text.
Fundamentally they are no different from any other pre-processor 
directive (``#include``, ``#ifdef``, etc.),
except people commonly use ``#define`` as a placeholder for a numeric type,
or a function.

So given:

.. code-block:: cpp

   #define ASPECT_RATIO 1.653

the pre-processor literally copies the value '1.653' every place in the source code
it encounters the string 'ASPECT_RATIO'.
Then the program is compiled.


Prefer this instead:

.. code-block:: cpp

   const double ASPECT_RATIO = 1.653;

-----

.. admonition:: More to Explore

  - From: cppreference.com: 
    :lang:`const qualifier <cv>` and 
    :lang:`constexpr <constant_expression>` 
  - `C++ Core Guidelines for constexpr 
    <https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr>`_





