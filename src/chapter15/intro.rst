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
   :name: question15_1_1

   Why aren't we filling in every value in our table, who are we leaving blank space above the diagonal of 0's?

   - [ ] Because we only need the half of the dataset contained by the triangle.

     Incorrect! All of the data above the 0 diagonal is a mirror image of the triangle! So, the triangle contains the whole dataset.
   - [ ] Because triangles are the most effective shape to use when presenting data to others.

     Incorrect! Triangles do look cool, but they aren't necessarily the most effective shape to use when presenting data.
   - [ ] Because matrices are triangles.

     Incorrect! This triangle is PART OF an apmatrix.
   - [x] Because the triangle contains the entire dataset.

     Correct! The triangle contains all data points with no repeat data. If we included all datapoints, the would just be repeats of the points we already have.

.. tb-choice::
   :name: question15_1_2

   Based on how it is used to create the above table, what do you think a ``matrix`` is?

   - [ ] a geometric shape

     Incorrect! A matrix is not a geometric shape, although they ARE rectangles.
   - [x] a two-dimensional vector

     Correct!
   - [ ] a material in which something develops

     Incorrect! This is a definition for matrix, but not in the programming sense.
   - [ ] a mold used to shape things

     Incorrect! This is a definition for matrix, but not in the programming sense.

