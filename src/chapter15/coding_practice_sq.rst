Coding Practice
---------------

.. tb-group::
   :name: c192_cp_15_2_q

   .. tb-tab:: Activecode

      Write a program that prompts a user for the name of an input file
      and for an integer ``n``. Then open the file and output the first
      ``n`` lines of the file with each line reversed. For example,
      if you read in the line "hello world" you should print out
      "dlrow olleh" to the terminal. Include proper file error checking.
      Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_2q
         :caption: Example c192_cp_15_ac_2q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
         :stdin: speech.txt
         :files: speech.txt

         #include <iostream>
         #include <fstream>

         // Write your code here.

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_15_ac_2q_pp

         Write a program that prompts a user for the name of an input file
         and for an integer ``n``. Then open the file and output the first
         ``n`` lines of the file with each line reversed. For example,
         if you read in the line "hello world" you should print out
         "dlrow olleh" to the terminal. Include proper file error checking.
         Use the lines to construct the code, then go back to complete the Activecode tab.

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

   .. tb-tab:: Input File

      Below are the contents of the input file.

      ::

         We choose to go to the Moon. We choose to go to the Moon...
         We choose to go to the Moon in this decade and do the other things,
         not because they are easy, but because they are hard; because that goal
         will serve to organize and measure the best of our energies and skills,
         because that challenge is one that we are willing to accept, one we are
         unwilling to postpone, and one we intend to win, and the others, too.

.. tb-group::
   :name: c192_cp_15_4_q

   .. tb-tab:: Activecode

      Write a program that prompts a user for an integer ``n`` and print the first ``n``
      powers of 2 to an output file called ``powers.txt``. Include proper file error checking.
      To simulate what your output file would look like, the contents of your output file
      will be displayed on the terminal. Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_4q
         :caption: Example c192_cp_15_ac_4q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
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

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_15_ac_4q_pp

         Write a program that prompts a user for an integer ``n`` and print the first ``n``
         powers of 2 to an output file called ``powers.txt``. Include proper file error checking.
         To simulate what your output file would look like, the contents of your output file
         will be displayed on the terminal. Use the lines to construct the code, then go back
         to complete the Activecode tab.

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

.. tb-group::
   :name: c192_cp_15_6_q

   .. tb-tab:: Activecode

      Write a program that takes an input file called "dream.txt" and outputs
      the number of times the string "you" appears in the file to the terminal.
      Include proper file error checking.
      Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_6q
         :caption: Example c192_cp_15_ac_6q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
         :files: dream.txt

         #include <iostream>
         #include <fstream>

         // Write your code here.

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_15_ac_6q_pp

         Write a program that takes an input file called "dream.txt" and outputs
         the number of times the string "you" appears in the file to the terminal.
         Include proper file error checking. Use the lines to construct the code,
         then go back to complete the Activecode tab.

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

   .. tb-tab:: Input File

      Below are the contents of the input file.

      .. code-block:: text

         Have you ever had a dream that you,
         um, you had, your, you- you could,
         you’ll do, you- you wants, you, you
         could do so, you- you’ll do, you could-
         you, you want, you want them to do you
         so much you could do anything?

.. tb-group::
   :name: c192_cp_15_8_q

   .. tb-tab:: Activecode

      Write a program that takes an input file called "shrimp.txt" and outputs
      the quote with "shrimp" replaced by a word that the user inputs to the terminal.
      Include proper file error checking.
      Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_8q
         :caption: Example c192_cp_15_ac_8q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
         :files: shrimp.txt

         #include <iostream>
         #include <fstream>

         // Write your code here.

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_15_ac_8q_pp

         Write a program that takes an input file called "shrimp.txt" and outputs
         the quote with "shrimp" replaced by a word that the user inputs to the terminal.
         Include proper file error checking.
         Use the lines to construct the code, then go back to complete the Activecode tab.

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

   .. tb-tab:: Input File

      Below are the contents of the input file.

      .. code-block:: text

          There's pineapple shrimp, lemon shrimp, coconut shrimp,
          pepper shrimp, shrimp soup, shrimp stew, shrimp salad,
          shrimp and potatoes, shrimp burger, shrimp sandwich.
          That- that's about it.

.. tb-group::
   :name: c192_cp_15_10_q

   .. tb-tab:: Activecode

      Multiply a two-by-three array by a three-by-two array. The result
      has two rows and two columns. For each result element, sum the
      products of the corresponding row and column entries.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_10q
         :caption: Example c192_cp_15_ac_10q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <array>
         #include <cstddef>
         #include <iostream>

         int main() {
             std::array<std::array<int, 3>, 2> a{{{1, 2, 3}, {4, 5, 6}}};
             std::array<std::array<int, 2>, 3> b{{{7, 8}, {9, 10}, {11, 12}}};
             // Write your multiplication and print the result.
         }

   .. tb-tab:: Parsonsprob

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
