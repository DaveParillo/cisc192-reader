A distance table with maps and sets
===================================

We can represent known routes with ``std::map<std::string, std::map<std::string, int>>``.
The outer map associates a city with its neighbors; each inner map associates
a neighbor with a distance. A separate set keeps city names sorted for display.

For this example we assume distances are symmetric. Adding a route stores both
directions. A later record for the same pair replaces both values. A route
from a city to itself must have distance zero. Missing routes remain absent;
we print a dash instead of inventing a distance or searching for an indirect route.

.. tb-file::
   :name: c192_routes-txt
   :filename: c192_routes.txt

   "San Diego" "Los Angeles" 120
   "Los Angeles" "San Francisco" 380
   "Boston" "Chicago" 980

.. tb-code:: cpp
   :name: c192_distance_table
   :caption: Example c192_distance_table
   :compileargs: ['-Wall', '-Wextra', '-std=c++20']
   :files: c192_routes.txt

   #include <fstream>
   #include <iomanip>
   #include <iostream>
   #include <map>
   #include <set>
   #include <sstream>
   #include <string>
   using std::cout;

   struct route_record {
       std::string origin;
       std::string destination;
       int distance = 0;
   };

   bool parse_record(const std::string& line, route_record& record) {
       std::istringstream input(line);
       route_record parsed;
       input >> std::ws;
       if (input.peek() != '"' || !(input >> std::quoted(parsed.origin))) {
           return false;
       }
       input >> std::ws;
       if (input.peek() != '"' || !(input >> std::quoted(parsed.destination))) {
           return false;
       }
       if (!(input >> parsed.distance) || parsed.distance < 0 ||
           parsed.origin.empty() || parsed.destination.empty()) {
           return false;
       }
       input >> std::ws;
       if (!input.eof()) {
           return false;
       }
       record = parsed;
       return true;
   }


   using distance_table = std::map<std::string, std::map<std::string, int>>;

   void add_route(distance_table& routes, const route_record& record) {
       routes[record.origin][record.destination] = record.distance;
       routes[record.destination][record.origin] = record.distance;
       routes[record.origin][record.origin] = 0;
       routes[record.destination][record.destination] = 0;
   }

   int main() {
       std::ifstream input("c192_routes.txt");
       if (!input) {
           std::cerr << "Unable to open routes\n";
           return 1;
       }
       distance_table routes;
       std::set<std::string> cities;
       std::string line;
       while (std::getline(input, line)) {
           route_record record;
           if (!parse_record(line, record) ||
               (record.origin == record.destination && record.distance != 0)) {
               std::cerr << "Invalid route: " << line << '\n';
               return 1;
           }
           add_route(routes, record);
           cities.insert(record.origin);
           cities.insert(record.destination);
       }
       if (input.bad() || !input.eof()) {
           std::cerr << "Read failed\n";
           return 1;
       }
       cout << std::setw(16) << "";
       for (const auto& city : cities) {
           cout << std::setw(16) << city;
       }
       cout << '\n';
       for (const auto& origin : cities) {
           cout << std::setw(16) << origin;
           const auto& neighbors = routes.at(origin);
           for (const auto& destination : cities) {
               auto position = neighbors.find(destination);
               if (position == neighbors.end()) {
                   cout << std::setw(16) << "-";
               } else {
                   cout << std::setw(16) << position->second;
               }
           }
           cout << '\n';
       }
   }

The display uses ``find`` and ``at``, so printing does not insert missing routes.
An empty input file produces an empty table without an invalid array access.
Storage grows with the records we actually insert; there is no guessed limit
of fifty cities and no custom resizing implementation.

For a dense numerical table with known dimensions, nested arrays or vectors
may be more appropriate. Container choice follows the operations and meaning
of the data, not the appearance of the printed table.

