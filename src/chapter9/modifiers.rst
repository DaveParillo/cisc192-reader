Modifiers
---------

Of course, sometimes you *want* to modify one of the arguments.
Functions that do are called modifiers.

As an example of a modifier, consider ``increment``, which adds a given
number of seconds to a ``Time`` object. Again, a rough draft of this
function looks like:

::

   void increment (Time& time, double secs) {
     time.second += secs;

     if (time.second >= 60.0) {
       time.second -= 60.0;
       time.minute += 1;
     }
     if (time.minute >= 60) {
       time.minute -= 60;
       time.hour += 1;
     }
   }

The first line performs the basic operation; the remainder deals with
the special cases we saw before.

Is this function correct? What happens if the argument ``secs`` is much
greater than 60? In that case, it is not enough to subtract 60 once; we
have to keep doing it until ``second`` is below 60. We can do that by
replacing the ``if`` statements with ``while`` statements:


The active code below uses the ``increment`` function.
Run the active code to see what the output is!

.. tb-code:: cpp
   :name: modifiers_AC_1
   :caption: Example modifiers_AC_1
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>

   struct Time {
       int hour, minute;
       double second;
   };

   void printTime (Time& t) {
       std::cout << t.hour << ":" << t.minute << ":" << t.second << std::endl;
   }

   void increment (Time& time, double secs) {
       time.second += secs;
       while (time.second >= 60.0) {
           time.second -= 60.0;
           time.minute += 1;
       }
       while (time.minute >= 60) {
           time.minute -= 60;
           time.hour += 1;
       }
   }

   int main() {
       Time currentTime = { 9, 14, 30.0 };
       increment(currentTime, 60.0);
       printTime (currentTime);
   }

The solution above is correct, but not very efficient. Can you think of a
solution that does not require iteration? Try writing a more efficient version
of ``increment`` in the commented section of the active code below. If you get stuck, 
you can reveal the extra problem at the end for help. 

.. tb-code:: cpp
   :name: modifiers_AC_2
   :caption: Example modifiers_AC_2
   :compileargs: ['-Wall', '-std=c++11']

   #include <iostream>
   using namespace std;

   struct Time {
       int hour, minute;
       double second;
   };

   void printTime (Time& t) {
       cout << t.hour << ":" << t.minute << ":" << t.second << endl;
   }

   void increment (Time& time, double secs) {
       // Write your implementation here.
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

.. tb-reveal:: Reveal Problem
   :name: id_9_6_1

   .. tb-parsons::
      :name: modifiers_1

      Let's write the code for the ``increment`` function. ``increment`` 
      adds a number of seconds to a ``Time`` object and updates the values
      of the object.

      .. code-block:: cpp

         {{group}}
         void increment (Time& time, double secs) {
         {{endgroup}}
         {{distractor}}
         {{group}}
         void increment (const Time& time, double secs) {
         {{endgroup}}
         {{group}}
            int mins = (time.second + secs) / 60;
         {{endgroup}}
         {{distractor}}
         {{group}}
            int mins = (time.second + secs) % 60;
         {{endgroup}}
         {{group}}
            time.second = time.second + secs - 60 * mins;
         {{endgroup}}
         {{distractor}}
         {{group}}
            time.second = time.second + secs;
         {{endgroup}}
         {{group}}
            int hours = (time.minute + mins) / 60;
         {{endgroup}}
         {{distractor}}
         {{group}}
            int hours = (time.second + second) / 60;
         {{endgroup}}
         {{group}}
            time.minute = time.minute + mins - 60 * hours;
         {{endgroup}}
         {{distractor}}
         {{group}}
            time.second = time.minute + mins - 60 * hours;
         {{endgroup}}
         {{group}}
            time.hour += hours;
         }
         {{endgroup}}
