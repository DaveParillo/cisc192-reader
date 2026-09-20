.. _more-structures-time:

time
----

As a second example of a user-defined structure, we will define a type
called ``time``, which is used to record the time of day. The various
pieces of information that form a time are the hour, minute and second,
so these will be the instance variables of the structure.

The first step is to decide what type each instance variable should be.
It seems clear that ``hour`` and ``minute`` should be integers. Just to
keep things interesting, let’s make ``second`` a ``double``, so we can
record fractions of a second.

The active code below shows what the structure definition looks like. 
We can create a ``time`` object in the usual way.

.. tb-code:: cpp
   :name: time_AC_1
   :caption: Example time_AC_1

   #include <iostream>

   struct time {
       int hour, minute;
       double second;
   };

   int main() {
       time time = { 11, 59, 3.14159 };
       std::cout << time.hour << ':' << time.minute << ':' << time.second;
   }

The state diagram in :numref:`fig_time_state` shows this object:

.. digraph:: state
   :name: fig_time_state
   :caption: Time object state diagram
   :alt: time object state diagram showing hour, minute, and second fields
   :align: center

   graph [compound = true,
          rankdir = "LR",
          nodesep = 0
          ranksep = 0.1]
   node [fontname = "Bitstream Vera Sans",
         shape=plain]
   edge [style = invis]
 
   subgraph cluster_time {
    "hour:   " -> "          11"
    "minute:" -> "          59"
    "second:" -> "3.14159"
   }
   time


.. index::
   single: instance

The word **instance** is sometimes used when we talk about objects,
because every object is an instance (or example) of some type. The
reason that instance variables are so-named is that every instance of a
type has a copy of the instance variables for that type.


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-click::
         :name: time_1

         Click on all the statements that are variables of type ``price``.  If you make a mistake you can click on the statement again to unhighlight it.

         .. code-block:: cpp

            struct price {
            int dollar;
            int cents;
            };
            int main() {
                price sandwich = { 3, 45 };
                price coffee = { 2, 50 };
                price pastry = { 2, 0 };
            }


         .. tb-miss:: text:struct price {

            Variables *use* a type, they are not part of the type.

         .. tb-miss:: text:int dollar;

            Variables *use* a type, they are not part of the type.

         .. tb-miss:: text:int cents;

            Variables *use* a type, they are not part of the type.

         .. tb-miss:: text:};

            Variables *use* a type, they are not part of the type.

         .. tb-miss:: text:int main() {

            Variables *use* a type, they are not part of the type.

         .. tb-hit:: text:price sandwich = { 3, 45 };

            Correct.

         .. tb-hit:: text:price coffee = { 2, 50 };

            Correct.

         .. tb-hit:: text:price pastry = { 2, 0 };

            Correct.

   .. tb-tab:: Q2

      .. tb-click::
         :name: time_2

         Click on all the statements that are instance variables of type ``price``.

         .. code-block:: cpp

            struct price {
            int dollar;
            int cents;
            };
            int main() {
                price sandwich = { 3, 45 };
                price coffee = { 2, 50 };
                price pastry = { 2, 0 };
            }


         .. tb-miss:: text:struct price {

            Try again.

         .. tb-hit:: text:int dollar;

            Correct.

         .. tb-hit:: text:int cents;

            Correct.

         .. tb-miss:: text:};

            Try again.

         .. tb-miss:: text:int main() {

            Try again.

         .. tb-miss:: text:price sandwich = { 3, 45 };

            Try again.

         .. tb-miss:: text:price coffee = { 2, 50 };

            Try again.

         .. tb-miss:: text:price pastry = { 2, 0 };

            Try again.

   .. tb-tab:: Q3

      Try writing the ``print_time`` function in the commented section
      of the active code below. ``print_time`` should print out the time
      in the HOUR:MINUTE:SECONDS format. If you get stuck, you can reveal the extra problem
      at the end for help. 

      .. tb-code:: cpp
         :name: time_AC_2
         :caption: Example time_AC_2

         #include <iostream>

         struct time {
             int hour;
             int minute;
             double second;
         };

         void print_time(time& time) {
             // ``print_time`` should print out the time in the   
             // HOUR:MINUTE:SECONDS format. Write your implementation here.
         }

         int main() {
             time time = { 11, 59, 3.14159 };

             // Should output "11:59:3.14159"
             print_time(time);
         }

      .. tb-reveal:: Reveal Problem
         :name: id_9_1_1

         .. tb-parsons::
            :name: time_4

            Let's write the code for the ``print_time`` function. ``print_time`` 
            should print out the time in the HOUR:MINUTE:SECONDS format.

            .. code-block:: cpp

               {{group}}
               void print_time(time& time) {
               {{endgroup}}
               {{distractor}}
               {{group}}
               time print_time(time& time) {
               {{endgroup}}
               {{group}}
                  cout << time.hour << ':' << time.minute << ':' << time.second;
               {{endgroup}}
               {{distractor}}
               {{group}}
                  cout << hour << ':' << minute << ':' << second;
               }
               {{endgroup}}
