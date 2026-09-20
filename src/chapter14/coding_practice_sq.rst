Coding Practice
---------------

.. tb-group::
   :name: c192_cp_14_2_q

   .. tb-tab:: Activecode

       There are errors in the code below. Modify the code so that ``main`` runs
       successfully. Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_2q
         :caption: Example c192_cp_14_ac_2q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         class room {
             private:
                 int length;
                 int width;
                 int height;

             public:
                 int calculate_area () {
                     return length * width;
                 }

                 int calculate_volume () {
                     return length * width * height;
                 }

                 // Add any necessary functions here.
         };

         int main() {
             room r;
             r.length = 12;
             r.width = 14;
             r.height = 10;
             std::cout << "The room with dimensions " << r.length ", " << r.width
                 << ", and " << r.height << " has an area of " << r.calculate_area()
                 << " and a volume of " << r.calculate_volume << '\n';
         }

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_14_ac_2q_pp

          There are errors in the code below. Modify the code so that ``main`` runs
          successfully. Use the lines to construct the code, then go back to complete the Activecode tab.

         .. code-block:: c++

            {{group}}
             class room {
                 private:
                     int length;
                     int width;
                     int height;
            {{endgroup}}
            {{group}}
                 public:
                     int calculate_area () {
                         return length * width;
                     }
            {{endgroup}}
            {{group}}
                     int calculate_volume () {
                         return length * width * height;
                     }
            {{endgroup}}
            {{group}}
                     void set_length (int l) {
                         length = l;
                     }
            {{endgroup}}
            {{group}}
                     int get_length () const {
                         return length;
                     }
            {{endgroup}}
            {{group}}
                     void set_width (int w) {
                         width = w;
                     }
            {{endgroup}}
            {{group}}
                     int get_width () const {
                         return width;
                     }
            {{endgroup}}
            {{group}}
                     void set_height (int h) {
                         height = h;
                     }
            {{endgroup}}
            {{group}}
                     int get_height () const {
                         return height;
                     }
            {{endgroup}}
            {{group}}
             };
            {{endgroup}}
            {{group}}
             int main() {
            {{endgroup}}
            {{group}}
                 room r;
            {{endgroup}}
            {{group}}
                 r.set_length(12);
            {{endgroup}}
            {{group}}
                 r.set_width(14);
            {{endgroup}}
            {{group}}
                 r.set_height(10);
            {{endgroup}}
            {{group}}
                 std::cout << "The room with dimensions " << r.get_length() << ", " << r.get_width()
                     << ", and " << r.get_height() << " has an area of " << r.calculate_area()
                     << " and a volume of " << r.calculate_volume() << '\n';
            {{endgroup}}
            {{group}}
             }
            {{endgroup}}

.. tb-group::
   :name: c192_cp_14_4_q

   .. tb-tab:: Activecode

       in ``main`` create a ``temp`` object to calculate
       what 100 degrees Celsius is in Fahrenheit.
       Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_4q
         :caption: Example c192_cp_14_ac_4q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         class temp {
             private:
                 double fahrenheit;
                 double celsius;
                 bool is_fahrenheit;
                 bool is_celsius;

                 double c_to_f() {
                     return celsius * 9/5 + 32;
                 }

                 double f_to_c() {
                     return (fahrenheit - 32) * 5/9;
                 }

             public:
                 double get_fahrenheit () {
                     if (is_celsius) { return c_to_f(); }
                     else { return fahrenheit; }
                 }
                 double get_celsius () {
                     if (is_fahrenheit) { return f_to_c(); }
                     else { return celsius; }
                 }
                 void set_fahrenheit (double f) { fahrenheit = f; is_fahrenheit = true; is_celsius = false; }
                 void set_celsius (double c) { celsius = c; is_celsius = true; is_fahrenheit = false; }
                 void print_temp () {
                     if (is_fahrenheit) {
                         std::cout << "It is " << get_fahrenheit() << " degrees Fahrenheit" << '\n';
                     }
                     else {
                         std::cout << "It is " << get_celsius() << " degrees Celsius" << '\n';
                     }
                 }
         };

         int main() {
             // Write your code here.
         }

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_14_ac_4q_pp

          in ``main`` create a ``temp`` object to calculate
          what 100 degrees Celsius is in Fahrenheit.
          Use the lines to construct the code, then go back to complete the Activecode tab.

         .. code-block:: c++

            {{group}}
             int main() {
            {{endgroup}}
            {{group}}
                 temp t;
            {{endgroup}}
            {{group}}
                 t.set_celsius(100);
            {{endgroup}}
            {{group}}
                 t.set_fahrenheit(t.get_fahrenheit());
            {{endgroup}}
            {{group}}
                 t.print_temp();
            {{endgroup}}
            {{group}}
             }
            {{endgroup}}

.. tb-group::
   :name: c192_cp_14_6_q

   .. tb-tab:: Activecode

       What if we had an existing ``vector`` with data that we want to copy
       into our ``my_vector``? Write a constructor that takes a ``vector``
       and copies the data into the ``elements`` vector.
       Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_6q
         :caption: Example c192_cp_14_ac_6q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>

         class my_vector {
             private:
                 std::vector<int> elements;

             public:
                 my_vector() {};
                 // Write your constructor here.
         };

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_14_ac_6q_pp

          What if we had an existing ``vector`` with data that we want to copy
          into our ``my_vector``? Write a constructor that takes a ``vector``
          and copies the data into the ``elements`` vector.
          Use the lines to construct the code, then go back to complete the Activecode tab.

         .. code-block:: c++

            {{group}}
             my_vector (std::vector<int> vec) {
            {{endgroup}}
            {{group}}
                elements = vec;
            {{endgroup}}
            {{group}}
             }
            {{endgroup}}

.. tb-group::
   :name: c192_cp_14_8_q

   .. tb-tab:: Activecode

       Now we can write some of our own fun functions! No longer
       do we need to write ``for`` loops every time we want to
       print out a ``vector``. With ``my_vector``, we can just
       call the member function ``print``! Write the ``my_vector``
       member function ``print``, which prints out the contents
       of ``my_vector``. For example, if our ``my_vector`` contained
       the elements 2, 5, 1, and 8, ``print`` should print out
       [2, 5, 1, 8] followed by a newline.
       Select the Parsonsprob tab for hints for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_8q-support
         :hidden:
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         my_vector::my_vector (std::vector<int> vec) {
             elements = vec;
         }

         std::size_t my_vector::size() { return elements.size(); }

         void my_vector::push_back(int value) { elements.push_back(value); }

         void my_vector::pop_back() { if (elements.empty()) throw std::out_of_range("empty vector");
             elements.pop_back(); };

         int my_vector::at(std::size_t index) { return elements.at(index); }

      .. tb-code:: cpp
         :name: c192_cp_14_ac_8q
         :caption: Example c192_cp_14_ac_8q
         :run-after: c192_cp_14_ac_8q-support
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <stdexcept>
         #include <cstddef>
         #include <iostream>
         #include <vector>

         class my_vector {
             private:
                 std::vector<int> elements;

             public:
                 my_vector() {};
                 my_vector(std::vector<int> vec);

                 std::size_t size();
                 void push_back(int value);
                 void pop_back();
                 int at(std::size_t index);

                 // Write your print function here.
         };

         int main() {
             my_vector my_vec;
             my_vec.push_back(13);
             my_vec.push_back(2);
             my_vec.push_back(4);
             my_vec.push_back(7);
             my_vec.push_back(9);
             my_vec.push_back(24);
             my_vec.print();
         }

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_14_ac_8q_pp

          Now we can write some of our own fun functions! No longer
          do we need to write ``for`` loops every time we want to
          print out a ``vector``. With ``my_vector``, we can just
          call the member function ``print``! Write the ``my_vector``
          member function ``print``, which prints out the contents
          of ``my_vector``. For example, if our ``my_vector`` contained
          the elements 2, 5, 1, and 8, ``print`` should print out
          [2, 5, 1, 8] followed by a newline. Use the lines to construct
          the code, then go back to complete the Activecode tab.

         .. code-block:: c++

            {{group}}
             void print() {
            {{endgroup}}
            {{group}}
                std::cout << '[';
            {{endgroup}}
            {{group}}
                for (std::size_t i = 0; i < elements.size(); ++i) {
            {{endgroup}}
            {{group}}
                    if (i != 0) std::cout << ", ";
                    std::cout << elements[i];
            {{endgroup}}
            {{group}}
                }
            {{endgroup}}
            {{group}}
                std::cout << ']' << '\n';
            {{endgroup}}
            {{group}}
             }
            {{endgroup}}

.. tb-group::
   :name: c192_cp_14_10_q

   .. tb-tab:: Activecode

       What if we wanted to return the largest and smallest elements in our
       ``my_vector``? Write the public member functions ``max`` and ``min``
       which calls the private member functions ``find_max`` and ``find_min``.
       ``find_max`` and ``find_min`` return the indices of the max and min
       values, and ``max`` and ``min`` call these private member functions
       and return the max and min values. Select the Parsonsprob tab for hints
       for the construction of the code.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_10q-support
         :hidden:
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         my_vector::my_vector (std::vector<int> vec) {
             elements = vec;
         }

         std::size_t my_vector::size() { return elements.size(); }

         void my_vector::push_back(int value) { elements.push_back(value); }

         void my_vector::pop_back() { if (elements.empty()) throw std::out_of_range("empty vector");
             elements.pop_back(); };

         int my_vector::at(std::size_t index) { return elements.at(index); }

         void my_vector::print() {
             std::cout << '[';
             for (std::size_t i = 0; i < elements.size(); ++i) {
                 if (i != 0) std::cout << ", ";
                 std::cout << elements[i];
             }
             std::cout << ']' << '\n';
         }

         void my_vector::push_front(int value) {
             std::vector<int> temp;
             temp.push_back(value);
             for (std::size_t i = 0; i < elements.size(); ++i) {
                 temp.push_back(elements[i]);
             }
             elements = temp;
         }

         void my_vector::pop_front() {
             for (std::size_t i = 1; i < elements.size(); ++i) {
                 elements[i - 1] = elements[i];
             }
             if (elements.empty()) throw std::out_of_range("empty vector");
             elements.pop_back();
         }

      .. tb-code:: cpp
         :name: c192_cp_14_ac_10q
         :caption: Example c192_cp_14_ac_10q
         :run-after: c192_cp_14_ac_10q-support
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <stdexcept>
         #include <cstddef>
         #include <iostream>
         #include <vector>
         using std::cout;

         class my_vector {
             private:
                 std::vector<int> elements;

                 // Write your find_max function here.

                 // Write your find_min function here.

             public:
                 my_vector() {};
                 my_vector(std::vector<int> vec);

                 std::size_t size();
                 void push_back(int value);
                 void pop_back();
                 int at(std::size_t index);
                 void print();
                 void push_front(int value);
                 void pop_front();
         };

         // Write your max function here.

         // Write your min function here.

         int main() {
             std::vector<int> vec = { 8, 1, 5, 87, 23, 64 };
             my_vector my_vec(vec);
             cout << "The largest element is " << my_vec.max() << '\n';
             cout << "The smallest element is " << my_vec.min() << '\n';
         }

   .. tb-tab:: Parsonsprob

      .. tb-parsons::
         :name: c192_cp_14_ac_10q_pp

          What if we wanted to return the largest and smallest elements in our
          ``my_vector``? Write the public member functions ``max`` and ``min``
          which calls the private member functions ``find_max`` and ``find_min``.
          ``find_max`` and ``find_min`` return the indices of the max and min
          values, and ``max`` and ``min`` call these private member functions
          and return the max and min values. Use the lines to construct the code,
          then go back to complete the Activecode tab. Include ``<stdexcept>`` for the empty-vector check. Be sure to declare the ``max`` and ``min``
          functions in ``public`` when you complete the Activecode.

         .. code-block:: c++

            {{group}}
             // find_max private member function
             std::size_t find_max (const std::vector<int>& vec) {
            {{endgroup}}
            {{group}}
                 if (vec.empty()) throw std::out_of_range("empty vector");
                 std::size_t in_max = 0;
            {{endgroup}}
            {{group}}
                 int max = vec[0];
            {{endgroup}}
            {{group}}
                 for (std::size_t i = 1; i < vec.size(); i++) {
            {{endgroup}}
            {{group}}
                     if (vec[i] > max) {
            {{endgroup}}
            {{group}}
                         max = vec[i];
            {{endgroup}}
            {{group}}
                         in_max = i;
            {{endgroup}}
            {{group}}
                     }
            {{endgroup}}
            {{group}}
                 }
            {{endgroup}}
            {{group}}
                 return in_max;
            {{endgroup}}
            {{group}}
             }
            {{endgroup}}
            {{group}}
             // find_min private member function
             std::size_t find_min (const std::vector<int>& vec) {
            {{endgroup}}
            {{group}}
                 if (vec.empty()) throw std::out_of_range("empty vector");
                 std::size_t in_min = 0;
            {{endgroup}}
            {{group}}
                 int min = vec[0];
            {{endgroup}}
            {{group}}
                 for (std::size_t i = 0; i < vec.size(); i++) {
            {{endgroup}}
            {{group}}
                     if (vec[i] < min) {
            {{endgroup}}
            {{group}}
                         min = vec[i];
            {{endgroup}}
            {{group}}
                         in_min = i;
            {{endgroup}}
            {{group}}
                     }
            {{endgroup}}
            {{group}}
                 }
            {{endgroup}}
            {{group}}
                 return in_min;
            {{endgroup}}
            {{group}}
             }
            {{endgroup}}
            {{group}}
             // max public member function
             int my_vector::max () {
            {{endgroup}}
            {{group}}
                 return elements[find_max(elements)];
            {{endgroup}}
            {{group}}
             }
            {{endgroup}}
            {{group}}
             // min public member function
             int my_vector::min () {
            {{endgroup}}
            {{group}}
                 return elements[find_min(elements)];
            {{endgroup}}
            {{group}}
             }
            {{endgroup}}

