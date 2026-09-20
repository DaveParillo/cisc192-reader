..  Copyright (C)  Dave Parillo.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, and Preface,
    no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. include:: <isonum.txt>

.. index:: namespace

Namespaces
----------
All functions in C++ are *by default* global.
Another way of saying this is that they are by default in the *global namespace*.
The ``namespace`` keyword provides a mechanism
to avoid polluting the global namespace with too many names.


A ``namespace`` is simply a named block that defines a scope.
Namespaces provide a method for preventing name conflicts in large projects.

Symbols declared inside a namespace block are placed in a named scope that 
prevents them from being mistaken for identically-named symbols in other scopes.

Multiple namespace blocks with the same name are allowed. 
All declarations within those blocks are declared in the named scope.

.. code-block:: cpp

   // declare some things in the mesa namespace
   namespace mesa {
     int i = 0;
     double pi = 3.1416;
     void details (char);
   }

   void mesa::details (char c) { // define the function declared earlier
     std::cout << int{c};
   }

   //void mesa::oops () {       // error: oops not yet declared in mesa namespace
   //}

   namespace mesa {      // a separate mesa namespace block
     void oops ();       // a declaration with no definition is allowed
     namespace cisc {
       double pi = 3.141592653;  // not the same variable as mesa::pi
     }
   }

   int main () {
     using mesa::cisc::pi;  // we can specify a name to treat as if it was global
     pi = 3.f;
     mesa::details('a');
   }

   

The larger your project, the more important it is to partition the global namespace.
By default, all symbols are declared in the *global namespace* (``::``).

What is the problem with the global namespace?

- There is only 1 of them
- Name conflicts can be common on large projects
- Complicates mixing third party libraries

Well-behaved third party libraries will not put much (if anything) in the global namespace.

You can put anything in a namespace, except ``main``.
The function main has a few special rules and one is that it must be in the global namespace.

The ``using`` directive allows all the names in a namespace to be used 
without the namespace-name as an explicit qualifier. 
Use a using directive in an implementation file (i.e. ``*.cpp``) 
if you are using several different identifiers in a namespace; 
if you are just using one or two identifiers, 
then consider a using declaration to only bring those identifiers into scope 
and not all the identifiers in the namespace. 
If a local variable has the same name as a namespace variable, 
the namespace variable is hidden. 
It is an error to have a namespace variable with the same name as a global variable.

-----

.. admonition:: More to Explore

  - From cppreference.com: 
    :lang:`namespace declarations <namespace>`

