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
             int m_length;
             int m_width;
             int m_height;

             int calculate_area () {
                 return m_length * m_width;
             }

             int calculate_volume () {
                 return m_length * m_width * m_height;
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
                 int m_length;
                 int m_width;
                 int m_height;

             public:
                 int calculate_area () {
                     return m_length * m_width;
                 }

                 int calculate_volume () {
                     return m_length * m_width * m_height;
                 }
         };


.. tb-group::
   :name: c192_cp_14_3

   .. tb-tab:: Question

      Below is the ``class`` definition for ``temp``. Write
      the private member functions ``c_to_f`` and ``f_to_c``,
      which converts Celsius to Fahrenheit and vice versa
      and returns the conversion. Update ``fahrenheit``
      and so that if ``is_celsius`` is
      true and a user calls ``fahrenheit``, it will
      call ``c_to_f`` and return the correct temperature
      in degrees Fahrenheit. Do the same for ``celsius``.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_3q
         :caption: Example c192_cp_14_ac_3q

         #include <iostream>

         class temp {
             private:
                 double m_fahrenheit;
                 double m_celsius;
                 bool is_fahrenheit;
                 bool is_celsius;

                 // Write your implementation of c_to_f here.

                 // Write your implementation of f_to_c here.

             public:
                 double fahrenheit () { return m_fahrenheit; }
                 double celsius () { return m_celsius; }
                 void fahrenheit (double f) { m_fahrenheit = f; is_fahrenheit = true; is_celsius = false; }
                 void celsius (double c) { m_celsius = c; is_celsius = true; is_fahrenheit = false; }
                 void print_temp () {
                     if (is_fahrenheit) {
                         std::cout << "It is " << fahrenheit() << " degrees Fahrenheit" << '\n';
                     }
                     else {
                         std::cout << "It is " << celsius() << " degrees Celsius" << '\n';
                     }
                 }
         };

   .. tb-tab:: Answer

      Below is one way to implement this. We use the correct conversions
      in ``c_to_f`` and ``f_to_c`` and then call these functions in
      ``fahrenheit`` and ``celsius`` if needed.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_3a
         :caption: Example c192_cp_14_ac_3a

         #include <iostream>

         class temp {
             private:
                 double m_fahrenheit;
                 double m_celsius;
                 bool is_fahrenheit;
                 bool is_celsius;

                 double c_to_f() {
                     return m_celsius * 9/5 + 32;
                 }

                 double f_to_c() {
                     return (m_fahrenheit - 32) * 5/9;
                 }

             public:
                 double fahrenheit () {
                     if (is_celsius) { return c_to_f(); }
                     else { return m_fahrenheit; }
                 }
                 double celsius () {
                     if (is_fahrenheit) { return f_to_c(); }
                     else { return m_celsius; }
                 }
                 void fahrenheit (double f) { m_fahrenheit = f; is_fahrenheit = true; is_celsius = false; }
                 void celsius (double c) { m_celsius = c; is_celsius = true; is_fahrenheit = false; }
                 void print_temp () {
                     if (is_fahrenheit) {
                         std::cout << "It is " << fahrenheit() << " degrees Fahrenheit" << '\n';
                     }
                     else {
                         std::cout << "It is " << celsius() << " degrees Celsius" << '\n';
                     }
                 }
         };


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

.. _classes-invariants-additional-coding-exercises:

Additional coding exercises
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. tb-group::
   :name: c192_cp_14_2_q

   .. tb-tab:: Question

       There are errors in the code below. Modify the code so that ``main`` runs
       successfully. Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_2q
         :caption: Example c192_cp_14_ac_2q

         #include <iostream>

         class room {
             private:
                 int m_length;
                 int m_width;
                 int m_height;

             public:
                 int calculate_area () {
                     return m_length * m_width;
                 }

                 int calculate_volume () {
                     return m_length * m_width * m_height;
                 }

                 // Add any necessary functions here.
         };

         int main() {
             room r;
             r.m_length = 12;
             r.m_width = 14;
             r.m_height = 10;
             std::cout << "The room with dimensions " << r.m_length ", " << r.m_width
                 << ", and " << r.height << " has an area of " << r.calculate_area()
                 << " and a volume of " << r.calculate_volume << '\n';
         }
.. tb-group::
   :name: c192_cp_14_4_q

   .. tb-tab:: Question

       in ``main`` create a ``temp`` object to calculate
       what 100 degrees Celsius is in Fahrenheit.
       Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_4q
         :caption: Example c192_cp_14_ac_4q

         #include <iostream>

         class temp {
             private:
                 double m_fahrenheit;
                 double m_celsius;
                 bool is_fahrenheit;
                 bool is_celsius;

                 double c_to_f() {
                     return m_celsius * 9/5 + 32;
                 }

                 double f_to_c() {
                     return (m_fahrenheit - 32) * 5/9;
                 }

             public:
                 double fahrenheit () {
                     if (is_celsius) { return c_to_f(); }
                     else { return m_fahrenheit; }
                 }
                 double celsius () {
                     if (is_fahrenheit) { return f_to_c(); }
                     else { return m_celsius; }
                 }
                 void fahrenheit (double f) { m_fahrenheit = f; is_fahrenheit = true; is_celsius = false; }
                 void celsius (double c) { m_celsius = c; is_celsius = true; is_fahrenheit = false; }
                 void print_temp () {
                     if (is_fahrenheit) {
                         std::cout << "It is " << fahrenheit() << " degrees Fahrenheit" << '\n';
                     }
                     else {
                         std::cout << "It is " << celsius() << " degrees Celsius" << '\n';
                     }
                 }
         };

         int main() {
             // Write your code here.
         }
.. tb-group::
   :name: c192_cp_14_6_q

   .. tb-tab:: Question

       What if we had an existing ``vector`` with data that we want to copy
       into our ``my_vector``? Write a constructor that takes a ``vector``
       and copies the data into the ``elements`` vector.
       Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_6q
         :caption: Example c192_cp_14_ac_6q

         #include <iostream>
         #include <vector>

         class my_vector {
             private:
                 std::vector<int> elements;

             public:
                 my_vector() {};
                 // Write your constructor here.
         };
.. tb-group::
   :name: c192_cp_14_8_q

   .. tb-tab:: Question

       Now we can write some of our own fun functions! No longer
       do we need to write ``for`` loops every time we want to
       print out a ``vector``. With ``my_vector``, we can just
       call the member function ``print``! Write the ``my_vector``
       member function ``print``, which prints out the contents
       of ``my_vector``. For example, if our ``my_vector`` contained
       the elements 2, 5, 1, and 8, ``print`` should print out
       [2, 5, 1, 8] followed by a newline.
       Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_8q-support
         :hidden:

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
.. tb-group::
   :name: c192_cp_14_10_q

   .. tb-tab:: Question

       What if we wanted to return the largest and smallest elements in our
       ``my_vector``? Write the public member functions ``max`` and ``min``
       which calls the private member functions ``find_max`` and ``find_min``.
       ``find_max`` and ``find_min`` return the indices of the max and min
       values, and ``max`` and ``min`` call these private member functions
       and return the max and min values. Use the code prompt to write your solution.

      .. tb-code:: cpp
         :name: c192_cp_14_ac_10q-support
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
.. tb-group::
   :name: c192_mucp_14_1_ac

   .. tb-tab:: Question

       Let's write the class definition for ``circle``. ``circle`` should have its
       radius stored in a private member variable. Also write the constructor
       for ``circle``, which takes a m_radius as a parameter, in addition to the
       public member function ``calculate_area``, which returns the area of
       the ``circle``. Make sure to include the ``private`` and ``public`` keywords!
       Use 3.14 for the value of pi.

      .. tb-code:: cpp
         :name: c192_mucp_14_1_ac_q
         :caption: Example c192_mucp_14_1_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to wrte the class definition and constructor for ``circle``.

      .. tb-code:: cpp
         :name: c192_mucp_14_11_ac_a
         :caption: Example c192_mucp_14_11_ac_a

         #include <iostream>

         class circle {
             private:
                 double m_radius;
             public:
                 circle (double r) { m_radius = r; }
                 double calculate_area () { return 3.14 * m_radius * m_radius; }
         };
.. tb-group::
   :name: c192_mucp_14_2_ac

   .. tb-tab:: Question

       Now that we have our ``circle`` class, let's write some accessor
       functions! Write the ``circle`` member functions ``radius``
       and ``radius``. It doesn't make sense for a ``circle``'s
       radius to be negative, so in your ``radius`` function,
       output an error message if the given radius is negative.

      .. tb-code:: cpp
         :name: c192_mucp_14_2_ac_q
         :caption: Example c192_mucp_14_2_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the accessor functions for ``radius`` and ``radius``.

      .. tb-code:: cpp
         :name: c192_mucp_14_2_ac_a
         :caption: Example c192_mucp_14_2_ac_a

         #include <iostream>

         class circle {
             private:
                 double m_radius;
             public:
                 circle (double r) { m_radius = r; }
                 double calculate_area () { return 3.14 * m_radius * m_radius; }
                 double radius () {
                     return m_radius;
                 }
                 void radius (double r) {
                     if (r < 0) { std::cout << "Error! Cannot have a negative radius!" << '\n'; }
                     else { m_radius = r; }
                 }
         };
.. tb-group::
   :name: c192_mucp_14_3_ac

   .. tb-tab:: Question

       Write a ``main``. in ``main``, create a ``circle`` with radius 2.4
       and output the radius. Then change the radius to 3.6 and output

      .. tb-code:: cpp
         :name: c192_mucp_14_3_ac_q
         :caption: Example c192_mucp_14_3_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the code.

      .. tb-code:: cpp
         :name: c192_mucp_14_3_ac_a
         :caption: Example c192_mucp_14_3_ac_a

         #include <iostream>

         class circle {
             private:
                 double m_radius;
             public:
                 circle (double r) { m_radius = r; }
                 double calculate_area () { return 3.14 * m_radius * m_radius; }
                 double radius () {
                     return m_radius;
                 }
                 void radius (double r) {
                     if (r < 0) { std::cout << "Error! Cannot have a negative radius!" << '\n'; }
                     else { m_radius = r; }
                 }
         };

         int main() {
             circle c(2.4);
             std::cout << "Radius: " << c.radius () << '\n';
             c.radius (3.6);
             std::cout << "New radius: " << c.radius () << '\n';
         }
.. tb-group::
   :name: c192_mucp_14_4_ac

   .. tb-tab:: Question

       A ``rectangle`` can be constructed given only two points. First,
       write the class definition for ``point``, which stores an x and
       a y value in private member variables. Also write the default constructor, which
       sets x and y to 0, and a constructor that takes in an x_val and y_val.
       in addition, write its accessor functions,
       ``x``, ``y``, ``x``, and ``y``.

      .. tb-code:: cpp
         :name: c192_mucp_14_4_ac_q
         :caption: Example c192_mucp_14_4_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the code.

      .. tb-code:: cpp
         :name: c192_mucp_14_4_ac_a
         :caption: Example c192_mucp_14_4_ac_a

         #include <iostream>

         class point {
             private:
                 double m_x, m_y;
             public:
                 point () { m_x = 0; m_y = 0; }
                 point (double x_val, double y_val) { m_x = x_val; m_y = y_val; }
                 double x () { return m_x; }
                 double y () { return m_y; }
                 void x (double x_val) { m_x = x_val; }
                 void y (double y_val) { m_y = y_val; }
         };
.. tb-group::
   :name: c192_mucp_14_5_ac

   .. tb-tab:: Question

       Now that we've defined the ``point`` class, we can go back to
       writing the ``rectangle`` class. ``rectangle`` should store
       it's upper-left and lower-right points as private member variables.
       Write accessor functions for these variables after the constructor.
       It should also have length and height stored as public member variables.
       Also write a constructor that
       takes an upper-left point and a lower-right point as parameters.

      .. tb-code:: cpp
         :name: c192_mucp_14_5_ac_q
         :caption: Example c192_mucp_14_5_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``rectangle`` class.

      .. tb-code:: cpp
         :name: c192_mucp_14_5_ac_a
         :caption: Example c192_mucp_14_5_ac_a

         #include <iostream>

         class point {
             private:
                 double m_x, m_y;
             public:
                 point () { m_x = 0; m_y = 0; }
                 point (double x_val, double y_val) { m_x = x_val; m_y = y_val; }
                 double x () { return m_x; }
                 double y () { return m_y; }
                 void x (double x_val) { m_x = x_val; }
                 void y (double y_val) { m_y = y_val; }
         };

         class rectangle {
             private:
                 point m_upper_left, m_lower_right;
             public:
                 double m_length, m_height;
                 rectangle (point up_left, point low_right) { m_upper_left = up_left; m_lower_right = low_right; }
                 point upper_left () { return m_upper_left; }
                 point lower_right () { return m_lower_right; }
                 void upper_left (point p) { m_upper_left = p; }
                 void lower_right (point p) { m_lower_right = p; }
         };
.. tb-group::
   :name: c192_mucp_14_6_ac

   .. tb-tab:: Question

       Write the ``rectangle`` member function ``calculate_sides``, which finds
       the length and height of the rectangle using the stored ``point``s.
       Afterwards, write the ``rectangle`` member function ``calculate_area``,
       which returns the area of the rectangle.

      .. tb-code:: cpp
         :name: c192_mucp_14_6_ac_q
         :caption: Example c192_mucp_14_6_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``calculate_sides`` and ``calculate_area`` member functions.

      .. tb-code:: cpp
         :name: c192_mucp_14_6_ac_a
         :caption: Example c192_mucp_14_6_ac_a

         #include <iostream>

         class point {
             private:
                 double m_x, m_y;
             public:
                 point () { m_x = 0; m_y = 0; }
                 point (double x_val, double y_val) { m_x = x_val; m_y = y_val; }
                 double x () { return m_x; }
                 double y () { return m_y; }
                 void x (double x_val) { m_x = x_val; }
                 void y (double y_val) { m_y = y_val; }
         };

         class rectangle {
             private:
                 point m_upper_left, m_lower_right;
             public:
                 double m_length, m_height;
                 rectangle (point up_left, point low_right) { m_upper_left = up_left; m_lower_right = low_right; }
                 point upper_left () { return m_upper_left; }
                 point lower_right () { return m_lower_right; }
                 void upper_left (point p) { m_upper_left = p; }
                 void lower_right (point p) { m_lower_right = p; }
         public:
             void calculate_sides();
             double calculate_area();
         };

         void rectangle::calculate_sides () {
             m_length = lower_right().x() - upper_left().x();
             m_height = upper_left().y() - lower_right().y();
         }

         double rectangle::calculate_area () {
             return m_length * m_height;
         }
.. tb-group::
   :name: c192_mucp_14_7_ac

   .. tb-tab:: Question

       Write a ``main`` in ``main``, create a ``rectangle`` with corners
       at (2.5, 7.5) and (8, 1.5). Print out the length and height, calculate the area,
       and print out the area. Then change the upper_left corner to be at (4.2, 10.7) and
       print out the new area.

      .. tb-code:: cpp
         :name: c192_mucp_14_7_ac_q
         :caption: Example c192_mucp_14_7_ac_q

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to create this ``rectangle``.

      .. tb-code:: cpp
         :name: c192_mucp_14_7_ac_a
         :caption: Example c192_mucp_14_7_ac_a

         #include <iostream>

         class point {
             private:
                 double m_x, m_y;
             public:
                 point () { m_x = 0; m_y = 0; }
                 point (double x_val, double y_val) { m_x = x_val; m_y = y_val; }
                 double x () { return m_x; }
                 double y () { return m_y; }
                 void x (double x_val) { m_x = x_val; }
                 void y (double y_val) { m_y = y_val; }
         };

         class rectangle {
             private:
                 point m_upper_left, m_lower_right;
             public:
                 double m_length, m_height;
                 rectangle (point up_left, point low_right) { m_upper_left = up_left; m_lower_right = low_right; }
                 point upper_left () { return m_upper_left; }
                 point lower_right () { return m_lower_right; }
                 void upper_left (point p) { m_upper_left = p; }
                 void lower_right (point p) { m_lower_right = p; }
         public:
             void calculate_sides();
             double calculate_area();
         };

         void rectangle::calculate_sides () {
             m_length = lower_right().x() - upper_left().x();
             m_height = upper_left().y() - lower_right().y();
         }

         double rectangle::calculate_area () {
             return m_length * m_height;
         }

         int main() {
             point p1(2.5, 7.5);
             point p2(8, 1.5);
             rectangle r(p1, p2);
             r.calculate_sides();
             std::cout << "length: " << r.m_length << ", Height: " << r.m_height << '\n';
             std::cout << "Area: " << r.calculate_area() << '\n';
             point p3(4.2, 10.7);
             r.upper_left(p3);
             r.calculate_sides();
             std::cout << "New area: " << r.calculate_area() << '\n';
         }
.. tb-group::
   :name: c192_mucp_14_8_ac

   .. tb-tab:: Question

       Let's write the ``date`` class. ``date`` stores information
       about the day, month, and year in private variables, in addition to a ``vector``
       of the number of days in each month. Write accessor functions
       for each variable, keeping in mind the valid values each variable can take.
       in addition, write the default constructor, which initializes
       the date to January 1, 2000. Write another constructor which takes in a day,
       month, and year in that order.

      .. tb-code:: cpp
         :name: c192_mucp_14_8_ac_q
         :caption: Example c192_mucp_14_8_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``date`` class and addtional constructors.

      .. tb-code:: cpp
         :name: c192_mucp_14_8_ac_a
         :caption: Example c192_mucp_14_8_ac_a

         #include <iostream>
         #include <vector>

         class date {
             private:
                 int m_day, m_month, m_year;
                 std::vector<int> days_in_month = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
             public:
                 date () { m_day = 1; m_month = 1; m_year = 2000; }
                 date (int d, int m, int m_y) { m_day = d; m_month = m; m_year = m_y; }
                 int day () { return m_day; }
                 int month () { return m_month; }
                 int year () { return m_year; }
                 void day (int d) { if (d > 0 && d < 32) m_day = d; }
                 void month (int m) { if (m > 0 && m < 13) m_month = m; }
                 void year (int m_y) { m_year = m_y; }
         };
.. tb-group::
   :name: c192_mucp_14_9_ac

   .. tb-tab:: Question

       Let's write the ``date`` member function, ``print_date``,
       which prints the date out in the following format: month/day/year CE/BCE
       depending on whether the year is negative or not.

      .. tb-code:: cpp
         :name: c192_mucp_14_9_ac_q
         :caption: Example c192_mucp_14_9_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``print_date`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_14_9_ac_a
         :caption: Example c192_mucp_14_9_ac_a

         #include <iostream>
         #include <vector>

         class date {
             private:
                 int m_day, m_month, m_year;
                 std::vector<int> days_in_month = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
             public:
                 date () { m_day = 1; m_month = 1; m_year = 2000; }
                 date (int d, int m, int m_y) { m_day = d; m_month = m; m_year = m_y; }
                 int day () { return m_day; }
                 int month () { return m_month; }
                 int year () { return m_year; }
                 void day (int d) { if (d > 0 && d < 32) m_day = d; }
                 void month (int m) { if (m > 0 && m < 13) m_month = m; }
                 void year (int m_y) { m_year = m_y; }
         public:
             void print_date();
         };

         void date::print_date () {
             if (year() < 0) {
                 std::cout << month() << '/' << day() << '/' << -year() << " BCE" << '\n';
             }
             else {
                 std::cout << month() << '/' << day() << '/' << year() << " CE" << '\n';
             }
         }
.. tb-group::
   :name: c192_mucp_14_10_ac

   .. tb-tab:: Question

       Write the ``date`` member function ``is_leap_year``, which returns true if
       the year is a leap year. Then write the ``date`` member function ``last_day_in_month``,
       which returns the last day in the ``date``'s month.

      .. tb-code:: cpp
         :name: c192_mucp_14_10_ac_q
         :caption: Example c192_mucp_14_10_ac_q

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is onne way to write the ``is_leap_year`` and ``last_day_in_month`` member functions.

      .. tb-code:: cpp
         :name: c192_mucp_14_10_ac_a
         :caption: Example c192_mucp_14_10_ac_a

         #include <iostream>
         #include <vector>

         class date {
             private:
                 int m_day, m_month, m_year;
                 std::vector<int> days_in_month = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
             public:
                 date () { m_day = 1; m_month = 1; m_year = 2000; }
                 date (int d, int m, int m_y) { m_day = d; m_month = m; m_year = m_y; }
                 int day () { return m_day; }
                 int month () { return m_month; }
                 int year () { return m_year; }
                 void day (int d) { if (d > 0 && d < 32) m_day = d; }
                 void month (int m) { if (m > 0 && m < 13) m_month = m; }
                 void year (int m_y) { m_year = m_y; }
         public:
             bool is_leap_year();
             int last_day_in_month();
         };

         bool date::is_leap_year () {
             if (year() % 4 != 0) { return false; }
             else if (year() % 100 != 0) { return true; }
             else if (year() % 400 != 0) { return false; }
             else { return true; }
         }

         int date::last_day_in_month () {
             if (is_leap_year() && month() == 2) {
                 return days_in_month[month() - 1] + 1;
             } else {
                 return days_in_month[month() - 1];
             }
         }
