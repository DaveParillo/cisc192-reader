Unique values with std::set
===========================

``std::set`` is declared in ``<set>``. It stores unique keys in sorted order.
For strings, the default order is lexicographical. This is not insertion order,
and elements are not numbered: a set does not have an indexing operator.

.. tb-code:: cpp
   :name: c192_15_7
   :caption: Example c192_15_7
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <iostream>
   #include <set>
   #include <string>

   int main() {
       std::set<std::string> cities{"San Diego", "Boston", "San Diego"};
       auto result = cities.insert("Chicago");
       std::cout << std::boolalpha << result.second << '\n';
       std::cout << cities.contains("Boston") << '\n';
       for (const auto& city_name : cities) {
           std::cout << city_name << '\n';
       }
   }

``insert`` returns a pair. Its ``first`` member is an iterator referring to the
stored key; ``second`` is true only if a new key was inserted. Trying to insert
an existing key leaves the set unchanged. ``contains`` is a C++20 member that
answers a membership question without changing the container.

``find(key)`` returns an iterator, not a numeric index. Compare it with
``end()`` before dereferencing it. Set keys cannot be changed through their
iterators: changing a key could break the ordering. Erase the old key and
insert a new one instead. ``erase(key)`` returns the number of keys removed,
which is either zero or one here.

.. tb-code:: cpp
   :name: c192_set_find
   :caption: Example c192_set_find
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <iostream>
   #include <set>
   #include <string>

   int main() {
       std::set<std::string> cities{"Boston", "Chicago"};
       auto position = cities.find("Chicago");
       if (position != cities.end()) {
           std::cout << *position << '\n';
       }
       cities.erase("Boston");
       std::cout << cities.size() << '\n';
   }

Use a vector when positions or repeated values matter. Use a set when the
important operations are membership, insertion, and removal of unique keys.
Lookup, insertion, and removal by key take logarithmic time in a ``std::set``.
An ``std::unordered_set`` is another option when sorted iteration is not needed;
it uses hashing and has different ordering and performance guarantees.

.. tb-choice::
   :name: c192_set_membership


   - [ ] cities[0]

     A set has no numeric indexing operator.
   - [x] cities.contains("Boston")

     contains tests membership without inserting a key.
   - [ ] cities.find("Boston") == 0

     find returns an iterator, not an index.

