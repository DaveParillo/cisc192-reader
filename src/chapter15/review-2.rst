.. _files-containers-mixed-up-code-exercises:

Mixed-Up Code Exercises
-----------------------

Arrange the following **Mixed-Up Code** exercises to
assess what you have learned in this chapter.

.. _files-containers-parsons-exercises:

Parsons exercises
~~~~~~~~~~~~~~~~~

.. tb-parsons::
   :name: c192_cp_15_ac_2q_pp

   Write a program that prompts a user for the name of an input file
   and for an integer ``n``. Then open the file and output the first
   ``n`` lines of the file with each line reversed. For example,
   if you read in the line "hello world" you should print out
   "dlrow olleh" to the terminal. Include proper file error checking.
   Use the lines to construct the code, then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
      int main () {
      {{endgroup}}
      {{group}}
         std::string file_in;
      {{endgroup}}
      {{group}}
         std::size_t n = 0;
      {{endgroup}}
      {{group}}
         std::string line;
      {{endgroup}}
      {{group}}
         std::cout << "Enter the name of the file: ";
         std::cin >> file_in;
         std::cout << file_in << '\n';
      {{endgroup}}
      {{group}}
         std::cout << "Enter an integer: ";
         std::cin >> n;
         std::cout << n << '\n';
      {{endgroup}}
      {{group}}
         std::ifstream in_file(file_in);
      {{endgroup}}
      {{group}}
         if (in_file.good() == false) {
            std::cout << "Unable to open the file named " << file_in << " and output " << n << " lines." << '\n';
            std::exit(1);
         }
      {{endgroup}}
      {{group}}
         for (std::size_t i = 0; i < n; i++) {
      {{endgroup}}
      {{group}}
            std::getline(in_file, line);
      {{endgroup}}
      {{group}}
            std::cout << line << '\n';
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_15_ac_4q_pp

   Write a program that prompts a user for an integer ``n`` and print the first ``n``
   powers of 2 to an output file called ``powers.txt``. Include proper file error checking.
   To simulate what your output file would look like, the contents of your output file
   will be displayed on the terminal. Use the lines to construct the code, then go back
   to complete the code tab.

   .. code-block:: c++

      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         std::size_t n = 0;
      {{endgroup}}
      {{group}}
         std::cout << "Enter an integer: ";
      {{endgroup}}
      {{group}}
         std::cin >> n;
      {{endgroup}}
      {{group}}
         std::cout << n << '\n';
      {{endgroup}}
      {{group}}
         std::ofstream outfile ("powers.txt");
      {{endgroup}}
      {{group}}
         if (outfile.good() == false) {
            std::cout << "Unable to open output file." << '\n';
            std::exit (1);
         }
      {{endgroup}}
      {{group}}
         while (true) {
      {{endgroup}}
      {{group}}
            for (std::size_t i = 0; i < n; i++) {
      {{endgroup}}
      {{group}}
                  outfile << std::pow(2,i) << '\n';
      {{endgroup}}
      {{group}}
            }
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         std::ifstream student_output("powers.txt");
      {{endgroup}}
      {{group}}
         if (!student_output.good()) {
            std::cout << "Error opening student's output." << '\n';
         }
      {{endgroup}}
      {{group}}
         std::string answer;
      {{endgroup}}
      {{group}}
         while (std::getline(student_output, answer)) {
            std::cout << answer << '\n';
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_15_ac_6q_pp

   Write a program that takes an input file called "dream.txt" and outputs
   the number of times the string "you" appears in the file to the terminal.
   Include proper file error checking. Use the lines to construct the code,
   then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         std::size_t count = 0;
      {{endgroup}}
      {{group}}
         char w[ ] = {'y', 'o', 'u'};
      {{endgroup}}
      {{group}}
         std::ifstream in_file("dream.txt");
      {{endgroup}}
      {{group}}
         std::string line;
      {{endgroup}}
      {{group}}
         if (!in_file.good()) {
            std::cout << "Unable to open file." << '\n';
            std::exit(1);
         }
      {{endgroup}}
      {{group}}
         while (std::getline(in_file,line)) {
      {{endgroup}}
      {{group}}
            for (std::size_t i = 0; i < line.size(); i++) {
      {{endgroup}}
      {{group}}
                  if (line.at(i) == w[0]) {
      {{endgroup}}
      {{group}}
                     if (line.at(i+1) == w[1]) {
      {{endgroup}}
      {{group}}
                        if (line.at (i+2) == w[2]) {
      {{endgroup}}
      {{group}}
                              count++;
      {{endgroup}}
      {{group}}
                        }
      {{endgroup}}
      {{group}}
                     }
      {{endgroup}}
      {{group}}
                  }
      {{endgroup}}
      {{group}}
            }
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         std::cout << count << '\n';
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_15_ac_8q_pp

   Write a program that takes an input file called "shrimp.txt" and outputs
   the quote with "shrimp" replaced by a word that the user inputs to the terminal.
   Include proper file error checking.
   Use the lines to construct the code, then complete the code in the correct order.

   .. code-block:: c++

      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         std::string word;
      {{endgroup}}
      {{group}}
         std::cout << "Enter word to replace 'shrimp': ";
      {{endgroup}}
      {{group}}
         std::cin >> word;
      {{endgroup}}
      {{group}}
         std::cout << word << '\n';
      {{endgroup}}
      {{group}}
         std::string replace = "shrimp";
      {{endgroup}}
      {{group}}
         std::ifstream in_file("shrimp.txt");
      {{endgroup}}
      {{group}}
         std::string line;
      {{endgroup}}
      {{group}}
         for (std::size_t i = 0; i < 4; i++) {
      {{endgroup}}
      {{group}}
            std::getline(in_file,line);
      {{endgroup}}
      {{group}}
            for (std::size_t j = 0; j < line.size(); j++) {
      {{endgroup}}
      {{group}}
               std::size_t pos = line.find(replace);
      {{endgroup}}
      {{group}}
               if (pos != std::string::npos) {
      {{endgroup}}
      {{group}}
                  line.replace(pos,replace.length(),word);
      {{endgroup}}
      {{group}}
               }
      {{endgroup}}
      {{group}}
            }
      {{endgroup}}
      {{group}}
            std::cout << line<< '\n';
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_cp_15_ac_10q_pp

   Construct the multiplication program. Include the array, cstddef,
   and iostream headers. The result should be 58 64 on the first
   row and 139 154 on the second row.

   .. code-block:: c++

      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
          std::array<std::array<int, 3>, 2> a{{{1, 2, 3}, {4, 5, 6}}};
      {{endgroup}}
      {{group}}
          std::array<std::array<int, 2>, 3> b{{{7, 8}, {9, 10}, {11, 12}}};
      {{endgroup}}
      {{group}}
          std::array<std::array<int, 2>, 2> product{};
      {{endgroup}}
      {{group}}
          for (std::size_t row = 0; row < a.size(); ++row) {
      {{endgroup}}
      {{group}}
              for (std::size_t col = 0; col < b[0].size(); ++col) {
      {{endgroup}}
      {{group}}
                  for (std::size_t k = 0; k < b.size(); ++k) {
      {{endgroup}}
      {{group}}
                      product[row][col] += a[row][k] * b[k][col];
      {{endgroup}}
      {{group}}
                  }
      {{endgroup}}
      {{group}}
              }
      {{endgroup}}
      {{group}}
          }
      {{endgroup}}
      {{group}}
          for (const auto& row : product) {
      {{endgroup}}
      {{group}}
              for (int value : row) { std::cout << value << ' '; }
      {{endgroup}}
      {{group}}
              std::cout << '\n';
      {{endgroup}}
      {{group}}
          }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_mucp_15_1
   :no-indent:

   We have a file called "locations.txt" that we want to read data from.
   Check to make sure that the file was opened properly; if it wasn't,
   display an error message and exit with a status of 1.
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         std::ifstream infile("locations.txt");
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::ifstream infile(locations.txt);
      {{endgroup}}
      {{group}}
         if (infile.good() == false) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         if (infile.good()) {
      {{endgroup}}
      {{group}}
            std::cout << "Unable to open the file." << '\n';
      {{endgroup}}
      {{group}}
            std::exit(1);
      {{endgroup}}
      {{distractor}}
      {{group}}
            return 1;
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_mucp_15_2
   :no-indent:

   Let's write a program that prompts the user for a filename and
   opens that file. Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         std::string filename;
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::ifstream filename;
      {{endgroup}}
      {{group}}
         std::cout << "Enter the name of the file: ";
      {{endgroup}}
      {{group}}
         std::cin >> filename;
      {{endgroup}}
      {{group}}
         std::ifstream infile(filename);
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::ofstream infile(filename);
      {{endgroup}}
      {{group}}
         if (infile.good() == false) {
      {{endgroup}}
      {{group}}
            std::cout << "Unable to open the file." << '\n';
      {{endgroup}}
      {{group}}
            std::exit(1);
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_mucp_15_3
   :no-indent:

   Now let's write some output to a file. Write a program that prompts
   a user for a list of 5 integers separated by spaces, calculates the
   average of those integers, and outputs "The average is ``average``"
   to an output file called "average.txt". Put the necessary blocks
   of code in the correct order. Declare the output file first and
   check that it is opened correctly.

   .. code-block:: c++

      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         std::ofstream outfile("average.txt");
      {{endgroup}}
      {{group}}
         if (outfile.good() == false) {
            std::cout << "Unable to open the file." << '\n';
            std::exit(1);
         }
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::vector<int> list;  #distractor
      {{endgroup}}
      {{group}}
         int sum = 0;
      {{endgroup}}
      {{group}}
         int n1, n2, n3, n4, n5;
      {{endgroup}}
      {{group}}
         std::cout << "Enter five integers separated by spaces: ";
      {{endgroup}}
      {{group}}
         std::cin >> n1 >> n2 >> n3 >> n4 >> n5;
      {{endgroup}}
      {{group}}
         sum = n1 + n2 + n3 + n4 + n5;
      {{endgroup}}
      {{group}}
         outfile << "The average is " << sum / 5.0 << '\n';
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::cout << "The average is " << sum / 5.0 << '\n';
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_mucp_15_4

   We are given a file called "data.txt" with an unknown number of
   ``double`` values. Write a program that finds the minimum, maximum,
   and number of data and outputs these values to a file called
   "summary.txt". Put the necessary blocks of code in the correct order.
   Declare the input and output files first, and check to see that
   both are opened correctly before dealing with data. Increment the
   number of data points before checking for the min and max.

   .. code-block:: c++

      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         std::ifstream infile("data.txt");
      {{endgroup}}
      {{group}}
         std::ofstream outfile("summary.txt");
      {{endgroup}}
      {{group}}
         if (infile.good() == false || outfile.good() == false) {
            std::cout << "Unable to open a file." << '\n';
            std::exit(1);
         }
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::vector<int> data;  #distractor
      {{endgroup}}
      {{group}}
         std::size_t num_data = 1;
      {{endgroup}}
      {{group}}
         double min, max, value;
      {{endgroup}}
      {{group}}
         if (!(infile >> value)) { return 1; }
      {{endgroup}}
      {{group}}
         min = value;
      {{endgroup}}
      {{group}}
         max = value;
      {{endgroup}}
      {{group}}
         while (infile >> value) {
      {{endgroup}}
      {{group}}
            ++num_data;
      {{endgroup}}
      {{group}}
            if (value < min) { min = value; }
      {{endgroup}}
      {{group}}
            if (value > max) { max = value; }
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         outfile << "Number of data: " << num_data << ", min: " << min << ", max: " << max << '\n';
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_mucp_15_5

   You are given a file called "employee_data.txt" and you want to store
   the information from that file into a vector of data. The file contains
   information about an employee's first and last name, age, phone number,
   and email. Write the definition of an ``employee`` before you write your
   ``main`` function. Open and check the file before working with the data.
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      struct employee {
         std::string fname;
         std::string lname;
         int age;
         int phone;
         std::string email;
      {{endgroup}}
      {{group}}
         employee(std::string f, std::string l, int a, int p, std::string e) {
            fname = f;
            lname = l;
            age = a;
            phone = p;
            email = e;
         }
      {{endgroup}}
      {{group}}
      };
      {{endgroup}}
      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         std::ifstream infile("employee_data.txt");
      {{endgroup}}
      {{group}}
         if (infile.good() == false) {
            std::cout << "Unable to open the file." << '\n';
            std::exit(1);
         }
      {{endgroup}}
      {{group}}
         std::vector<employee> data;
      {{endgroup}}
      {{group}}
         std::string fname, lname, email;
      {{endgroup}}
      {{group}}
         int age, phone;
      {{endgroup}}
      {{group}}
         while (infile >> fname >> lname >> age >> phone >> email) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         while (infile) {
      {{endgroup}}
      {{group}}
            employee e(fname, lname, age, phone, email);
      {{endgroup}}
      {{group}}
            data.push_back(e);
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_mucp_15_6

   You are given a file but it appears that someone's capslock key was stuck
   because everything is in uppercase. Write a program that takes the input from
   the file "UPPER.txt" and converts all the words to lowercase and prints
   out the modified message to a file called "lower.txt". Write the definition
   of the function ``to_lower`` first. Separate the words with spaces.
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      std::string upper_to_lower(std::string upper) {
         for (std::size_t i = 0; i < upper.length(); ++i) {
      {{endgroup}}
      {{group}}
            upper[i] = static_cast<char>(std::tolower(static_cast<unsigned char>(upper[i])));
      {{endgroup}}
      {{distractor}}
      {{group}}
            std::tolower(upper[i]);
      {{endgroup}}
      {{group}}
         }
         return upper;
      }
      {{endgroup}}
      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         std::ifstream infile("UPPER.txt");
      {{endgroup}}
      {{group}}
         std::ofstream outfile("lower.txt");
      {{endgroup}}
      {{group}}
         if (infile.good() == false || outfile.good() == false) {
            std::cout << "Unable to open a file." << '\n';
            std::exit(1);
         }
      {{endgroup}}
      {{group}}
         std::string word;
      {{endgroup}}
      {{group}}
         while (infile >> word) {
      {{endgroup}}
      {{group}}
            std::string upper = upper_to_lower(word);
      {{endgroup}}
      {{distractor}}
      {{group}}
            upper_to_lower(word);
      {{endgroup}}
      {{group}}
            outfile << upper << ' ';
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_mucp_15_7

   Nobody ever put a limit on how many files we can work with. Does
   this mean we can open two or more files at once? Yes we can!
   Write a program that combines two files "odds.txt" and "evens.txt"
   into one output file "numbers.txt". You should combine them in a
   way such that "numbers.txt" contains the first odd number then
   the first even number then the second odd number and so on. You
   are guaranteed that there are equal amounts of odd and even numbers.
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      int main() {
      {{endgroup}}
      {{group}}
         std::ifstream odds("odds.txt");
      {{endgroup}}
      {{group}}
         std::ifstream evens("evens.txt");
      {{endgroup}}
      {{group}}
         std::ofstream outfile("numbers.txt");
      {{endgroup}}
      {{group}}
         if (!odds.good() || !evens.good() || !outfile.good()) {
            std::cout << "Unable to open a file." << '\n';
            std::exit(1);
         }
      {{endgroup}}
      {{group}}
         int odd, even;
      {{endgroup}}
      {{group}}
         while (odds >> odd && evens >> even) {
      {{endgroup}}
      {{group}}
            outfile << odd << ' ' << even << ' ';
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_mucp_15_8

   Convert a vector of names to a set of unique names. Assume the necessary standard-library headers are included.

   .. code-block:: c++

      {{group}}
      std::set<std::string> vector_to_set(const std::vector<std::string>& data) {
      {{endgroup}}
      {{group}}
          std::set<std::string> names;
      {{endgroup}}
      {{group}}
          for (const auto& name : data) {
      {{endgroup}}
      {{group}}
              names.insert(name);
      {{endgroup}}
      {{group}}
          }
      {{endgroup}}
      {{group}}
          return names;
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_mucp_15_9

   Create a rectangular table with rows and columns supplied at run time. Initialize all entries to zero. Assume the necessary standard-library headers are included.

   .. code-block:: c++

      {{group}}
      std::vector<std::vector<int>> make_table(std::size_t rows, std::size_t columns) {
      {{endgroup}}
      {{group}}
          return std::vector<std::vector<int>>(rows, std::vector<int>(columns, 0));
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
.. tb-parsons::
   :name: c192_mucp_15_10

   Count repeated city names with a map. Return the frequency of each name. Assume the necessary standard-library headers are included.

   .. code-block:: c++

      {{group}}
      std::map<std::string, std::size_t> count_cities(const std::vector<std::string>& names) {
      {{endgroup}}
      {{group}}
          std::map<std::string, std::size_t> counts;
      {{endgroup}}
      {{group}}
          for (const auto& name : names) {
      {{endgroup}}
      {{group}}
              ++counts[name];
      {{endgroup}}
      {{group}}
          }
      {{endgroup}}
      {{group}}
          return counts;
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
