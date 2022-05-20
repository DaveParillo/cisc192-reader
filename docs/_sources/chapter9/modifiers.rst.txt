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


.. activecode:: modifiers_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:

   The active code below uses the ``increment`` function.
   Run the active code to see what the output is!
   ~~~~
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
 
.. activecode:: modifiers_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:

   The solution above is correct, but not very efficient. Can you think of a
   solution that does not require iteration? Try writing a more efficient version
   of ``increment`` in the commented section of the active code below. If you get stuck, 
   you can reveal the extra problem at the end for help. 
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
 
.. reveal:: 9_6_1
   :showtitle: Reveal Problem
   :hidetitle: Hide Problem

   .. parsonsprob:: modifiers_1
      :numbered: left
      :adaptive:
   
      Let's write the code for the ``increment`` function. ``increment`` 
      adds a number of seconds to a ``Time`` object and updates the values
      of the object.
      -----
      void increment (Time& time, double secs) {
      =====
      void increment (const Time& time, double secs) {                         #paired
      =====
         int mins = (time.second + secs) / 60;
      =====
         int mins = (time.second + secs) % 60;                        #paired 
      =====
         time.second = time.second + secs - 60 * mins;
      =====
         time.second = time.second + secs;                        #paired 
      =====
         int hours = (time.minute + mins) / 60;
      =====
         int hours = (time.second + second) / 60;                        #paired 
      =====
         time.minute = time.minute + mins - 60 * hours;
      =====
         time.second = time.minute + mins - 60 * hours;                        #paired 
      =====
         time.hour += hours;
      }
