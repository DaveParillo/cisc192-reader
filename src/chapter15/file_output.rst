File output
===========

``std::ofstream`` writes to a file. Opening an output file normally truncates
its old contents; use a different output name when copying a file. If you
intend to append instead, open it with ``std::ios::app``. Both file stream
types are declared in ``<fstream>``.

The following program copies whole lines. It checks input and output opening
separately so its error messages identify the failed operation. It also
checks writes and the explicit close: an output failure may be reported only
when buffered output is flushed.

.. tb-code:: cpp
   :name: c192_copy_file
   :caption: Example c192_copy_file
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']
   :files: c192_readings.txt

   #include <fstream>
   #include <iostream>
   #include <string>

   int main() {
       std::ifstream input("c192_readings.txt");
       if (!input) {
           std::cerr << "Unable to open input\n";
           return 1;
       }
       std::ofstream output("readings_copy.txt");
       if (!output) {
           std::cerr << "Unable to open output\n";
           return 1;
       }
       std::string line;
       while (std::getline(input, line)) {
           output << line << '\n';
           if (!output) {
               std::cerr << "Write failed\n";
               return 1;
           }
       }
       if (input.bad() || !input.eof()) {
           std::cerr << "Read failed\n";
           return 1;
       }
       output.close();
       if (!output) {
           std::cerr << "Unable to finish output\n";
           return 1;
       }
       std::cout << "Copy complete\n";
   }

This copies text lines, adding a newline after each one. It is not a
byte-for-byte copy when the original file has no final newline. If exact bytes
matter, that is a different requirement.

.. tb-parsons::
   :name: c192_question15_4_1

   Write the values in ``readings`` to ``readings.txt``, one per line.
   Return a nonzero status from main if opening or writing fails.
   Assume the headers and ``readings`` are supplied.

   .. code-block:: c++

      {{group}}
      std::ofstream output("readings.txt");
      {{endgroup}}
      {{group}}
      if (!output) { return 1; }
      {{endgroup}}
      {{group}}
      for (int reading : readings) {
      {{endgroup}}
      {{group}}
          output << reading << '\n';
      }
      {{endgroup}}
      {{group}}
      output.close();
      {{endgroup}}
      {{group}}
      if (!output) { return 1; }
      {{endgroup}}

.. tb-choice::
   :name: question15_4_2

   The code from the previous problem checks whether the files open or not. It doesn't specify which one, if any, doesn't open. How could you specify which file does not open?

   - [ ] Create two "for" loops instead of an if-statement so that the statement loops through both conditions once.

     Try again!
   - [ ] Create a "while" loop instead of an if-statement so that the statement loops through both conditions separately until the body of the loop is reached.

     Try again!
   - [x] Create two "if" statements, one that check whether in_file.good() is false, and another that checks whether out_file.good() is false, instead of putting them together in one "if" statement.

     Correct!

.. tb-blank::
   :name: c192_question15_4_3

   Complete the type: {{{{blank}}}} ``output("results.txt");``.

   .. tb-answer::
      :match: (std
      :feedback: :)?ofstream: Correct!
      :incorrect: Use an output file stream.

