Multiple Choice Exercises
-------------------------

.. tb-choice::
   :name: mce_15_1

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
   :name: mce_15_2

   The code below reads data from a file called ``input.txt``. What is wrong with the following code?

   .. code-block:: cpp

       #include <iostream>
       #include <fstream>
       using namespace std;

       int main() {
         string input;
         string filename = "input.txt";
         ifstream infile(filename.c_str());
         getline(filename, input);
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
   :name: mce_15_3

   We want to make sure the file we wanted to open was opened successfully. Which of the
   following checks this and prints the proper output?

   - [ ] ``if (infile.good()) { cout << "File opened unsuccessfully" << '\n'; }``

     - If the ``if`` statement evaluates to true, then the file was opened successfully.

   - [x] ``if (!infile.is_open()) { cout << "File opened unsuccessfully" << '\n'; }``

     + ``is_open()`` is another function that returns ``true`` if a file is opened successfully.

   - [x] ``if (infile.good() == false) { cout << "File opened unsuccessfully" << '\n'; }``

     + If the file isn't opened successfully, an error message is printed.

   - [ ] ``if (!infile.open()) { cout << "File opened unsuccessfully" << '\n'; }``

     - The ``open()`` function is different from ``is_open()`` and does not return a ``bool``.

.. tb-choice::
   :name: mce_15_4

   Which of the following statements are true?

   - [x] The ``ifstream`` constructor expects a C string as an argument.

     + Thus you should convert a filename string to a C string using the c_str() function.

   - [ ] We can assume the program opens all files successfully.

     - There are times when a file can't be properly opened because they may have not been properly closed the last time they were used or the file is currently used by another program. As a result, it is good practice to include a check in your program.

   - [x] A stream is an abstract object that represents the flow of data from a source.

     + We've used two streams before: the standard input stream and standard output stream (``cin`` and ``cout``).

   - [ ] We cannot use the operators ``<<`` and ``>>``, as they are for ``iostream`` objects only.

     - We are also able to use the operators for ``fstream`` objects.

.. tb-choice::
   :name: mce_15_5

   What are the contents of the output file ``output.txt`` after running the code below?

   .. code-block:: cpp

       #include <iostream>
       #include <fstream>
       using namespace std;

       int main() {
         ofstream outfile("output.txt");

         if (!outfile.good()) {
           cout << "Unable to open file" << '\n';
         }

         cout << "Powers of 2: ";
         outfile << "2 4 8 16 32 64" << '\n';  
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
   :name: mce_15_6

   The file ``scores.txt`` contains data about the roster number and test scores of students in a class.
   The output file ``averages.txt`` should store each student's roster number and average test score.
   What should replace the question marks?

   .. code-block:: cpp

       #include <iostream>
       #include <fstream>
       using namespace std;

       int main() {
         string junk;
         int student_num;
         double mid1, mid2, final;
         ifstream infile("scores.txt");
         ofstream outfile("averages.txt");

         if (!infile.good() || !outfile.good()) {
           cout << "Unable to open a file" << '\n';
         }

         getline(infile, junk);
         outfile << "student#\t_average" << '\n';

         while (infile >> student_num >> mid1 >> mid2 >> final) {
           double avg = (mid1 + mid2 + final) / 3;
           ???  
         }  
       }

   - [ ] ``cout << avg << '\n'``

     - This will output the average to standard output.

   - [ ] ``outfile << avg << '\n'``

     - Take another look at the code. Is there a clue as to what data should be in the output file?

   - [ ] ``infile << student_num << '\t' << avg << '\n'``

     - The data should be written to the output file.

   - [x] ``outfile << student_num << '\t' << avg << '\n'``

     + This properly outputs the student number and the student's average to the output file.

.. tb-choice::
   :name: mce_15_7

   What does the following code do?

   .. code-block:: cpp

       #include <iostream>
       #include <string>
       using namespace std;

       int main() {
         string original = "430-0444";
         string digit_string = "";

         for (size_t i = 0; i < original.length(); i++) {
           if (isdigit(original[original.length() - 1 - i])) {
             digit_string += original[original.length() - 1 - i];
           }
         }
         cout << atoi(digit_string.c_str()) << '\n';
       }

   - [ ] The code converts the original string to an integer and outputs the integer.

     - Take a closer look at the contents of the ``for`` loop.

   - [ ] The code converts an integer to a string and outputs the string.

     - What does the ``atoi`` function do?

   - [ ] The code outputs the sum of all the original string's digits.

     - The ``digit_string`` variable is a ``string``, not an ``int``.

   - [x] The code converts the original string to an integer in reverse and outputs the integer in reverse.

     + The code in the ``for`` loop parses the string in reverse.

.. tb-choice::
   :name: mce_15_8

   Which of the following statements are false about the ``Set`` data structure?

   - [x] A set can contain multiple elements with the same value.

     + All elements in a set are unique.

   - [ ] We can identify elements of a set by each element's index.

     - Each element has an index associated with it.

   - [x] The elements of a ``Set`` are always sorted.

     + Although a set is ordered, it is not necessarily sorted.

   - [x] The size of a ``Set`` object is fixed.

     + The ``Set`` data structure can expand to make room for new elements.

.. tb-choice::
   :name: mce_15_9

   There are many ways to construct a ``matrix``. Which of the following are valid constructors of a ``matrix``?

   - [ ] ``matrix<string> m1(2);``

     - A ``matrix`` has two dimensions and this constructor only has one dimension.

   - [x] ``matrix<int> m2(2, 6, 0);``

     + This creates a ``matrix`` with 2 rows and 6 columns with all of its elements equal to 0.

   - [x] ``matrix<char> m3(m2);``

     + This creates ``m3`` to be a copy of ``m2``.

   - [ ] ``matrix<int> m2(2.4, 2);``

     - There must be a whole number of rows and columns.

.. tb-choice::
   :name: mce_15_10

   What is the output of the following code?

   .. code-block:: cpp

       #include <iostream>
       #include <vector>
       using namespace std;

       bool secret_function(int num) {
         if (num % 2 == 0) {
           return true;
         }
         return false;
       }

       int main() {
         matrix<int> mat(4, 2);
         for (size_t i = 0 i < mat.size(); ++i) {
           for (size_t j = 0; j < mat[i].size(); ++j) {
             if (!secret_function(i + j) {
               mat[i][j] = 0;
             }
             else {
               mat[i][j] = i + j;
             }
           }
         }
         int n;
         for (size_t i = 0 i < mat.size(); ++i) {
           for (size_t j = 0; j < mat[i].size(); ++j) {
             n += mat[i][j];
           }
         }
         cout << n << '\n';
       }

   - [ ] 8

     - The matrix only contains even sums of the row and column indices and 0 otherwise. Thus, the sum of all elements is 8.

   - [ ] 16

     - What does the secret function do?

   - [ ] 0

     - What are the contents of the matrix?

   - [x] 9

     + What are the contents of the matrix?

