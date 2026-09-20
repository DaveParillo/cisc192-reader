.. _classes-invariants-coding-practice:

Coding Practice
---------------

.. tb-group::
   :name: c192_cp_14_1

   .. tb-tab:: Question

      Below is the ``struct`` definition for ``room``, which has a length,
      width, and height. It also has two member functions, ``calculate_area``
      and ``calculate_volume``. Turn this ``struct`` into a ``class`` with
      private member variables.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_1q
         :caption: Example c192_cp_14_ac_1q

         #include <iostream>

         // Turn the struct definition of room into a class definition.
         struct room {
             int length;
             int width;
             int height;

             int calculate_area () {
                 return length * width;
             }

             int calculate_volume () {
                 return length * width * height;
             }
         };

   .. tb-tab:: Answer

      Below is the ``class`` definition of ``room``. As you can see, there isn't
      a big difference between ``struct``\s and ``class``\es.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_1a
         :caption: Example c192_cp_14_ac_1a

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
         };

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_14_ac_2_sq`` is represented by these exercises:

   * :ref:`c192_cp_14_ac_2q <classes-invariants-coding-practice-2>`

   * :ref:`c192_cp_14_ac_2q_pp <classes-invariants-coding-practice-2>`

.. tb-group::
   :name: c192_cp_14_3

   .. tb-tab:: Question

      Below is the ``class`` definition for ``temp``. Write
      the private member functions ``c_to_f`` and ``f_to_c``,
      which converts Celsius to Fahrenheit and vice versa
      and returns the conversion. Update ``get_fahrenheit``
      and so that if ``is_celsius`` is
      true and a user calls ``get_fahrenheit``, it will
      call ``c_to_f`` and return the correct temperature
      in degrees Fahrenheit. Do the same for ``get_celsius``.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_3q
         :caption: Example c192_cp_14_ac_3q

         #include <iostream>

         class temp {
             private:
                 double fahrenheit;
                 double celsius;
                 bool is_fahrenheit;
                 bool is_celsius;

                 // Write your implementation of c_to_f here.

                 // Write your implementation of f_to_c here.

             public:
                 double get_fahrenheit () { return fahrenheit; }
                 double get_celsius () { return celsius; }
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

   .. tb-tab:: Answer

      Below is one way to implement this. We use the correct conversions
      in ``c_to_f`` and ``f_to_c`` and then call these functions in
      ``get_fahrenheit`` and ``get_celsius`` if needed.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_3a
         :caption: Example c192_cp_14_ac_3a

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

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_14_ac_4_sq`` is represented by these exercises:

   * :ref:`c192_cp_14_ac_4q <classes-invariants-coding-practice-2>`

   * :ref:`c192_cp_14_ac_4q_pp <classes-invariants-coding-practice-2>`

.. tb-group::
   :name: c192_cp_14_5

   .. tb-tab:: Question

      We took a look at ``vector``\s in chapter 10, where we saw
      how we could add data to the end of a ``vector`` and remove
      data from the end of a ``vector``. But what if we wanted to
      add and remove things at the beginning of a ``vector``? Or we wanted to
      print out a ``vector`` without painfully constructing a
      loop every time? We can create our own ``my_vector`` class!
      Write the ``my_vector`` class, which has a ``vector`` of ``int``\s as a
      private member variable. Also write the default constructor.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_5q
         :caption: Example c192_cp_14_ac_5q

         #include <iostream>
         #include <vector>

         // Write the class definition for my_vector here.

   .. tb-tab:: Answer

      Below is the ``class`` definition of ``my_vector``. We use the ``public``
      and ``private`` keywords to separate public and private members of
      our class. The default constructor sets size to 0.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_5a
         :caption: Example c192_cp_14_ac_5a

         #include <iostream>
         #include <vector>

         class my_vector {
             private:
                 std::vector<int> elements;

             public:
                 my_vector() {};
         };

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_14_ac_6_sq`` is represented by these exercises:

   * :ref:`c192_cp_14_ac_6q <classes-invariants-coding-practice-2>`

   * :ref:`c192_cp_14_ac_6q_pp <classes-invariants-coding-practice-2>`

.. tb-group::
   :name: c192_cp_14_7

   .. tb-tab:: Question

      The reason why we have ``elements`` as a private member variable is that
      people using our ``my_vector`` class don't need to know how we implemented
      our class, so we can implement it however we want.
      This means for functions ``my_vector`` has that overlap with
      functions that ``vector`` has, we can just call the same function
      on our ``elements`` vector. Write the ``my_vector`` functions
      ``size``, ``push_back``, ``pop_back``, and ``at``. ``size`` returns
      the size of our ``my_vector``. ``push_back`` takes an
      ``int`` and adds it to the end of our ``my_vector``. ``pop_back``
      removes the last element. ``at`` takes an index and returns the
      data stored at that index. Use existing ``vector`` functions to
      implement these ``my_vector`` functions!

      .. tb-code:: cpp
         :name: c192_cp_14_ac_7q-support
         :hidden:

         my_vector::my_vector (std::vector<int> vec) {
             elements = vec;
         }


      .. tb-code:: cpp
         :name: c192_cp_14_ac_7q
         :caption: Example c192_cp_14_ac_7q
         :run-after: c192_cp_14_ac_7q-support

         #include <iostream>
         #include <vector>

         class my_vector {
             private:
                 std::vector<int> elements;

             public:
                 my_vector() {};
                 my_vector(std::vector<int> vec);

                 // Write the size function here.

                 // Write the push_back function here.

                 // Write the pop_back function here.

                 // Write the at function here.
         };

         int main() {
             std::vector<int> data = { 2, 4, 1, 5, 2, 6 };
             my_vector my_vec(data);
             std::cout << "The first element is " << my_vec.at(0) << '\n';
             my_vec.pop_back();
             my_vec.pop_back();
             my_vec.push_back(12);
             std::cout << "The size of my_vec is " << my_vec.size() << '\n';
             std::cout << "The last three elements are " << my_vec.at(2) << ", "
                  << my_vec.at(3) << ", and " << my_vec.at(4) << '\n';
         }

   .. tb-tab:: Answer

      Below is one way to implement these functions. Since these
      functions are defined for ``vector``\s, we can call them
      on ``elements``.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_7a-support
         :hidden:

         my_vector::my_vector (std::vector<int> vec) {
             elements = vec;
         }


      .. tb-code:: cpp
         :name: c192_cp_14_ac_7a
         :caption: Example c192_cp_14_ac_7a
         :run-after: c192_cp_14_ac_7a-support

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

                 std::size_t size() { return elements.size(); }
                 void push_back(int value) { elements.push_back(value); }
                 void pop_back() { if (elements.empty()) throw std::out_of_range("empty vector");
             elements.pop_back(); };
                 int at(std::size_t index) { return elements.at(index); }
         };

         int main() {
             std::vector<int> data = { 2, 4, 1, 5, 2, 6 };
             my_vector my_vec(data);
             std::cout << "The first element is " << my_vec.at(0) << '\n';
             my_vec.pop_back();
             my_vec.pop_back();
             my_vec.push_back(12);
             std::cout << "The size of my_vec is " << my_vec.size() << '\n';
             std::cout << "The last three elements are " << my_vec.at(2) << ", "
                  << my_vec.at(3) << ", and " << my_vec.at(4) << '\n';
         }

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_14_ac_8_sq`` is represented by these exercises:

   * :ref:`c192_cp_14_ac_8q <classes-invariants-coding-practice-2>`

   * :ref:`c192_cp_14_ac_8q_pp <classes-invariants-coding-practice-2>`

.. tb-group::
   :name: c192_cp_14_9

   .. tb-tab:: Question

      Let's write the ``my_vector`` member function ``push_front`` and
      ``pop_front``. ``push_front`` should take a value and add it
      to the front of our ``my_vector``, and ``pop_front`` should
      remove the first element.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_9q-support
         :hidden:

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


      .. tb-code:: cpp
         :name: c192_cp_14_ac_9q
         :caption: Example c192_cp_14_ac_9q
         :run-after: c192_cp_14_ac_9q-support

         #include <stdexcept>
         #include <cstddef>
         #include <iostream>
         #include <vector>
         using std::cout;

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
                 void print();
         };

         // Write your implementation of push_front here.

         // Write your implementation of pop_front here.

         int main() {
             std::vector<int> data = { 2, 14, 5 };
             my_vector my_vec(data);
             my_vec.pop_front();
             my_vec.push_front(5);
             my_vec.push_front(10);
             cout << "The new size is " << my_vec.size(); << '\n';
             my_vec.print();
         }

   .. tb-tab:: Answer

      Below is one way to implement these functions. For push_front,
      we can create a temporary vector and add the new element to the
      front before pushing the rest of the old elements to the back.
      For pop_front, we can shift all elements up by one index and
      pop the last element off.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_9a-support
         :hidden:

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


      .. tb-code:: cpp
         :name: c192_cp_14_ac_9a
         :caption: Example c192_cp_14_ac_9a
         :run-after: c192_cp_14_ac_9a-support

         #include <stdexcept>
         #include <cstddef>
         #include <iostream>
         #include <vector>
         using std::cout;

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
                 void print();
         public:
             void push_front(int value);
             void pop_front();
         };

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

         int main() {
             std::vector<int> data = { 2, 14, 5 };
             my_vector my_vec(data);
             my_vec.pop_front();
             my_vec.push_front(5);
             my_vec.push_front(10);
             cout << "The new size is " << my_vec.size() << '\n';
             my_vec.print();
         }

.. admonition:: Practice selection

   The legacy Runestone question pool ``c192_cp_14_ac_10_sq`` is represented by these exercises:

   * :ref:`c192_cp_14_ac_10q <classes-invariants-coding-practice-2>`

   * :ref:`c192_cp_14_ac_10q_pp <classes-invariants-coding-practice-2>`

