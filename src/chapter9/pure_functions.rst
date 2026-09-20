.. _more-structures-pure-functions:

Pure functions
--------------

.. index::
   single: pure function

A function is considered a pure function if the result depends only on
the arguments, and it has no side effects like modifying an argument or
outputting something. The only result of calling a pure function is the
return value.

One example is the function ``after``, which compares two ``time``\ s and
returns a ``bool`` that indicates whether the first operand comes
after the second.
Take a look at the active code below.

.. tb-code:: cpp
   :name: pure_function_AC_1
   :caption: Example pure_function_AC_1

   #include <iostream>

   struct time {
      int hour, minute;
      double second;
   };

   bool after (time& time1, time& time2) {
      if (time1.hour > time2.hour) { return true; }
      if (time1.hour < time2.hour) { return false; }
      if (time1.minute > time2.minute) { return true; }
      if (time1.minute < time2.minute) { return false; }
      if (time1.second > time2.second) { return true; }
      return false;
   }

   int main () {
      time time = { 11, 59, 3.14159 };
      time time2 = { 1, 50, 3.14159 };
      std::cout << after(time, time2);
   }

What is the result of this function if the two times are equal? Does
that seem like the appropriate result for this function? If you were
writing the documentation for this function, would you mention that case
specifically?

A second example is ``add_time``, which calculates the sum of two times.
For example, if it is ``9:14:30``, and your bread maker takes 3 hours and
35 minutes, you could use ``add_time`` to figure out when the bread will
be done.

Here is a rough draft of this function that is not quite right:

::

   time add_time (time& t1, time& t2) {
     time sum;
     sum.hour = t1.hour + t2.hour;
     sum.minute = t1.minute + t2.minute;
     sum.second = t1.second + t2.second;
     return sum;
   }

Take a look at the active code below. If ``current_time``
contains the current time and ``bread_time`` contains the amount of time
it takes for your breadmaker to make bread, then you could use
``add_time`` to figure out when the bread will be done.

.. tb-code:: cpp
   :name: pure_function_AC_2
   :caption: Example pure_function_AC_2

   #include <iostream>

   struct time {
       int hour, minute;
       double second;
   };

   void print_time (time& t) {
       std::cout << t.hour << ':' << t.minute << ':' << t.second << '\n';
   }

   time add_time (time& t1, time& t2) {
       time sum;
       sum.hour = t1.hour + t2.hour;
       sum.minute = t1.minute + t2.minute;
       sum.second = t1.second + t2.second;
       return sum;
   }

   int main() {
       time current_time = { 9, 14, 30.0 };
       time bread_time = { 3, 35, 0.0 };
       time done_time = add_time (current_time, bread_time);
       print_time (done_time);
   }

The output of this program is ``12:49:30``, which is correct. On the
other hand, there are cases where the result is not correct. Can you
think of one?

The problem is that this function does not deal with cases where the
number of seconds or minutes adds up to more than 60. When that happens
we have to "carry" the extra seconds into the minutes column, or extra
minutes into the hours column.

Here's a second, corrected version of this function.

 The active code below is the corrected version of ``add_time``.

.. tb-code:: cpp
   :name: pure_function_AC_3
   :caption: Example pure_function_AC_3

   #include <iostream>

   struct time {
       int hour, minute;
       double second;
   };

   void print_time (time& t) {
       std::cout << t.hour << ':' << t.minute << ':' << t.second << '\n';
   }

   time add_time (time& t1, time& t2) {
       time sum;
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
       return sum;
   }

   int main() {
       time current_time = { 9, 14, 30.0 };
       time bread_time = { 3, 35, 0.0 };
       time done_time = add_time (current_time, bread_time);
       print_time (done_time);
   }

Although it's correct, it's starting to get big. Later, I will suggest
an alternate approach to this problem that will be much shorter.

This code demonstrates two operators we have not seen before, ``+=`` and
``-=``. These operators provide a concise way to increment and decrement
variables. For example, the statement ``sum.second -= 60.0;`` is
equivalent to ``sum.second = sum.second - 60;``

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-match::
         :name: pure_functions_1

         Match the statement to its equivalent.

         x.dollar += 2;
            x.dollar = x.dollar + 2;
         x.dollar -= 2;
            x.dollar = x.dollar - 2;
         x.cents -= 2;
            x.cents = x.cents - 2;
         x.cents += 2;
            x.cents = x.cents + 2;

