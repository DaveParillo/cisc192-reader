.. _files-containers-activecode-exercises:

Activecode Exercises
--------------------

Answer the following **Activecode** questions to assess what you have learned in this chapter.

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

