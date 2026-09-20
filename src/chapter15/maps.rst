Key-value associations with std::map
====================================

``std::map`` is declared in ``<map>``. Each element associates a unique key
with a value. Keys are sorted by the comparison function; the default order
for strings is lexicographical. A map of names to counts lets us update a
count without searching a vector of records ourselves.

.. tb-code:: cpp
   :name: c192_map_counts
   :caption: Example c192_map_counts
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <cstddef>
   #include <iostream>
   #include <map>
   #include <string>
   #include <vector>

   int main() {
       std::vector<std::string> visits{"Boston", "Chicago", "Boston"};
       std::map<std::string, std::size_t> counts;
       for (const auto& city_name : visits) {
           ++counts[city_name];
       }
       for (const auto& [city_name, count] : counts) {
           std::cout << city_name << ": " << count << '\n';
       }
   }

The structured binding ``[city_name, count]`` names the key and mapped value
of each pair. The reference avoids copying the strings during iteration.

Unlike a vector subscript, a map subscript names a key, not a position.
``counts[key]`` **inserts** a missing key with a value-initialized value (zero
for ``std::size_t``), and returns a reference to that value. That behavior is useful
for counting, but can be a bug in code that only intended to look up a value.

.. tb-code:: cpp
   :name: c192_map_lookup
   :caption: Example c192_map_lookup
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']

   #include <iostream>
   #include <map>
   #include <string>

   int main() {
       std::map<std::string, int> distances{{"Boston", 1100}, {"Chicago", 700}};
       auto position = distances.find("Seattle");
       if (position == distances.end()) {
           std::cout << "unknown distance\n";
       } else {
           std::cout << position->second << '\n';
       }
       std::cout << distances.size() << '\n';
   }

``find`` and ``contains`` do not insert. ``at(key)`` returns an existing mapped
value, or throws ``std::out_of_range`` if the key is absent. A map can also be
read through a const reference using those members; ``operator[]`` is not
available on a const map because it might insert.

``insert_or_assign(key, value)`` explicitly inserts or replaces a mapped value.
``try_emplace(key, value)`` inserts only when the key is absent. ``erase(key)``
removes a key and its value. Lookup, insertion, and removal by key take
logarithmic time. As with sets, an unordered counterpart is available when
hashing rather than sorted iteration fits the task.

.. tb-choice::
   :name: c192_map_lookup_question


   - [ ] distances["Seattle"]

     Subscript inserts a missing key, which can create a misleading zero distance.
   - [x] distances.find("Seattle")

     find reports absence by returning end() and leaves the map unchanged.

