From files to containers
========================

A file stores characters; a program gives those characters meaning. In this
chapter we read and write text files, parse records, and choose a container
that fits the data. The examples use the C++20 standard library.

Our running example records distances between cities. A record contains two
city names and a nonnegative distance. City names can contain spaces, so the
file surrounds each name with double quotes::

   "San Diego" "Los Angeles" 120
   "Los Angeles" "San Francisco" 380

These are illustrative values, not a source for travel planning. We want to
look up a known distance, list the cities without duplicates, and distinguish
an unknown route from a route whose distance is zero.

The standard library provides containers for different jobs:

.. list-table:: Choosing a container
   :header-rows: 1
   :widths: 20 35 45

   * - Container
     - Organization
     - A useful example
   * - ``std::array<T, N>``
     - A fixed number of elements in sequence
     - The four suit names or seven daily readings
   * - ``std::vector<T>``
     - A sequence that can grow
     - Records read from a file of unknown length
   * - ``std::set<T>``
     - Unique keys in sorted order
     - City names without duplicates
   * - ``std::map<Key, Value>``
     - Unique keys with associated values, sorted by key
     - A city's neighbors and their distances

We can combine these containers. A rectangular table can be an array of
arrays when its dimensions are fixed, or a vector of vectors when dimensions
are chosen at run time. A map of maps can represent only the routes we know.
There is no need to implement another container just to store this data.

.. tb-choice::
   :name: c192_question15_1_1



   - [ ] Store zero for every unknown route.

     Zero already means a distance of zero; it should not also mean missing information.
   - [x] Store only known routes and check whether a key is present.

     A missing key lets us distinguish an unknown route from a known distance.

.. tb-choice::
   :name: c192_question15_1_2


   - [ ] std::array

     An array does not enforce uniqueness.
   - [ ] std::vector

     A vector can contain repeated values.
   - [x] std::set

     A set stores each distinct key once.

