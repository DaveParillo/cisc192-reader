Values
------

.. index::
   single: value

A **value** is one of the fundamental things—like a letter or a number—that
a program manipulates. The only values we have manipulated so far are
the string values we have been outputting, like "Hello, world.". You
(and the compiler) can identify ``string`` values because they are enclosed
in quotation marks.

.. index::
   single: type

.. index::
   single: integer
   single: int

There many different kinds of values, called **types**.  This includes integers and characters. An
**integer** is a whole number like 1 or 17. You can output integer values
the same way you output strings:

::

    cout << 17 << endl;

.. index::
   single: character
   single: char

A **character** value is a letter or digit or punctuation mark enclosed in
single quotes, like ’a’ or ’5’. You can output character values the same
way:

::

    cout << '}' << endl;

This example outputs a single close curly-brace on a line by itself.

It is easy to confuse different types of values, like "5", ’5’ and 5,
but if you pay attention to the punctuation, it should be clear that the
first is a string, the second is a character and the third is an
integer. The reason this distinction is important should become clear
soon.

.. tabbed:: tab_check

   .. tab:: Q1

      .. fillintheblank:: values_1

         A |blank| value is a single letter, number, or punctuation enclosed in single quotes.

         - :([Cc][Hh][Aa][Rr]|[Cc][Hh][Aa][Rr][Aa][Cc][Tt][Ee][Rr]): Correct!
           :.*: Try again!


   .. tab:: Q2

      .. clickablearea:: values2.0
          :question: Click on all integer VALUES.
          :iscode:
          :feedback: Try again!

          :click-incorrect:int main() {:endclick:
              :click-incorrect:int x:endclick: = :click-correct:7:endclick:;
              :click-incorrect:char c:endclick: = :click-incorrect:'8':endclick:;
              while (:click-incorrect:x:endclick: < :click-correct:10:endclick:) {
                  cout << :click-incorrect:c:endclick: << endl;
                  :click-incorrect:x:endclick:++;
              }
              :click-incorrect:c:endclick: = :click-incorrect:'9':endclick:;
              cout << ":click-incorrect:It's the year:endclick: :click-incorrect:3000:endclick:!";
              cout << :click-incorrect:"Just kidding, it's ":endclick: << :click-correct:2020:endclick: << "!";
          }


   .. tab:: Q3

      .. clickablearea:: values2.1
          :question: Click on all string VALUES.
          :iscode:
          :feedback: Try again!

          int main() {
              char :click-incorrect:init1:endclick: = :click-incorrect:'R':endclick:;
              string :click-incorrect:init2:endclick: = :click-correct:"M":endclick:;
              cout << :click-incorrect:init1:endclick: << :click-correct:"+":endclick: << :click-incorrect:init2:endclick: << endl;
              string :click-incorrect:init3:endclick: = :click-correct:"R":endclick:;
              char :click-incorrect:init4:endclick: = :click-incorrect:'P':endclick:;
              cout << :click-incorrect:init3:endclick: << :click-incorrect:'+':endclick: << :click-incorrect:init4:endclick: << endl;
              cout << :click-correct:"Carved their initials in a tree!":endclick:;
          }


   .. tab:: Q4

      .. dragndrop:: values_3
         :feedback: Try again!
         :match_1:  1|||integer
         :match_2: "1"|||string
         :match_3: '1'|||character

         Match the value to its data type.
