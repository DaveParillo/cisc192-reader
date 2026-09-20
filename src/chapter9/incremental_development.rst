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
insight is that a ``time`` is really a three-digit number in base 60!
The ``second`` is the “ones column,” the ``minute`` is the “60’s
column”, and the ``hour`` is the “3600’s column.”

When we wrote ``add_time`` and ``increment``, we were effectively doing
addition in base 60, which is why we had to “carry” from one column to
the next.

Thus an alternate approach to the whole problem is to convert
``time``\ s into ``double``\ s and take advantage of the fact that the
computer already knows how to do arithmetic with ``double``\ s. Here is
a function that converts a ``time`` into a ``double``:

::

   double convert_to_seconds (const time& t) {
     int minutes = t.hour * 60 + t.minute;
     double seconds = minutes * 60 + t.second;
     return seconds;
   }

Now all we need is a way to convert from a ``double`` to a ``time``
object:

::

   time make_time (double secs) {
     time time;
     time.hour = int (secs / 3600.0);
     secs -= time.hour * 3600.0;
     time.minute = int (secs / 60.0);
     secs -= time.minute * 60;
     time.second = secs;
     return time;
   }

You might have to think a bit to convince yourself that the technique I
am using to convert from one base to another is correct. Assuming you
are convinced, we can use these functions to rewrite ``add_time``:

::

   time add_time (const time& t1, const time& t2) {
     double seconds = convert_to_seconds (t1) + convert_to_seconds (t2);
     return make_time (seconds);
   }


The active code below uses the ``convert_to_seconds`` and ``make_time`` functions.

.. tb-code:: cpp
   :name: incremental_development_AC_1
   :caption: Example incremental_development_AC_1
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>
   using namespace std;

   struct time {
       int hour, minute;
       double second;
   };

   void print_time (time& t) {
       cout << t.hour << ':' << t.minute << ':' << t.second << '\n';
   }

   double convert_to_seconds (const time& t) {
       int minutes = t.hour * 60 + t.minute;
       double seconds = minutes * 60 + t.second;
       return seconds;
   }

   time make_time (double secs) {
      time time;
      time.hour = int (secs / 3600.0);
      secs -= time.hour * 3600.0;
      time.minute = int (secs / 60.0);
      secs -= time.minute * 60;
      time.second = secs;
      return time;
   }

   time add_time (const time& t1, const time& t2) {
      double seconds = convert_to_seconds (t1) + convert_to_seconds (t2);
      return make_time (seconds);
   }

   int main() {
      time current_time = { 9, 14, 30.0 };
      time other_time = { 10, 32, 15.2 };
      time done_time = add_time(current_time, other_time);
      print_time (done_time);
   }

This is much shorter than the original version, and it is much easier to
demonstrate that it is correct (assuming, as usual, that the functions
it calls are correct). As an exercise, rewrite ``increment`` the same
way.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      Write your implementation of ``increment`` in the commented area of the active 
      code below. If you get stuck, you can reveal the extra problem at the end for help. 

      .. tb-code:: cpp
         :name: incremental_development_AC_2
         :caption: Example incremental_development_AC_2
         :compileargs: ['-Wall', '-std=c++11']

         #include <iostream>
         using namespace std;

         struct time {
             int hour, minute;
             double second;
         };

         void print_time (time& t) {
             cout << t.hour << ':' << t.minute << ':' << t.second << '\n';
         }

         double convert_to_seconds (const time& t) {
             int minutes = t.hour * 60 + t.minute;
             double seconds = minutes * 60 + t.second;
             return seconds;
         }

         time make_time (double secs) {
             time time;
             time.hour = int (secs / 3600.0);
             secs -= time.hour * 3600.0;
             time.minute = int (secs / 60.0);
             secs -= time.minute * 60;
             time.second = secs;
             return time;
         }

         time add_time (const time& t1, const time& t2) {
             double seconds = convert_to_seconds (t1) + convert_to_seconds (t2);
             return make_time (seconds);
         }

         void increment (time& time, double secs) {
             // This version of ``increment`` should use ``convert_to_seconds``
             // and ``make_time``. Write your implementation here.
         }

         int main() {
             time t1 = { 9, 14, 30.0 };
             increment(t1, 60.0);
             // Should output "9:15:30"
             print_time (t1);

             time t2 = { 9, 59, 45.0 };
             increment(t2, 120.0);
             // Should output "10:1:45"
             print_time (t2);
         }

      .. tb-reveal:: Reveal Problem
         :name: id_9_9_1

         .. tb-parsons::
            :name: incremental_development_1

            Let's write the code for the updated version of the ``increment`` function. ``increment`` 
            adds a number of seconds to a ``time`` object and updates the values
            of the object. This version should use ``convert_to_seconds`` and ``make_time``.

            .. code-block:: cpp

               {{group}}
               void increment (time& time, double secs) {
               {{endgroup}}
               {{distractor}}
               {{group}}
               time increment (time& time, double secs) {
               {{endgroup}}
               {{group}}
                  double seconds = convert_to_seconds (time) + secs;
               {{endgroup}}
               {{distractor}}
               {{group}}
                  double seconds = convert_to_seconds (time);
               {{endgroup}}
               {{group}}
                  time = make_time (seconds);
               }
               {{endgroup}}
               {{distractor}}
               {{group}}
                  return make_time (seconds)
               }
               {{endgroup}}
