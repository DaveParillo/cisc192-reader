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

.. activecode:: time_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:

   The active code below shows what the structure definition looks like. 
   We can create a ``Time`` object in the usual way.
   ~~~~
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


.. tabbed:: self_check

   .. tab:: Q1

      .. clickablearea:: time_1
          :question: Click on all the statements that are variables of type ``Price``.  If you make a mistake you can click on the statement again to unhighlight it.
          :iscode:
          :feedback: Variables *use* a type, they are not part of the type.
          
          :click-incorrect:struct Price {:endclick:
          :click-incorrect:int dollar;:endclick:
          :click-incorrect:int cents;:endclick:
          :click-incorrect:};:endclick:
          :click-incorrect:int main() {:endclick:
              :click-correct:Price sandwich = { 3, 45 };:endclick:
              :click-correct:Price coffee = { 2, 50 };:endclick:
              :click-correct:Price pastry = { 2, 0 };:endclick:
          :click-incorrect:}:endclick:

   .. tab:: Q2

      .. clickablearea:: time_2
          :question: Click on all the statements that are instance variables of type ``Price``.
          :iscode:
          
          :click-incorrect:struct Price {:endclick:
          :click-correct:int dollar;:endclick:
          :click-correct:int cents;:endclick:
          :click-incorrect:};:endclick:
          :click-incorrect:int main() {:endclick:
              :click-incorrect:Price sandwich = { 3, 45 };:endclick:
              :click-incorrect:Price coffee = { 2, 50 };:endclick:
              :click-incorrect:Price pastry = { 2, 0 };:endclick:
          :click-incorrect:}:endclick:

   .. tab:: Q3

      .. activecode:: time_AC_2
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:
 
         Try writing the ``printTime`` function in the commented section
         of the active code below. ``printTime`` should print out the time
         in the HOUR:MINUTE:SECONDS format. If you get stuck, you can reveal the extra problem
         at the end for help. 
         ~~~~
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

      .. reveal:: 9_1_1
         :showtitle: Reveal Problem
         :hidetitle: Hide Problem

         .. parsonsprob:: time_4
            :numbered: left
            :adaptive:
         
            Let's write the code for the ``printTime`` function. ``printTime`` 
            should print out the time in the HOUR:MINUTE:SECONDS format.
            -----
            void printTime(Time& time) {
            =====
            Time printTime(Time& time) {                         #paired
            =====
               cout << time.hour << ":" << time.minute << ":" << time.second;
            =====
               cout << hour << ":" << minute << ":" << second;                        #paired 
            }

