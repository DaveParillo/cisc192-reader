Fill-in functions
-----------------

Occasionally you will see functions like ``add_time`` written with a
different interface (different arguments and return values). 
Instead of creating a new object every time ``add_time`` is called,
we could require the caller to provide an "empty" object where 
``add_time`` can store the result.
compare the following with the previous version:

::

   void add_time_fill (const time& t1, const time& t2, time& sum) {
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

The active code below uses the fill-in version of the ``add_time`` function.
Feel free to modify the code!

.. tb-code:: cpp
   :name: fillin_functions_AC_1
   :caption: Example fillin_functions_AC_1
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

   void add_time_fill (const time& t1, const time& t2, time& sum) {
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
      time current_time = { 5, 45, 30.0 };
      time baking_time = {0, 55, 0.0 };
      time finished_time; // We'll store the sum in this variable
      add_time_fill (current_time, baking_time, finished_time);
      cout << "The bread will be ready at ";
      print_time (finished_time);
   }

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: fillin_functions_1

         Which parameter is not declared as a ``const``?

         .. code-block:: cpp

            void add_time_fill (const time& t1, const time& t2, time& sum) {
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

         - [ ] time& t1

           Try again.
         - [ ] time& t2

           Try again.
         - [x] time& sum

           Correct!

