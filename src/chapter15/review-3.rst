.. _files-containers-coding-practice:

Coding Practice
---------------

.. tb-group::
   :name: c192_cp_15_3

   .. tb-tab:: Question

      Write a program that takes in an input file called ``heights.txt,``
      finds the median of the data, and prints
      "The median height is: ``height`` inches" to the terminal.
      Include proper file error checking.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_3q
         :caption: Example c192_cp_15_ac_3q
         :files: heights.txt

         #include <iostream>
         #include <fstream>
         #include <vector>
         #include <algorithm>

         // Write your code here.


   .. tb-tab:: Answer

      Below is one way to implement this program. We create an ``ifstream`` object
      to open our file. We check to make sure the file is opened correctly before
      we read the data values into a vector. After sorting the vector, we find
      the median depending on whether the number of data values was even or odd.
      Finally, we output our result to the terminal.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_3a
         :caption: Example c192_cp_15_ac_3a
         :files: heights.txt

         #include <cstdlib>
         #include <iostream>
         #include <fstream>
         #include <vector>
         #include <algorithm>

         int main() {
             std::ifstream infile("heights.txt");
             std::vector<int> data;
             double median;
             int height;
             if (!infile.good()) {
                 std::cout << "Error. Unable to open file." << '\n';
                 std::exit(1);
             }
             while (infile >> height) {
                 data.push_back(height);
             }
             sort(data.begin(), data.end());
             if (data.size() % 2 == 0) {
                 median = (data[data.size() / 2 - 1] + data[data.size() / 2]) / 2.0;
             }
             else {
                 median = data[data.size() / 2];
             }
             std::cout << "The median height is: " << median << " inches" << '\n';
         }


.. tb-group::
   :name: c192_cp_15_5

   .. tb-tab:: Question

      ROT13 is a simple Caesar cipher that replaces each letter in a string
      with the 13th letter after it in the alphabet. For example, using ROT13
      on the letter "a" would turn it into "n". Notice how since 13 is exactly
      half the number of characters in the alphabet, using ROT13 on the letter
      "n" would turn it into "a". Thus, ROT13 can be used to encrypt and decrypt
      messages. Write a program that takes in an input file called ``message.txt,``
      applies ROT13, and outputs the result to the terminal.
      Include proper file error checking.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_5q
         :caption: Example c192_cp_15_ac_5q
         :files: message.txt

         #include <iostream>
         #include <fstream>
         #include <cctype>

         int main() {
             // Write your code here.
         }


   .. tb-tab:: Answer

      Below is one way to implement this program. We create an ``ifstream`` object
      to open our file. We check to make sure the file is opened correctly before
      we read the data values into a string. We call our ``ROT13`` function and
      output the result to the output file.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_5a
         :caption: Example c192_cp_15_ac_5a
         :files: message.txt

         #include <cstddef>
         #include <cstdlib>
         #include <string>
         #include <iostream>
         #include <fstream>
         #include <cctype>

         std::string ROT13 (std::string message) {
             for (std::size_t i = 0; i < message.size(); ++i) {
                 if (std::isalpha(static_cast<unsigned char>(message[i]))) {
                     if (message[i] >= 'A' && message[i] <= 'Z') {
                         if (message[i] <= 'M') {
                             message[i] = message[i] + 13;
                         }
                         else {
                             message[i] = message[i] - 13;
                         }
                     }
                     else {
                          if (message[i] <= 'm') {
                             message[i] = message[i] + 13;
                         }
                         else {
                             message[i] = message[i] - 13;
                         }
                     }
                 }
             }
             return message;
         }

         int main() {
             std::ifstream infile("message.txt");
             std::string message;
             if (!infile.good()) {
                 std::cout << "Error. Unable to open file." << '\n';
                 std::exit(1);
             }
             while (std::getline(infile, message)) {
                 std::cout << ROT13(message) << '\n';
             }
         }


.. tb-group::
   :name: c192_cp_15_7

   .. tb-tab:: Question

      Write a program that reads in data about a class from the file
      ``class_data.txt`` and outputs the rows of data where a
      student has a GPA of at least 3.5. Include proper file error checking.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_7q
         :caption: Example c192_cp_15_ac_7q
         :files: class_data.txt

         #include <iostream>
         #include <fstream>

         int main() {
             // Write your code here.
         }


   .. tb-tab:: Answer

      Below is one way to implement this program. We create an ``ifstream`` object
      to open our file. We check to make sure the file is opened correctly before
      we read the data values into corresponding variables. We check if the GPA
      is at least 3.5, and print the data values to the terminal if so.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_7a
         :caption: Example c192_cp_15_ac_7a
         :files: class_data.txt

         #include <cstdlib>
         #include <string>
         #include <iostream>
         #include <fstream>

         int main() {
             std::ifstream infile("class_data.txt");
             std::string fname, lname;
             int grade, age;
             double gpa;
             if (!infile.good()) {
                 std::cout << "Error. Unable to open file." << '\n';
                 std::exit(1);
             }
             std::getline(infile, fname);
             while (infile >> fname >> lname >> grade >> gpa >> age) {
                 if (gpa >= 3.5) {
                     std::cout << fname << '\t' << lname << '\t' << grade
                          << '\t' << gpa << '\t' << age << '\n';
                 }
             }
         }


.. tb-group::
   :name: c192_cp_15_9

   .. tb-tab:: Question

      Write a program that creates a multiplication table for the first 10
      numbers using a matrix and outputting the table to an output file
      called ``mult_table.txt``. Include proper file error checking.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_9q
         :caption: Example c192_cp_15_ac_9q
         :files: mult_table.txt

         #include <iostream>
         #include <fstream>
         #include <vector>

         int main() {
             // Write your code here.
         }

   .. tb-tab:: Answer

      Below is one way to implement this program. We create a 10x10 matrix
      and fill in the products. Then we traverse through the matrix and output
      the values into the output file.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_9a
         :caption: Example c192_cp_15_ac_9a
         :files: mult_table.txt

         #include <cstddef>
         #include <cstdlib>
         #include <iostream>
         #include <fstream>
         #include <vector>

         int main() {
             std::ofstream outfile("mult_table.txt");
             if (!outfile.good()) {
                 std::cout << "Error. Unable to open file." << '\n';
                 std::exit(1);
             }
             std::vector<std::size_t> rows(10);
             std::vector<std::vector<std::size_t>> mat;
             for (std::size_t i = 0; i < 10; ++i) {
                 mat.push_back(rows);
             }
             for (std::size_t i = 0; i < 10; ++i) {
                 for (std::size_t j = 0; j < 10; ++j) {
                     mat[i][j] = (i + 1) * (j + 1);
                 }
             }
             for (std::size_t i = 0; i < 10; ++i) {
                 for (std::size_t j = 0; j < 10; ++j) {
                     outfile << mat[i][j] << '\t';
                 }
                 outfile << '\n';
             }
         }


.. tb-group::
   :name: c192_cp_15_1

   .. tb-tab:: Question

      Write a program that takes in an input file called ``poem.txt``
      and prints the first 5 lines to the terminal. Include proper
      file error checking.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_1q
         :caption: Example c192_cp_15_ac_1q
         :files: poem.txt

         #include <iostream>
         #include <fstream>

         // Write your code here.


   .. tb-tab:: Answer

      Below is one way to implement this program. We create an ``ifstream`` object
      to open our file. We check to make sure the file is opened correctly before
      we use ``getline`` in a ``for`` loop to retrieve and print the first 5
      lines of the poem.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_1a
         :caption: Example c192_cp_15_ac_1a
         :files: poem.txt

         #include <cstddef>
         #include <cstdlib>
         #include <string>
         #include <iostream>
         #include <fstream>

         int main() {
             std::ifstream infile("poem.txt");
             std::string input;
             if (!infile.good()) {
                 std::cout << "Error. Unable to open file." << '\n';
                 std::exit(1);
             }
             for (std::size_t i = 0; i < 5; ++i) {
                 std::getline(infile, input);
                 std::cout << input << '\n';
             }
         }



.. tb-group::
   :name: c192_cp_15_2_q

   .. tb-tab:: Question

      Write a program that prompts a user for the name of an input file
      and for an integer ``n``. Then open the file and output the first
      ``n`` lines of the file with each line reversed. For example,
      if you read in the line "hello world" you should print out
      "dlrow olleh" to the terminal. Include proper file error checking.
      Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_2q
         :caption: Example c192_cp_15_ac_2q
         :stdin: speech.txt
         :files: speech.txt

         #include <iostream>
         #include <fstream>

         // Write your code here.
.. tb-group::
   :name: c192_cp_15_4_q

   .. tb-tab:: Question

      Write a program that prompts a user for an integer ``n`` and print the first ``n``
      powers of 2 to an output file called ``powers.txt``. Include proper file error checking.
      To simulate what your output file would look like, the contents of your output file
      will be displayed on the terminal. Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_4q
         :caption: Example c192_cp_15_ac_4q
         :files: powers.txt

         #include <string>
         #include <iostream>
         #include <fstream>
         #include <cmath>

         int main() {
            // Write your code here.





            // Do not modify the code below
            std::ifstream student_output("powers.txt");
            if (!student_output.good()) {
                  std::cout << "Error opening student's output." << '\n';
            }
            std::string answer;
            while (std::getline(student_output, answer)) {
                  std::cout << answer << '\n';
            }
         }
.. tb-group::
   :name: c192_cp_15_6_q

   .. tb-tab:: Question

      Write a program that takes an input file called "dream.txt" and outputs
      the number of times the string "you" appears in the file to the terminal.
      Include proper file error checking.
      Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_6q
         :caption: Example c192_cp_15_ac_6q
         :files: dream.txt

         #include <iostream>
         #include <fstream>

         // Write your code here.
.. tb-group::
   :name: c192_cp_15_8_q

   .. tb-tab:: Question

      Write a program that takes an input file called "shrimp.txt" and outputs
      the quote with "shrimp" replaced by a word that the user inputs to the terminal.
      Include proper file error checking.
      Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_8q
         :caption: Example c192_cp_15_ac_8q
         :files: shrimp.txt

         #include <iostream>
         #include <fstream>

         // Write your code here.
.. tb-group::
   :name: c192_cp_15_10_q

   .. tb-tab:: Question

      Multiply a two-by-three array by a three-by-two array. The result
      has two rows and two columns. For each result element, sum the
      products of the corresponding row and column entries.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_10q
         :caption: Example c192_cp_15_ac_10q

         #include <array>
         #include <cstddef>
         #include <iostream>

         int main() {
             std::array<std::array<int, 3>, 2> a{{{1, 2, 3}, {4, 5, 6}}};
             std::array<std::array<int, 2>, 3> b{{{7, 8}, {9, 10}, {11, 12}}};
             // Write your multiplication and print the result.
         }
.. tb-group::
   :name: c192_mucp_15_1_ac

   .. tb-tab:: Question

       We have a file called "locations.txt" that we want to read data from.
       Check to make sure that the file was opened properly; if it wasn't,
       display an error message and exit with a status of 1.

      .. tb-code:: cpp
         :name: c192_mucp_15_1_ac_q
         :caption: Example c192_mucp_15_1_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write code that makes sure the file was opened properly.

      .. tb-code:: cpp
         :name: c192_mucp_15_1_ac_a
         :caption: Example c192_mucp_15_1_ac_a

         #include <cstdlib>
         #include <fstream>
         #include <iostream>

         int main() {
             std::ifstream infile("locations.txt");
             if (infile.good() == false) {
                 std::cout << "Unable to open the file." << '\n';
                 std::exit(1);
             }
         }
.. tb-group::
   :name: c192_mucp_15_2_ac

   .. tb-tab:: Question

       Let's write a program that prompts the user for a filename and
       opens that file.

      .. tb-code:: cpp
         :name: c192_mucp_15_2_ac_q
         :caption: Example c192_mucp_15_2_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the program.

      .. tb-code:: cpp
         :name: c192_mucp_15_2_ac_a
         :caption: Example c192_mucp_15_2_ac_a

         #include <cstdlib>
         #include <fstream>
         #include <string>
         #include <iostream>

         int main() {
             std::string filename;
             std::cout << "Enter the name of the file: ";
             std::cin >> filename;
             std::ifstream infile(filename);
             if (infile.good() == false) {
                 std::cout << "Unable to open the file." << '\n';
                 std::exit(1);
             }
         }
.. tb-group::
   :name: c192_mucp_15_3_ac

   .. tb-tab:: Question

       Now let's write some output to a file. Write a program that prompts
       a user for a list of 5 integers separated by spaces, calculates the
       average of those integers, and outputs "The average is ``average``"
       to an output file called "average.txt". Put the necessary blocks
       of code in the correct order. Declare the output file first and
       check that it is opened correctly.

      .. tb-code:: cpp
         :name: c192_mucp_15_3_ac_q
         :caption: Example c192_mucp_15_3_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

      Below is one way to write the program.

      .. tb-code:: cpp
         :name: c192_mucp_15_3_ac_a
         :caption: Example c192_mucp_15_3_ac_a

         #include <cstdlib>
         #include <fstream>
         #include <iostream>

         int main() {
            std::ofstream outfile("average.txt");
            if (outfile.good() == false) {
               std::cout << "Unable to open the file." << '\n';
               std::exit(1);
            }
            int sum = 0;
            int n1, n2, n3, n4, n5;
            std::cout << "Enter five integers separated by spaces: ";
            if (!(std::cin >> n1 >> n2 >> n3 >> n4 >> n5)) return 1;
            sum = n1 + n2 + n3 + n4 + n5;
            outfile << "The average is " << sum / 5.0 << '\n';
         }
.. tb-group::
   :name: c192_mucp_15_4_ac

   .. tb-tab:: Question

       We are given a file called "data.txt" with an unknown number of
       ``double`` values. Write a program that finds the minimum, maximum,
       and number of data and outputs these values to a file called
       "summary.txt".
       Declare the input and output files first, and check to see that
       both are opened correctly before dealing with data. Increment the
       number of data points before checking for the min and max.

      .. tb-code:: cpp
         :name: c192_mucp_15_4_ac_q
         :caption: Example c192_mucp_15_4_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the code.

      .. tb-code:: cpp
         :name: c192_mucp_15_4_ac_a
         :caption: Example c192_mucp_15_4_ac_a

         #include <cstddef>
         #include <cstdlib>
         #include <fstream>
         #include <iostream>

         int main() {
             std::ifstream infile("data.txt");
             std::ofstream outfile("summary.txt");
             if (infile.good() == false || outfile.good() == false) {
                 std::cout << "Unable to open a file." << '\n';
                 std::exit(1);
             }
             std::size_t num_data = 1;
             double min, max, value;
             if (!(infile >> value)) { return 1; }
             min = value;
             max = value;
             while (infile >> value) {
                 ++num_data;
                 if (value < min) { min = value; }
                 if (value > max) { max = value; }
             }
             outfile << "Number of data: " << num_data << ", min: " << min << ", max: " << max << '\n';
         }
.. tb-group::
   :name: c192_mucp_15_5_ac

   .. tb-tab:: Question

       You are given a file called "employee_data.txt" and you want to store
       the information from that file into a vector of data. The file contains
       information about an employee's first and last name, age, phone number,
       and email. Write the definition of an ``employee`` before you write your
       ``main`` function. Open and check the file before working with the data.

      .. tb-code:: cpp
         :name: c192_mucp_15_5_ac_q
         :caption: Example c192_mucp_15_5_ac_q

         #include <iostream>
         #include <string>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to define ``employee``.

      .. tb-code:: cpp
         :name: c192_mucp_15_5_ac_a
         :caption: Example c192_mucp_15_5_ac_a

         #include <cstdlib>
         #include <fstream>
         #include <iostream>
         #include <string>
         #include <vector>

         struct employee {
             std::string fname;
             std::string lname;
             int age;
             int phone;
             std::string email;
             employee(std::string f, std::string l, int a, int p, std::string e) {
                 fname = f;
                 lname = l;
                 age = a;
                 phone = p;
                 email = e;
             }
         };

         int main() {
             std::ifstream infile("employee_data.txt");
             if (infile.good() == false) {
                 std::cout << "Unable to open the file." << '\n';
                 std::exit(1);
             }
             std::vector<employee> data;
             std::string fname, lname, email;
             int age, phone;
             while (infile >> fname >> lname >> age >> phone >> email) {
                 employee e(fname, lname, age, phone, email);
                 data.push_back(e);
             }
         }
.. tb-group::
   :name: c192_mucp_15_6_ac

   .. tb-tab:: Question

       You are given a file but it appears that someone's capslock key was stuck
       because everything is in uppercase. Write a program that takes the input from
       the file "UPPER.txt" and converts all the words to lowercase and prints
       out the modified message to a file called "lower.txt". Write the definition
       of the function ``to_lower`` first. Separate the words with spaces.

      .. tb-code:: cpp
         :name: c192_mucp_15_6_ac_q
         :caption: Example c192_mucp_15_6_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the program and ``to_lower`` function.

      .. tb-code:: cpp
         :name: c192_mucp_15_6_ac_a
         :caption: Example c192_mucp_15_6_ac_a

         #include <cctype>
         #include <cstddef>
         #include <cstdlib>
         #include <fstream>
         #include <iostream>
         #include <string>

         std::string upper_to_lower(std::string upper) {
             for (std::size_t i = 0; i < upper.length(); ++i) {
                 upper[i] = static_cast<char>(std::tolower(static_cast<unsigned char>(upper[i])));
             }
             return upper;
         }

         int main() {
             std::ifstream infile("UPPER.txt");
             std::ofstream outfile("lower.txt");
             if (infile.good() == false || outfile.good() == false) {
                 std::cout << "Unable to open a file." << '\n';
                 std::exit(1);
             }
             std::string word;
             while (infile >> word) {
                 std::string upper = upper_to_lower(word);
                 outfile << upper << ' ';
             }
         }
.. tb-group::
   :name: c192_mucp_15_7_ac

   .. tb-tab:: Question

       Nobody ever put a limit on how many files we can work with. Does
       this mean we can open two or more files at once? Yes we can!
       Write a program that combines two files "odds.txt" and "evens.txt"
       into one output file "numbers.txt". You should combine them in a
       way such that "numbers.txt" contains the first odd number then
       the first even number then the second odd number and so on. You
       are guaranteed that there are equal amounts of odd and even numbers.

      .. tb-code:: cpp
         :name: c192_mucp_15_7_ac_q
         :caption: Example c192_mucp_15_7_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the prgram.

      .. tb-code:: cpp
         :name: c192_mucp_15_7_ac_a
         :caption: Example c192_mucp_15_7_ac_a

         #include <cstdlib>
         #include <fstream>
         #include <iostream>

         int main() {
             std::ifstream odds("odds.txt");
             std::ifstream evens("evens.txt");
             std::ofstream outfile("numbers.txt");
             if (!odds.good() || !evens.good() || !outfile.good()) {
                 std::cout << "Unable to open a file." << '\n';
                 std::exit(1);
             }
             int odd, even;
             while (odds >> odd && evens >> even) {
                 outfile << odd << ' ' << even << ' ';
             }
         }
.. tb-group::
   :name: c192_mucp_15_8_ac

   .. tb-tab:: Question

      Convert a vector of names to a set of unique names.

      .. tb-code:: cpp
         :name: c192_mucp_15_8_ac_q
         :caption: Example c192_mucp_15_8_ac_q

         #include <cstddef>
         #include <iostream>
         #include <map>
         #include <set>
         #include <string>
         #include <vector>

         // Write your function and a main that demonstrates it.

   .. tb-tab:: Answer

      .. tb-code:: cpp
         :name: c192_mucp_15_8_ac_a
         :caption: Example c192_mucp_15_8_ac_a

         #include <cstddef>
         #include <iostream>
         #include <map>
         #include <set>
         #include <string>
         #include <vector>

         std::set<std::string> vector_to_set(const std::vector<std::string>& data) {
             std::set<std::string> names;
             for (const auto& name : data) {
                 names.insert(name);
             }
             return names;
         }

         int main() {
             auto names = vector_to_set({"Boston", "Chicago", "Boston"});
             for (const auto& name : names) { std::cout << name << '\n'; }
         }
.. tb-group::
   :name: c192_mucp_15_9_ac

   .. tb-tab:: Question

      Create a rectangular table with rows and columns supplied at run time. Initialize all entries to zero.

      .. tb-code:: cpp
         :name: c192_mucp_15_9_ac_q
         :caption: Example c192_mucp_15_9_ac_q

         #include <cstddef>
         #include <iostream>
         #include <map>
         #include <set>
         #include <string>
         #include <vector>

         // Write your function and a main that demonstrates it.

   .. tb-tab:: Answer

      .. tb-code:: cpp
         :name: c192_mucp_15_9_ac_a
         :caption: Example c192_mucp_15_9_ac_a

         #include <cstddef>
         #include <iostream>
         #include <map>
         #include <set>
         #include <string>
         #include <vector>

         std::vector<std::vector<int>> make_table(std::size_t rows, std::size_t columns) {
             return std::vector<std::vector<int>>(rows, std::vector<int>(columns, 0));
         }

         int main() {
             auto table = make_table(2, 3);
             table.at(1).at(2) = 7;
             std::cout << table.at(1).at(2) << '\n';
         }
.. tb-group::
   :name: c192_mucp_15_10_ac

   .. tb-tab:: Question

      Count repeated city names with a map. Return the frequency of each name.

      .. tb-code:: cpp
         :name: c192_mucp_15_10_ac_q
         :caption: Example c192_mucp_15_10_ac_q

         #include <cstddef>
         #include <iostream>
         #include <map>
         #include <set>
         #include <string>
         #include <vector>

         // Write your function and a main that demonstrates it.

   .. tb-tab:: Answer

      .. tb-code:: cpp
         :name: c192_mucp_15_10_ac_a
         :caption: Example c192_mucp_15_10_ac_a

         #include <cstddef>
         #include <iostream>
         #include <map>
         #include <set>
         #include <string>
         #include <vector>

         std::map<std::string, std::size_t> count_cities(const std::vector<std::string>& names) {
             std::map<std::string, std::size_t> counts;
             for (const auto& name : names) {
                 ++counts[name];
             }
             return counts;
         }

         int main() {
             auto counts = count_cities({"Boston", "Chicago", "Boston"});
             for (const auto& [name, count] : counts) {
                 std::cout << name << ": " << count << '\n';
             }
         }

Files used in the practice
--------------------------

.. tb-file::
   :name: poem-txt
   :filename: poem.txt

   Two roads diverged in a yellow wood,
   And sorry I could not travel both
   And be one traveler, long I stood
   And looked down one as far as I could
   To where it bent in the undergrowth;
   Then took the other, as just as fair,
   And having perhaps the better claim
   Because it was grassy and wanted wear,
   Though as for that the passing there
   Had worn them really about the same,
   And both that morning equally lay
   In leaves no step had trodden black.
   Oh, I kept the first for another day!
   Yet knowing how way leads on to way
   I doubted if I should ever come back.
   I shall be telling this with a sigh
   Somewhere ages and ages hence:
   Two roads diverged in a wood, and I,
   I took the one less traveled by,
   And that has made all the difference.

.. tb-file::
   :name: heights-txt
   :filename: heights.txt

   62	67	75	68	65
   67	70	72	74	66
   72	66	66	73	69
   61	60	73	72	60

.. tb-file::
   :name: powers-txt
   :filename: powers.txt

   student output file


.. tb-file::
   :name: dream-txt
   :filename: dream.txt

   Have you ever had a dream that you,
   um, you had, your, you- you could,
   you’ll do, you- you wants, you, you
   could do so, you- you’ll do, you could-
   you, you want, you want them to do you
   so much you could do anything?


.. tb-file::
   :name: shrimp-txt
   :filename: shrimp.txt

   There's pineapple shrimp, lemon shrimp, coconut shrimp,
   pepper shrimp, shrimp soup, shrimp stew, shrimp salad,
   shrimp and potatoes, shrimp burger, shrimp sandwich.
   That- that's about it.

.. tb-file::
   :name: message-txt
   :filename: message.txt

   Can you encrypt this message and decrypt the message below?
   Pbatenghyngvbaf! Lbh'ir qrpelcgrq guvf zrffntr.

.. tb-file::
   :name: class_data-txt
   :filename: class_data.txt

   First    Last       Grade    GPA    Age
   Alex     Jones      9        3.4    14
   Beth     Hamilton   12       3.7    18
   Charles  White      11       3.5    16
   Daniel   Kim        10       3.8    16
   Ethan    Brooks     11       3.9    17
   Faith    Flemmings  10       3.0    15
   Gina     Zhou       9        3.2    14

.. tb-file::
   :name: mult_table-txt
   :filename: mult_table.txt

   student output file

.. tb-file::
   :name: speech-txt
   :filename: speech.txt

   We choose to go to the Moon. We choose to go to the Moon...
   We choose to go to the Moon in this decade and do the other things,
   not because they are easy, but because they are hard; because that goal
   will serve to organize and measure the best of our energies and skills,
   because that challenge is one that we are willing to accept, one we are
   unwilling to postpone, and one we intend to win, and the others, too.
