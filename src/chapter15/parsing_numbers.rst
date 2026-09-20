Parsing numbers with error reporting
====================================

Converting a string to an integer should distinguish valid input from invalid
input and detect values that cannot fit in the result type. ``std::stoi``
from ``<string>`` returns an ``int`` and throws ``std::invalid_argument`` or
``std::out_of_range`` when it cannot produce one. It also reports how many
characters it consumed, so we can reject a partially parsed value.

Unlike ``atoi``, this interface does not silently make a failed conversion
look like a valid zero. Do not strip every nondigit from a string: that would
turn ``-12`` into ``12`` or ``12x3`` into ``123`` instead of detecting a problem.

For a format that permits comma-separated thousands, first validate the groups,
then remove the commas. Phone numbers and identifiers should remain strings;
arithmetic conversion loses leading zeros and other meaningful formatting.

.. tb-code:: cpp
   :name: c192_15_6
   :caption: Example c192_15_6
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <cstddef>
   #include <iostream>
   #include <stdexcept>
   #include <string>

   int parse_distance(const std::string& text) {
       std::string digits;
       std::size_t group_size = 0;
       bool has_comma = false;
       for (char ch : text) {
           if (ch >= '0' && ch <= '9') {
               digits += ch;
               ++group_size;
           } else if (ch == ',') {
               if (group_size == 0 || (!has_comma && group_size > 3) ||
                   (has_comma && group_size != 3)) {
                   throw std::invalid_argument("invalid digit grouping");
               }
               has_comma = true;
               group_size = 0;
           } else {
               throw std::invalid_argument("expected a nonnegative integer");
           }
       }
       if (digits.empty() || (has_comma && group_size != 3)) {
           throw std::invalid_argument("incomplete distance");
       }
       std::size_t used = 0;
       int value = std::stoi(digits, &used);
       if (used != digits.size()) {
           throw std::invalid_argument("trailing characters");
       }
       return value;
   }

   int main() {
       try {
           std::cout << parse_distance("1,750") << '\n';
       } catch (const std::exception& error) {
           std::cerr << error.what() << '\n';
           return 1;
       }
   }

The examples ``1750`` and ``1,750`` produce the same value. Inputs such as
``1,,750``, ``17,50``, ``-12``, an empty string, or letters are rejected.
An integer larger than ``int`` can represent is also rejected. The accumulated
``digits`` string is an example of building a result one character at a time.

.. tb-choice::
   :name: question15_6_1

   What does the ``atoi()`` function do?

   - [ ] takes the absolute value of a number

     Incorrect! Go back and read for the answer.
   - [ ] converts a double to an int

     Incorrect! Go back and read for the answer.
   - [x] converts a string to an int

     Correct! This is very helpful when we read numbers from a file (where they are strings).
   - [ ] converts an int to a string

     Incorrect! Go back and read for the answer.

.. tb-choice::
   :name: question15_6_2

   Which of the following strings will return "2020" when passed into ``convertToInt()``?

   - [x] 2020

     Correct! This one is quite simple.
   - [x] ab,jkl2!!moo0?huh2mth0haha.

     Correct! This long, confusing string will clean up nicely!
   - [ ] 2,00!!!!!!!!2

     Incorrect!
   - [x] 2OOO020OOOOO

     Correct! You have to look closely to see that some of these are 0's!
   - [ ] we2love0parsing2numbersO!

     Incorrect! Although we do love parsing numbers, this is incorrect.

.. tb-parsons::
   :name: c192_question15_6_3

   Return a copy of ``text`` with every ``old_char`` replaced by ``new_char``.

   .. code-block:: c++

      {{group}}
      std::string replace_with(std::string text, char old_char, char new_char) {
      {{endgroup}}
      {{group}}
          for (char& ch : text) {
      {{endgroup}}
      {{group}}
              if (ch == old_char) {
      {{endgroup}}
      {{group}}
                  ch = new_char;
              }
          }
      {{endgroup}}
      {{group}}
          return text;
      }
      {{endgroup}}

