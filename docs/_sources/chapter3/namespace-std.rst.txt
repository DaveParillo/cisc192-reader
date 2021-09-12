..  Copyright (C)  Dave Parillo.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, and Preface,
    no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. include:: <isonum.txt>

.. index::
   pair: namespace; using directive

Prefer using declarations to ``using namespace std``
----------------------------------------------------
What's wrong with ``using namespace std;``?

Nothing, technically.
You see it commonly in examples on the web and often the intent is
to make an example appear as simple as possible with no extra clutter.

**BUT**

The using-directive ``using namespace std;`` at any namespace scope introduces 
*every* name from the namespace ``std`` into the global namespace,
which may lead to undesirable name collisions. 
This, and other using directives are generally considered bad practice 
at file scope of a header file.
Additionally, shadowing names in the standard namespace can lead to unexpected behaviors.


.. tabbed:: namespace

   .. tab:: Example: namespace std

      It can be hard to remember every name that might be
      imported when ``using namespace std;``.
      Even when only 1 header is included.

      The following example seems innocent enough,
      until you learn that :io:`showpoint<manip/showpoint>` is a name
      in ``std::ios``

      Run the following example twice,
      first as is, then remove the line ``bool showpoint = true;``:

      .. activecode:: ac_using_namespace_std_1
         :language: cpp
         :nocodelens:

         #include <iostream>

         using namespace std;

         int main () {
           bool showpoint = true; 

           cout << "1.0 with showpoint: " << showpoint << 1.0 << '\n'
                << "1.0 with noshowpoint: " << noshowpoint << 1.0 << '\n';

         }
   
Errors using namespace directives are seldom this obviously wrong.


.. index::
   pair: Herb Sutter; namespace using
   pair: Andrei Alexandrescu; namespace using

One final word from two experts:

  **Summary**

  Namespace usings are for your convenience, not for you to inflict on others: 
  Never write a ``using`` declaration or a ``using`` directive before an ``#include`` directive.

  Corollary: In header files, 
  don’t write namespace-level using directives or using declarations; 
  instead, explicitly namespace-qualify all names. 
  (The second rule follows from the first, 
  because headers can never know what other header ``#include`` might appear after them.)

  **Discussion**

  In short: 
  You can and should use namespace using declarations and directives liberally 
  in your implementation files after ``#include`` directives and feel good about it. 
  Despite repeated assertions to the contrary, 
  namespace ``using`` declarations and directives are not evil and they do not defeat the purpose of namespaces. 
  Rather, they are what make namespaces usable.

  -- Herb Sutter and Andrei Alexandrescu, C++ Coding Standards


-----

.. admonition:: More to Explore

  - From: cppreference.com: 
    :lang:`namespace declarations <namespace>` and 
    :lang:`namespace aliases <namespace_alias>`

  - From stack overflow:
    `Why is using namespace std considered bad practice? <https://stackoverflow.com/questions/1452721/why-is-using-namespace-std-considered-bad-practice>`_


