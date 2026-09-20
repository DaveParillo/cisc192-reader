Fill-in functions
-----------------

Occasionally you will see functions like ``addTime`` written with a
different interface (different arguments and return values). 
Instead of creating a new object every time ``addTime`` is called,
we could require the caller to provide an "empty" object where 
``addTime`` can store the result.
Compare the following with the previous version:

::

   void addTimeFill (const Time& t1, const Time& t2, Time& sum) {
     sum.hour = t1.hour + t2.hour;
     sum.minute = t1.minute + t2.minute;
     sum.second = t1.second + t2.second;

     if (sum.second >= 60.0) {
       sum.second -= 60.0;
       sum.minute += 1;
     }
     if (sum.minute >= 60) {
       sum.minute -= 60;
       sum.hour += 1;
     }
   }

One advantage of this approach is that the caller has the option of
reusing the same object repeatedly to perform a series of additions.
This can be slightly more efficient, although it can be confusing enough
to cause subtle errors. For the vast majority of programming, it is
worth a spending a little run time to avoid a lot of debugging time.

The active code below uses the fill-in version of the ``addTime`` function.
Feel free to modify the code!

.. tb-code:: cpp
   :name: fillin_functions_AC_1
   :caption: Example fillin_functions_AC_1
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

   void addTimeFill (const Time& t1, const Time& t2, Time& sum) {
       sum.hour = t1.hour + t2.hour;
       sum.minute = t1.minute + t2.minute;
       sum.second = t1.second + t2.second;

       if (sum.second >= 60.0) {
           sum.second -= 60.0;
           sum.minute += 1;
       }
       if (sum.minute >= 60) {
          sum.minute -= 60;
            sum.hour += 1;
      }
   }

   int main() {
      Time currentTime = { 5, 45, 30.0 };
      Time bakingTime = {0, 55, 0.0 };
      Time finishedTime; // We'll store the sum in this variable
      addTimeFill (currentTime, bakingTime, finishedTime);
      cout << "The bread will be ready at ";
      printTime (finishedTime);
   }

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: fillin_functions_1

         ch parameter is not declared as a ``const``?

         code-block:: cpp

         void addTimeFill (const Time& t1, const Time& t2, Time& sum) {
           sum.hour = t1.hour + t2.hour;
           sum.minute = t1.minute + t2.minute;
           sum.second = t1.second + t2.second;

           if (sum.second >= 60.0) {
             sum.second -= 60.0;
             sum.minute += 1;
           }
           if (sum.minute >= 60) {
             sum.minute -= 60;
             sum.hour += 1;
           }
         }

         - [ ] Time& t1

           Try again.
         - [ ] Time& t2

           Try again.
         - [x] Time& sum

           Correct!

