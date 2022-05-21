Incremental development versus planning
---------------------------------------
.. index::
   single: rapid prototyping with iterative improvement

In this chapter I have demonstrated an approach to program development I
refer to as **rapid prototyping with iterative improvement**. In each
case, I wrote a rough draft (or prototype) that performed the basic
calculation, and then tested it on a few cases, correcting flaws as I
found them.

Although this approach can be effective, it can lead to code that is
unnecessarily complicated—since it deals with many special cases—and
unreliable—since it is hard to know if you have found all the errors.

An alternative is high-level planning, in which a little insight into
the problem can make the programming much easier. In this case the
insight is that a ``Time`` is really a three-digit number in base 60!
The ``second`` is the “ones column,” the ``minute`` is the “60’s
column”, and the ``hour`` is the “3600’s column.”

When we wrote ``addTime`` and ``increment``, we were effectively doing
addition in base 60, which is why we had to “carry” from one column to
the next.

Thus an alternate approach to the whole problem is to convert
``Time``\ s into ``double``\ s and take advantage of the fact that the
computer already knows how to do arithmetic with ``double``\ s. Here is
a function that converts a ``Time`` into a ``double``:

::

   double convertToSeconds (const Time& t) {
     int minutes = t.hour * 60 + t.minute;
     double seconds = minutes * 60 + t.second;
     return seconds;
   }

Now all we need is a way to convert from a ``double`` to a ``Time``
object:

::

   Time makeTime (double secs) {
     Time time;
     time.hour = int (secs / 3600.0);
     secs -= time.hour * 3600.0;
     time.minute = int (secs / 60.0);
     secs -= time.minute * 60;
     time.second = secs;
     return time;
   }

You might have to think a bit to convince yourself that the technique I
am using to convert from one base to another is correct. Assuming you
are convinced, we can use these functions to rewrite ``addTime``:

::

   Time addTime (const Time& t1, const Time& t2) {
     double seconds = convertToSeconds (t1) + convertToSeconds (t2);
     return makeTime (seconds);
   }


.. activecode:: incremental_development_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:

   The active code below uses the ``convertToSeconds`` and ``makeTime`` functions.
   ~~~~
   #include <iostream>
   using namespace std;
 
   struct Time {
       int hour, minute;
       double second;
   };
 
   void printTime (Time& t) {
       cout << t.hour << ":" << t.minute << ":" << t.second << endl;
   }
 
   double convertToSeconds (const Time& t) {
       int minutes = t.hour * 60 + t.minute;
       double seconds = minutes * 60 + t.second;
       return seconds;
   }
 
   Time makeTime (double secs) {
      Time time;
      time.hour = int (secs / 3600.0);
      secs -= time.hour * 3600.0;
      time.minute = int (secs / 60.0);
      secs -= time.minute * 60;
      time.second = secs;
      return time;
   }

   Time addTime (const Time& t1, const Time& t2) {
      double seconds = convertToSeconds (t1) + convertToSeconds (t2);
      return makeTime (seconds);
   }

   int main() {
      Time currentTime = { 9, 14, 30.0 };
      Time otherTime = { 10, 32, 15.2 };
      Time doneTime = addTime(currentTime, otherTime);
      printTime (doneTime);
   }

This is much shorter than the original version, and it is much easier to
demonstrate that it is correct (assuming, as usual, that the functions
it calls are correct). As an exercise, rewrite ``increment`` the same
way.

.. tabbed:: self_check

   .. tab:: Q1

      .. activecode:: incremental_development_AC_2
         :language: cpp
         :compileargs: ['-Wall', '-std=c++11']
         :nocodelens:

         Write your implementation of ``increment`` in the commented area of the active 
         code below. If you get stuck, you can reveal the extra problem at the end for help. 
         ~~~~
         #include <iostream>
         using namespace std;
       
         struct Time {
             int hour, minute;
             double second;
         };
       
         void printTime (Time& t) {
             cout << t.hour << ":" << t.minute << ":" << t.second << endl;
         }
       
         double convertToSeconds (const Time& t) {
             int minutes = t.hour * 60 + t.minute;
             double seconds = minutes * 60 + t.second;
             return seconds;
         }
       
         Time makeTime (double secs) {
             Time time;
             time.hour = int (secs / 3600.0);
             secs -= time.hour * 3600.0;
             time.minute = int (secs / 60.0);
             secs -= time.minute * 60;
             time.second = secs;
             return time;
         }
       
         Time addTime (const Time& t1, const Time& t2) {
             double seconds = convertToSeconds (t1) + convertToSeconds (t2);
             return makeTime (seconds);
         }
       
         void increment (Time& time, double secs) {
             // This version of ``increment`` should use ``convertToSeconds``
             // and ``makeTime``. Write your implementation here.
         }

         int main() {
             Time t1 = { 9, 14, 30.0 };
             increment(t1, 60.0);
             // Should output "9:15:30"
             printTime (t1);
       
             Time t2 = { 9, 59, 45.0 };
             increment(t2, 120.0);
             // Should output "10:1:45"
             printTime (t2);
         }

      .. reveal:: 9_9_1
         :showtitle: Reveal Problem
         :hidetitle: Hide Problem

         .. parsonsprob:: incremental_development_1
            :numbered: left
            :adaptive:
         
            Let's write the code for the updated version of the ``increment`` function. ``increment`` 
            adds a number of seconds to a ``Time`` object and updates the values
            of the object. This version should use ``convertToSeconds`` and ``makeTime``.
            -----
            void increment (Time& time, double secs) {
            =====
            Time increment (Time& time, double secs) {                         #paired
            =====
               double seconds = convertToSeconds (time) + secs;
            =====
               double seconds = convertToSeconds (time);                        #paired 
            =====
               time = makeTime (seconds);
            }
            =====
               return makeTime (seconds)                        #paired
            }
