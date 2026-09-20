Time
----

As a second example of a user-defined structure, we will define a type
called ``Time``, which is used to record the time of day. The various
pieces of information that form a time are the hour, minute and second,
so these will be the instance variables of the structure.

The first step is to decide what type each instance variable should be.
It seems clear that ``hour`` and ``minute`` should be integers. Just to
keep things interesting, let’s make ``second`` a ``double``, so we can
record fractions of a second.

The active code below shows what the structure definition looks like. 
We can create a ``Time`` object in the usual way.

.. tb-code:: cpp
   :name: time_AC_1
   :caption: Example time_AC_1
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>

   struct Time {
       int hour, minute;
       double second;
   };

   int main() {
       Time time = { 11, 59, 3.14159 };
       std::cout << time.hour << ':' << time.minute << ':' << time.second;
   }

The state diagram for this object looks like this:

.. digraph:: state
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

         Click on all the statements that are variables of type ``Price``.  If you make a mistake you can click on the statement again to unhighlight it.

         .. code-block:: cpp

            struct Price {
            int dollar;
            int cents;
            };
            int main() {
                Price sandwich = { 3, 45 };
                Price coffee = { 2, 50 };
                Price pastry = { 2, 0 };
            }


         .. tb-miss:: text:struct Price {

            Variables *use* a type, they are not part of the type.

         .. tb-miss:: text:int dollar;

            Variables *use* a type, they are not part of the type.

         .. tb-miss:: text:int cents;

            Variables *use* a type, they are not part of the type.

         .. tb-miss:: text:};

            Variables *use* a type, they are not part of the type.

         .. tb-miss:: text:int main() {

            Variables *use* a type, they are not part of the type.

         .. tb-hit:: text:Price sandwich = { 3, 45 };

            Correct.

         .. tb-hit:: text:Price coffee = { 2, 50 };

            Correct.

         .. tb-hit:: text:Price pastry = { 2, 0 };

            Correct.

   .. tb-tab:: Q2

      .. tb-click::
         :name: time_2

         Click on all the statements that are instance variables of type ``Price``.

         .. code-block:: cpp

            struct Price {
            int dollar;
            int cents;
            };
            int main() {
                Price sandwich = { 3, 45 };
                Price coffee = { 2, 50 };
                Price pastry = { 2, 0 };
            }


         .. tb-miss:: text:struct Price {

            Try again.

         .. tb-hit:: text:int dollar;

            Correct.

         .. tb-hit:: text:int cents;

            Correct.

         .. tb-miss:: text:};

            Try again.

         .. tb-miss:: text:int main() {

            Try again.

         .. tb-miss:: text:Price sandwich = { 3, 45 };

            Try again.

         .. tb-miss:: text:Price coffee = { 2, 50 };

            Try again.

         .. tb-miss:: text:Price pastry = { 2, 0 };

            Try again.

   .. tb-tab:: Q3

      Try writing the ``printTime`` function in the commented section
      of the active code below. ``printTime`` should print out the time
      in the HOUR:MINUTE:SECONDS format. If you get stuck, you can reveal the extra problem
      at the end for help. 

      .. tb-code:: cpp
         :name: time_AC_2
         :caption: Example time_AC_2
         :compileargs: ['-Wall', '-std=c++11']

         #include <iostream>

         struct Time {
             int hour;
             int minute;
             double second;
         };

         void printTime(Time& time) {
             // ``printTime`` should print out the time in the   
             // HOUR:MINUTE:SECONDS format. Write your implementation here.
         }

         int main() {
             Time time = { 11, 59, 3.14159 };

             // Should output "11:59:3.14159"
             printTime(time);
         }

      .. tb-reveal:: Reveal Problem
         :name: id_9_1_1

         .. tb-parsons::
            :name: time_4

            Let's write the code for the ``printTime`` function. ``printTime`` 
            should print out the time in the HOUR:MINUTE:SECONDS format.

            .. code-block:: cpp

               {{group}}
               void printTime(Time& time) {
               {{endgroup}}
               {{distractor}}
               {{group}}
               Time printTime(Time& time) {
               {{endgroup}}
               {{group}}
                  cout << time.hour << ":" << time.minute << ":" << time.second;
               {{endgroup}}
               {{distractor}}
               {{group}}
                  cout << hour << ":" << minute << ":" << second;
               }
               {{endgroup}}
