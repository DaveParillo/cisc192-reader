Parsing quoted records
======================

.. _c192_parsing:

Parsing interprets characters according to a format. Our format is two
quoted, nonempty city names followed by a nonnegative integer distance.
Reading each record with ``getline`` lets us report malformed records one
line at a time.

``std::istringstream`` from ``<sstream>`` reads from a string using the same
extraction interface as a file stream. ``std::quoted`` from ``<iomanip>``
handles quoted names, including escaped quotes. Check the opening quote
explicitly when the file format requires it: ``std::quoted`` also accepts an
unquoted word if there is no opening quote.

.. tb-code:: cpp
   :name: c192_parse_record
   :caption: Example c192_parse_record
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <iomanip>
   #include <iostream>
   #include <sstream>
   #include <string>

   struct route_record {
       std::string origin;
       std::string destination;
       int distance = 0;
   };

   bool parse_record(const std::string& line, route_record& record) {
       std::istringstream input(line);
       route_record parsed;
       input >> std::ws;
       if (input.peek() != '"' || !(input >> std::quoted(parsed.origin))) {
           return false;
       }
       input >> std::ws;
       if (input.peek() != '"' || !(input >> std::quoted(parsed.destination))) {
           return false;
       }
       if (!(input >> parsed.distance) || parsed.distance < 0 ||
           parsed.origin.empty() || parsed.destination.empty()) {
           return false;
       }
       input >> std::ws;
       if (!input.eof()) {
           return false;
       }
       record = parsed;
       return true;
   }

   int main() {
       route_record record;
       if (parse_record(R"("San Diego" "Los Angeles" 120)", record)) {
           std::cout << record.origin << " -> " << record.destination
                     << ": " << record.distance << '\n';
       }
   }

A temporary ``parsed`` record prevents partially updating the caller's record
on failure. The final whitespace check rejects trailing junk such as ``120km``.
The raw string literal in ``main`` lets the example contain double quotes
without backslash escapes. An ordinary string literal with ``\"`` escapes
would work too.

This format deliberately uses plain digits for distances. The next section
shows how to handle a separate format that permits commas.

.. tb-choice::
   :name: c192_question15_5_1



   - [x] Interpreting input according to a specified structure.

     Parsing extracts and validates meaningful values.
   - [ ] Printing every character unchanged.

     Copying text does not interpret its structure.

.. tb-blank::
   :name: c192_question15_5_2

   The character used to escape a quote in an ordinary string literal is a {{{{blank}}}}.

   .. tb-answer::
      :match: backslash
      :feedback: Correct!
      :incorrect: It is the character before the quote in the escape sequence.

.. tb-blank::
   :name: c192_question15_5_3

   ``std::string::substr`` takes a starting {{blank:blank1}} and an optional {{blank:blank2}}.

   .. tb-answer:: blank1
      :match: index|position
      :feedback: Correct!
      :incorrect: Where should the substring begin?

   .. tb-answer:: blank2
      :match: count|length
      :incorrect: How many characters should it contain?

