Multiple Choice Exercises
-------------------------

.. tb-choice::
   :name: c192_mce_15_1

   We want to open a file and parse its data into our program. What library
   do we need to include?

   - [ ] ``iostream``

     - This library deals with communication through the standard input and output.

   - [ ] ``sstream``

     -  This library is used to manipulate string objects as if they were streams.

   - [x] ``fstream``

     + This library is used to manipulate files using streams.

   - [ ] ``iomanip``

     - This library is used to modify internal flags and formatting options.

.. tb-choice::
   :name: c192_mce_15_2

   The code below reads data from a file called ``input.txt``. What is wrong with the following code?

   .. code-block:: cpp

       #include <iostream>
       #include <fstream>

       int main() {
         std::string input;
         std::string filename = "input.txt";
         std::ifstream infile(filename);
         std::getline(filename, input);
       }

   - [ ] We should use ``ofstream`` instead of ``ifstream``.

     - Since we are dealing with an input file, we should use ``ifstream``.

   - [x] The arguments in ``getline`` are incorrect.

     + We are supposed to read input through the ``ifstream`` object. This line should be ``getline(infile, input)``.

   - [ ] We cannot use a variable to store the filename.

     - Since the name of the file is just a string, we can store it in a variable.

   - [ ] There are no errors with this code.

     - Take another look at the code. Are we reading the input correctly into ``input``?

.. tb-choice::
   :name: c192_mce_15_3

   We want to make sure the file we wanted to open was opened successfully. Which of the
   following checks this and prints the proper output?

   - [ ] ``if (infile.good()) { cout << "File opened unsuccessfully" << endl; }``

     - If the ``if`` statement evaluates to true, then the file was opened successfully.

   - [x] ``if (!infile.is_open()) { cout << "File opened unsuccessfully" << endl; }``

     + ``is_open()`` is another function that returns ``true`` if a file is opened successfully.

   - [x] ``if (infile.good() == false) { cout << "File opened unsuccessfully" << endl; }``

     + If the file isn't opened successfully, an error message is printed.

   - [ ] ``if (!infile.open()) { cout << "File opened unsuccessfully" << endl; }``

     - The ``open()`` function is different from ``is_open()`` and does not return a ``bool``.

.. tb-choice::
   :name: c192_mce_15_4

   Which of the following statements are true?

   - [x] The ``std::ifstream`` constructor can accept a ``std::string`` filename.

     + C++20 accepts the string directly; a ``c_str()`` conversion is unnecessary.

   - [ ] We can assume the program opens all files successfully.

     - There are times when a file can't be properly opened because they may have not been properly closed the last time they were used or the file is currently used by another program. As a result, it is good practice to include a check in your program.

   - [x] A stream is an abstract object that represents the flow of data from a source.

     + We've used two streams before: the standard input stream and standard output stream (``cin`` and ``cout``).

   - [ ] We cannot use the operators ``<<`` and ``>>``, as they are for ``iostream`` objects only.

     - We are also able to use the operators for ``fstream`` objects.

.. tb-choice::
   :name: c192_mce_15_5

   What are the contents of the output file ``output.txt`` after running the code below?

   .. code-block:: cpp

       #include <iostream>
       #include <fstream>

       int main() {
         std::ofstream outfile("output.txt");

         if (!outfile.good()) {
           std::cout << "Unable to open file" << std::endl;
         }

         std::cout << "Powers of 2: ";
         outfile << "2 4 8 16 32 64" << std::endl;
       }

   - [x] 2 4 8 16 32 64

     + This is the only thing we write to the output file.

   - [ ] Powers of 2: 2 4 8 16 31 64

     - Take another look at the stream objects used in the code.

   - [ ] Powers of 2:

     - This is printed to standard output, not the output file.

   - [ ] Unable to open file

     - Although this may be printed, this is not the contents of the output file.

.. tb-choice::
   :name: c192_mce_15_6

   The file ``scores.txt`` contains data about the roster number and test scores of students in a class.
   The output file ``averages.txt`` should store each student's roster number and average test score.
   What should replace the question marks?

   .. code-block:: cpp

       #include <iostream>
       #include <fstream>

       int main() {
         std::string junk;
         int student_num;
         double mid1, mid2, final;
         std::ifstream infile("scores.txt");
         std::ofstream outfile("averages.txt");

         if (!infile.good() || !outfile.good()) {
           std::cout << "Unable to open a file" << std::endl;
         }

         std::getline(infile, junk);
         outfile << "student#\t_average" << std::endl;

         while (infile >> student_num >> mid1 >> mid2 >> final) {
           double avg = (mid1 + mid2 + final) / 3;
           ???
         }
       }

   - [ ] ``cout << avg << endl``

     - This will output the average to standard output.

   - [ ] ``outfile << avg << endl``

     - Take another look at the code. Is there a clue as to what data should be in the output file?

   - [ ] ``infile << student_num << "\t" << avg << endl``

     - The data should be written to the output file.

   - [x] ``outfile << student_num << "\t" << avg << endl``

     + This properly outputs the student number and the student's average to the output file.

.. tb-choice::
   :name: c192_mce_15_7

   What does the following code do?

   .. code-block:: cpp

       #include <iostream>
       #include <string>

       int main() {
         std::string original = "430-0444";
         std::string digit_string = "";

         for (std::size_t i = 0; i < original.length(); i++) {
           if (std::isdigit(static_cast<unsigned char>(original[original.length() - 1 - i]))) {
             digit_string += original[original.length() - 1 - i];
           }
         }
         std::cout << std::stoi(digit_string) << std::endl;
       }

   - [ ] The code converts the original string to an integer and outputs the integer.

     - Take a closer look at the contents of the ``for`` loop.

   - [ ] The code converts an integer to a string and outputs the string.

     - What does the ``std::stoi`` function do?

   - [ ] The code outputs the sum of all the original string's digits.

     - The ``digit_string`` variable is a ``string``, not an ``int``.

   - [x] The code converts the original string to an integer in reverse and outputs the integer in reverse.

     + The code in the ``for`` loop parses the string in reverse.

.. tb-choice::
   :name: c192_mce_15_8



   - [x] A std::set can store the same key multiple times.

     A set stores each distinct key once.
   - [x] A std::set provides numeric indexing with operator[].

     Use membership tests or iterators, not numeric indexing.
   - [ ] A std::set keeps keys sorted by its comparison function.

     This is true, so do not select it as false.
   - [ ] A std::set can grow as keys are inserted.

     This is true; a set is not fixed-size.

.. tb-choice::
   :name: c192_mce_15_9



   - [x] std::array<std::array<int, 6>, 2> table{};

     Two rows of six integers are value-initialized to zero.
   - [x] std::vector<std::vector<int>> table(2, std::vector<int>(6, 0));

     Two vectors of six zero-initialized integers form the table.
   - [ ] std::vector<int> table(2, 6);

     This creates a one-dimensional vector of two integers equal to 6.

.. tb-choice::
   :name: c192_mce_15_10

   t does this C++20 program print?

   code-block:: cpp

   #include <array>
   #include <cstddef>
   #include <iostream>

   int main() {
       std::array<std::array<int, 2>, 4> table{};
       for (std::size_t row = 0; row < table.size(); ++row) {
           for (std::size_t col = 0; col < table[row].size(); ++col) {
               if ((row + col) % 2 == 0) {
                   table[row][col] = static_cast<int>(row + col);
               }
           }
       }
       int total = 0;
       for (const auto& row : table) {
           for (int value : row) {
               total += value;
           }
       }
       std::cout << total << '\n';
   }

   - [x] 8

     The nonzero entries are 2, 2, and 4, whose sum is 8.
   - [ ] 16

     Only even row-plus-column sums are stored.
   - [ ] 0

     Several positions receive nonzero values.

