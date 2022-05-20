Pure functions
--------------

.. index::
   single: pure function

A function is considered a pure function if the result depends only on
the arguments, and it has no side effects like modifying an argument or
outputting something. The only result of calling a pure function is the
return value.

.. activecode:: pure_function_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:

   One example is the function ``after``, which compares two ``Time``\ s and
   returns a ``bool`` that indicates whether the first operand comes
   after the second.
   Take a look at the active code below.
   ~~~~
   #include <iostream>

   struct Time {
      int hour, minute;
      double second;
   };

   bool after (Time& time1, Time& time2) {
      if (time1.hour > time2.hour) { return true; }
      if (time1.hour < time2.hour) { return false; }
      if (time1.minute > time2.minute) { return true; }
      if (time1.minute < time2.minute) { return false; }
      if (time1.second > time2.second) { return true; }
      return false;
   }

   int main () {
      Time time = { 11, 59, 3.14159 };
      Time time2 = { 1, 50, 3.14159 };
      std::cout << after(time, time2);
   }

What is the result of this function if the two times are equal? Does
that seem like the appropriate result for this function? If you were
writing the documentation for this function, would you mention that case
specifically?

A second example is ``addTime``, which calculates the sum of two times.
For example, if it is ``9:14:30``, and your bread maker takes 3 hours and
35 minutes, you could use ``addTime`` to figure out when the bread will
be done.

Here is a rough draft of this function that is not quite right:

::

   Time addTime (Time& t1, Time& t2) {
     Time sum;
     sum.hour = t1.hour + t2.hour;
     sum.minute = t1.minute + t2.minute;
     sum.second = t1.second + t2.second;
     return sum;
   }

.. activecode:: pure_function_AC_2
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:

   Take a look at the active code below. If ``currentTime``
   contains the current time and ``breadTime`` contains the amount of time
   it takes for your breadmaker to make bread, then you could use
   ``addTime`` to figure out when the bread will be done.
   ~~~~
   #include <iostream>
 
   struct Time {
       int hour, minute;
       double second;
   };

   void printTime (Time& t) {
       std::cout << t.hour << ':' << t.minute << ':' << t.second << '\n';
   }

   Time addTime (Time& t1, Time& t2) {
       Time sum;
       sum.hour = t1.hour + t2.hour;
       sum.minute = t1.minute + t2.minute;
       sum.second = t1.second + t2.second;
       return sum;
   }

   int main() {
       Time currentTime = { 9, 14, 30.0 };
       Time breadTime = { 3, 35, 0.0 };
       Time doneTime = addTime (currentTime, breadTime);
       printTime (doneTime);
   }

The output of this program is ``12:49:30``, which is correct. On the
other hand, there are cases where the result is not correct. Can you
think of one?

The problem is that this function does not deal with cases where the
number of seconds or minutes adds up to more than 60. When that happens
we have to "carry" the extra seconds into the minutes column, or extra
minutes into the hours column.

Here's a second, corrected version of this function.

.. activecode:: pure_function_AC_3
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:

    The active code below is the corrected version of ``addTime``.
   ~~~~
   #include <iostream>

   struct Time {
       int hour, minute;
       double second;
   };

   void printTime (Time& t) {
       std::cout << t.hour << ':' << t.minute << ':' << t.second << '\n';
   }

   Time addTime (Time& t1, Time& t2) {
       Time sum;
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
       Time currentTime = { 9, 14, 30.0 };
       Time breadTime = { 3, 35, 0.0 };
       Time doneTime = addTime (currentTime, breadTime);
       printTime (doneTime);
   }

Although it's correct, it's starting to get big. Later, I will suggest
an alternate approach to this problem that will be much shorter.

This code demonstrates two operators we have not seen before, ``+=`` and
``-=``. These operators provide a concise way to increment and decrement
variables. For example, the statement ``sum.second -= 60.0;`` is
equivalent to ``sum.second = sum.second - 60;``

.. tabbed:: self_check

   .. tab:: Q1

      .. dragndrop:: pure_functions_1
          :feedback: Try again.
          :match_1: x.dollar += 2;|||x.dollar = x.dollar + 2;
          :match_2: x.dollar -= 2;|||x.dollar = x.dollar - 2;
          :match_3: x.cents -= 2;|||x.cents = x.cents - 2;
          :match_4: x.cents += 2;|||x.cents = x.cents + 2;

          Match the statement to its equivalent.
