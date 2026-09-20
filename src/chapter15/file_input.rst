File input
==========

.. _c192_finput:

``std::ifstream``, declared in ``<fstream>``, reads from a file. Construct the
stream with a string containing the file name. Modern C++ accepts a
``std::string`` directly; no conversion to a C string is required.

.. code-block:: cpp

   std::string file_name = "readings.txt";
   std::ifstream input(file_name);

Check that the file opened, then check each read. A stream converts to a
Boolean value that is false after a failed operation. Reading in a loop's
condition avoids processing a value that was never successfully read.

.. tb-file::
   :name: c192_readings-txt
   :filename: c192_readings.txt

   12
   7
   19

.. tb-code:: cpp
   :name: c192_file_input_readings
   :caption: Example c192_file_input_readings
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']
   :files: c192_readings.txt

   #include <fstream>
   #include <iostream>

   int main() {
       std::ifstream input("c192_readings.txt");
       if (!input) {
           std::cerr << "Unable to open readings\n";
           return 1;
       }
       int reading = 0;
       while (input >> reading) {
           std::cout << reading << '\n';
       }
       if (input.bad() || !input.eof()) {
           std::cerr << "Unable to read an integer\n";
           return 1;
       }
   }

For whole lines, use ``while (std::getline(input, line))``. A final line
without a newline is still a valid line and must be processed. Testing
``eof()`` immediately after a successful ``getline`` can incorrectly discard
that line. Testing ``!eof()`` before reading can process stale data after a
failed read. Check the read itself instead.

.. code-block:: cpp

   std::string line;
   while (std::getline(input, line)) {
       std::cout << line << '\n';
   }

Formatted extraction (``>>``) usually skips leading whitespace. ``getline``
reads up to the next newline. If you mix them, remember that ``>>`` can leave
the newline in the stream, so the next ``getline`` may read an empty line.
One option is to read whole lines and parse each line with a separate string
stream, as we will do for the city records.

A file stream closes its file when it goes out of scope. This is an example
of resource ownership: the object's lifetime controls the resource's lifetime.

.. tb-choice::
   :name: question15_3_3

   We need to use the function ``c_str()`` to convert a string to a native C string because...


   - [x] the ifstream constructor expects a C string as an argument.

     Correct!
   - [ ] you need to make sure you have permission to read to/from the file.

     Incorrect! Try reading again!
   - [ ] it will check whether you have an infinite loop or not.

     Incorrect! Try reading again!
   - [ ] strings are not supported by C++.

     Incorrect! strings are allowed in C++.

.. tb-blank::
   :name: c192_question15_3_2

   The standard-library type used to read from a file is {{{{blank}}}}.

   .. tb-answer::
      :match: (std
      :feedback: :)?ifstream: Correct!
      :incorrect: Look for the input file stream type.

