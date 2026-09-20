Coding Practice
---------------

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

.. tb-group::
   :name: c192_cp_15_1

   .. tb-tab:: Question

      Write a program that takes in an input file called ``poem.txt``
      and prints the first 5 lines to the terminal. Include proper
      file error checking.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_1q
         :caption: Example c192_cp_15_ac_1q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
         :files: poem.txt

         #include <iostream>
         #include <fstream>

         // Write your code here.

   .. tb-tab:: Input File

      Below are the contents of the input file.

      .. code-block:: text

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
          in leaves no step had trodden black.
          Oh, I kept the first for another day!
          Yet knowing how way leads on to way
          I doubted if I should ever come back.
          I shall be telling this with a sigh
          Somewhere ages and ages hence:
          Two roads diverged in a wood, and I,
          I took the one less traveled by,
          And that has made all the difference.

   .. tb-tab:: Answer

      Below is one way to implement this program. We create an ``ifstream`` object
      to open our file. We check to make sure the file is opened correctly before
      we use ``getline`` in a ``for`` loop to retrieve and print the first 5
      lines of the poem.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_1a
         :caption: Example c192_cp_15_ac_1a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
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

.. tb-file::
   :name: speech-txt
   :filename: speech.txt

   We choose to go to the Moon. We choose to go to the Moon...
   We choose to go to the Moon in this decade and do the other things, 
   not because they are easy, but because they are hard; because that goal 
   will serve to organize and measure the best of our energies and skills, 
   because that challenge is one that we are willing to accept, one we are 
   unwilling to postpone, and one we intend to win, and the others, too.

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_15_ac_2_sq`` is represented by these exercises:

   * :doc:`c192_cp_15_ac_2q <coding_practice_sq>`

   * :doc:`c192_cp_15_ac_2q_pp <coding_practice_sq>`

.. tb-file::
   :name: heights-txt
   :filename: heights.txt

   62	67	75	68	65
   67	70	72	74	66
   72	66	66	73	69
   61	60	73	72	60

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
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
         :files: heights.txt

         #include <iostream>
         #include <fstream>
         #include <vector>
         #include <algorithm>

         // Write your code here.

   .. tb-tab:: Input File

      Below are the contents of the input file.

      .. code-block:: text

          62	67	75	68	65
          67	70	72	74	66
          72	66	66	73	69
          61	60	73	72	60

   .. tb-tab:: Answer

      Below is one way to implement this program. We create an ``ifstream`` object
      to open our file. We check to make sure the file is opened correctly before
      we read the data values into a vector. After sorting the vector, we find
      the median depending on whether the number of data values was even or odd.
      Finally, we output our result to the terminal.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_3a
         :caption: Example c192_cp_15_ac_3a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
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

.. tb-file::
   :name: powers-txt
   :filename: powers.txt

   student output file

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_15_ac_4_sq`` is represented by these exercises:

   * :doc:`c192_cp_15_ac_4q <coding_practice_sq>`

   * :doc:`c192_cp_15_ac_4q_pp <coding_practice_sq>`

.. tb-file::
   :name: message-txt
   :filename: message.txt

   Can you encrypt this message and decrypt the message below?
   Pbatenghyngvbaf! Lbh'ir qrpelcgrq guvf zrffntr.

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
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
         :files: message.txt

         #include <iostream>
         #include <fstream>
         #include <cctype>

         int main() {
             // Write your code here.
         }

   .. tb-tab:: Input File

      Below are the contents of the input file.

      .. code-block:: text

          Can you encrypt this message and decrypt the message below?
          Pbatenghyngvbaf! Lbh'ir qrpelcgrq guvf zrffntr.

   .. tb-tab:: Answer

      Below is one way to implement this program. We create an ``ifstream`` object
      to open our file. We check to make sure the file is opened correctly before
      we read the data values into a string. We call our ``ROT13`` function and
      output the result to the output file.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_5a
         :caption: Example c192_cp_15_ac_5a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
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

.. tb-file::
   :name: dream-txt
   :filename: dream.txt

   Have you ever had a dream that you, 
   um, you had, your, you- you could, 
   you’ll do, you- you wants, you, you 
   could do so, you- you’ll do, you could- 
   you, you want, you want them to do you 
   so much you could do anything?

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_15_ac_6_sq`` is represented by these exercises:

   * :doc:`c192_cp_15_ac_6q <coding_practice_sq>`

   * :doc:`c192_cp_15_ac_6q_pp <coding_practice_sq>`

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

.. tb-group::
   :name: c192_cp_15_7

   .. tb-tab:: Question

      Write a program that reads in data about a class from the file
      ``class_data.txt`` and outputs the rows of data where a
      student has a GPA of at least 3.5. Include proper file error checking.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_7q
         :caption: Example c192_cp_15_ac_7q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
         :files: class_data.txt

         #include <iostream>
         #include <fstream>

         int main() {
             // Write your code here.
         }

   .. tb-tab:: Input File

      Below are the contents of the input file.

      ::

          First    Last       Grade    GPA    Age
          Alex     Jones      9        3.4    14
          Beth     Hamilton   12       3.7    18
          Charles  White      11       3.5    16
          Daniel   Kim        10       3.8    16
          Ethan    Brooks     11       3.9    17
          Faith    Flemmings  10       3.0    15
          Gina     Zhou       9        3.2    14

   .. tb-tab:: Answer

      Below is one way to implement this program. We create an ``ifstream`` object
      to open our file. We check to make sure the file is opened correctly before
      we read the data values into corresponding variables. We check if the GPA
      is at least 3.5, and print the data values to the terminal if so.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_7a
         :caption: Example c192_cp_15_ac_7a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
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

.. tb-file::
   :name: shrimp-txt
   :filename: shrimp.txt

   There's pineapple shrimp, lemon shrimp, coconut shrimp, 
   pepper shrimp, shrimp soup, shrimp stew, shrimp salad, 
   shrimp and potatoes, shrimp burger, shrimp sandwich. 
   That- that's about it.

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_15_ac_8_sq`` is represented by these exercises:

   * :doc:`c192_cp_15_ac_8q <coding_practice_sq>`

   * :doc:`c192_cp_15_ac_8q_pp <coding_practice_sq>`

.. tb-file::
   :name: mult_table-txt
   :filename: mult_table.txt

   student output file

.. tb-group::
   :name: c192_cp_15_9

   .. tb-tab:: Question

      Write a program that creates a multiplication table for the first 10
      numbers using a matrix and outputting the table to an output file
      called ``mult_table.txt``. Include proper file error checking.

      .. tb-code:: cpp
         :name: c192_cp_15_ac_9q
         :caption: Example c192_cp_15_ac_9q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
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
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']
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

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_15_ac_10_sq`` is represented by these exercises:

   * :doc:`c192_cp_15_ac_10q <coding_practice_sq>`

   * :doc:`c192_cp_15_ac_10q_pp <coding_practice_sq>`
