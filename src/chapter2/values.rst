.. _variables-types-values:

Values
------

.. index::
   single: value

A **value** is one of the fundamental things—like a letter or a number—that
a program manipulates. The only values we have manipulated so far are
the string values we have been outputting, like "Hello, world.". You
(and the compiler) can identify ``string`` values because they are enclosed
in double-quotation marks.

.. index::
   single: type

.. index::
   single: integer
   single: int

There many different kinds of values, called :lang:`types <type>`.
This includes integers and characters.
An **integer** is a whole number like 1 or 17.
You can output integer values the same way you output strings:

::

    cout << 17 << '\n';

.. index::
   single: character
   single: char

A **character** value is a letter or digit or punctuation mark enclosed in
single quotes, like ’a’ or ’5’. You can output character values the same
way:

::

    cout << '}' << '\n';

This example outputs a single close curly-brace on a line by itself.

It is easy to confuse different types of values, like "5", ’5’ and 5,
but if you pay attention to the punctuation, it should be clear that the
first is a string, the second is a character and the third is an
integer. The reason this distinction is important should become clear
soon.

.. tb-group::
   :name: tab_check

   .. tb-tab:: Q1

      .. tb-blank::
         :name: values_1

         A {{blank}} value is a single letter, number, or punctuation enclosed in single quotes.

         .. tb-answer::
            :regex:
            :match: char|character
            :feedback: Correct!
            :incorrect: Try again!

   .. tb-tab:: Q2

      .. tb-click::
         :name: values2_0

         Click on all integer VALUES.

         .. code-block:: cpp

            int main() {
                int x = 7;
                char c = '8';
                while (x < 10) {
                    cout << c << '\n';
                    x++;
                }
                c = '9';
                cout << "It's the year 3000!";
                cout << "Just kidding, it's " << 2020 << '!';
            }



         .. tb-miss:: text:int main() {

            Try again!

         .. tb-miss:: text:int x

            Try again!

         .. tb-hit:: text:7

            Correct.

         .. tb-miss:: text:char c

            Try again!

         .. tb-miss:: text:8

            Try again!

         .. tb-hit:: text:10

            Correct.

         .. tb-miss:: text:x#2

            Try again!

         .. tb-miss:: text:9

            Try again!

         .. tb-miss:: text:It's the year

            Try again!

         .. tb-miss:: text:3000

            Try again!

         .. tb-miss:: text:"Just kidding, it's "

            Try again!

         .. tb-hit:: text:2020

            Correct.

   .. tb-tab:: Q3

      .. tb-click::
         :name: values2_1

         Click on all string VALUES.

         .. code-block:: cpp

            int main() {
                char init1 = 'R';
                string init2 = "M";
                cout << init1 << '+' << init2 << '\n';
                string init3 = "R";
                char init4 = 'P';
                cout << init3 << '+' << init4 << '\n';
                cout << "Carved their initials in a tree!";
            }



         .. tb-miss:: text:init1

            Try again!

         .. tb-miss:: text:R

            Try again!

         .. tb-miss:: text:init2

            Try again!

         .. tb-hit:: text:"M"

            Correct.

         .. tb-miss:: text:init1#2

            Try again!

         .. tb-hit:: text:+

            Correct.

         .. tb-miss:: text:init2#2

            Try again!

         .. tb-miss:: text:init3

            Try again!

         .. tb-hit:: text:R#2

            Correct.

         .. tb-miss:: text:init4

            Try again!

         .. tb-miss:: text:P

            Try again!

         .. tb-miss:: text:init3#2

            Try again!

         .. tb-miss:: text:+#2

            Try again!

         .. tb-miss:: text:init4#2

            Try again!

         .. tb-hit:: text:"Carved their initials in a tree!"

            Correct.

   .. tb-tab:: Q4

      .. tb-match::
         :name: values_3

         Match the value to its data type.

         1
            integer
         "1"
            string
         '1'
            character

-----

.. admonition:: More to Explore

   - From cppreference.com

     - The :lang:`type` property
     - :c:`Complete list of all punctuation <language/punctuators>`
