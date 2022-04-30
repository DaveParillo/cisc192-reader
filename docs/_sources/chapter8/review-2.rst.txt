Mixed Up Code Practice
----------------------

.. tabbed:: self_check

   .. tab:: Q1

      .. parsonsprob:: mucp_8_1
         :numbered: left
         :adaptive:
         :noindent:
         :practice: T

         Let's write the code for the struct definition of ``song``. 
         The song structure will have the instance variables string title, 
         string artist, string album, and int year in that order. 
         Put the necessary blocks of code in the correct order.
         -----
         struct song {
         =====
         struct Song {  #distractor
         =====
         struct song (  #distractor
         =====
            string title;
         =====
            string artist;
         =====
            string album;
         =====
            int year;
         =====
            string year;  #distractor
         =====
         };
         =====
         } #distractor
         =====
         ) #distractor

   .. tab:: Q2

      .. parsonsprob:: mucp_8_2
         :numbered: left
         :adaptive:
         :noindent:

         In main, create a song object called fly which holds
         the data for Frank Sinatra's "Fly Me to the Moon" from his 1964 album "It Might as Well Be Swing".
         Put the necessary blocks of code in the correct order.
         -----
         int main() {
         =====
            Song fly;
         =====
            song fly;  #paired
         =====
            fly.title = "Fly Me to the Moon";
         =====
            fly.artist = "Frank Sinatra";
         =====
            fly.album = "It Might as Well Be Swing";
         =====
            fly.year = 1964;
         =====
            fly.year = "1964";  #distractor
         =====
            title = "Fly Me to the Moon";  #distractor
         =====
            artist.fly = "Frank Sinatra";  #distractor
         =====
         }

   .. tab:: Q3

      .. parsonsprob:: mucp_8_3
         :numbered: left
         :adaptive:
         :noindent:

         Let's write the code for the ``print_song`` function. print_song
         takes a song as a parameter and prints out the instance variables
         in the following format: "title" by artist (album, year). Put the necessary blocks of 
         code in the correct order.
         -----
         void print_song (Song s) {
         =====
         struct print_song (Song s) {  #paired
         =====
            using std::cout;
         =====
            cout << "\"" << s.title << "\" by " << s.artist;
         =====
            cout << " (" << s.album << ", " << s.year << ")\n";
         =====
            cout << title << artist << album << year;  #distractor
         =====
            cout << "\"" << title << "\" by " << artist;  #distractor
         =====
            cout << """ << s.title << "" by " << s.artist;  #distractor
         =====
            cout << " (" << album << ", " << year << ")\n";  #distractor
         =====
         }

   .. tab:: Q4

      .. parsonsprob:: mucp_8_4
         :numbered: left
         :adaptive:
         :practice: T

         Let's write the code for the struct definition of ``unicorn``. 
         The unicorn structure will have the instance variables name, 
         age, hornLength, hairColor, and isSparkly in that order. A unicorn's
         horn length is measured to the nearest tenth of a unit.
         Put the necessary blocks of code in the correct order.
         -----
         struct unicorn {
         =====
         Struct Unicorn {  #distractor
         =====
            string name;
         =====
            int age;
         =====
            double horn_length;
         =====
            string hair_color;
         =====
            bool is_sparkly;
         =====
            int horn_length;  #distractor
         =====
         };
         =====
         } #distractor

   .. tab:: Q5

      .. parsonsprob:: mucp_8_5
         :numbered: left
         :adaptive:

         Let's write the code for the ``convert_to_human_age`` function. convert_to_human_age
         takes a unicorn as a parameter and returns the equivalent human age.
         If a unicorn is sparkly, then its equivalent human age is three times its age in unicorn years
         plus the length of its horn. If a unicorn is not sparkly, then its equivalent human age is
         four times its age in unicorn years plus twice the length of its horn.
         Put the necessary blocks of code in the correct order.
         -----
         int convert_to_human_age (unicorn u) {
         =====
         void convert_to_human_age (unicorn u) {  #paired
         =====
            if (u.is_sparkly) {
         =====
            if (is_sparkly) {  #paired
         =====
               return 3 * u.age + u.horn_length;
         =====
               return 3 * age + horn_length;  #paired
         =====
            }
         =====
            else {
         =====
               return 4 * u.age + 2 * u.horn_length;
         =====
               return 4 * age + 2 * horn_length;  #distractor
         =====
            }
         =====
            int human_years;  #distractor
         =====
         }

   .. tab:: Q6

      .. parsonsprob:: mucp_8_6
         :numbered: left
         :adaptive:

         Let's write the code for the ``unicorn_power`` function. unicorn_power
         takes a unicorn as a parameter and 
         sets isSparkly to true and changes the color to rainbow.
         Put the necessary blocks of code in the correct order.
         -----
         void unicorn_power (unicorn& u) {
         =====
         void &unicorn_power (unicorn u) {  #distractor
         =====
         void unicorn_power (unicorn u) {  #distractor
         =====
            u.is_sparkly = true;
         =====
            u.is_sparkly == true;  #paired
         =====
            u.color = "rainbow";
         =====
            u.color = rainbow;  #paired
         =====
         }

   .. tab:: Q7

      .. parsonsprob:: mucp_8_7
         :numbered: left
         :adaptive:
         :practice: T

         Let's write the code for the struct definitions of Address and Employee. 
         The Address structure will have the instance variables houseNumber, 
         state (abbreviation), and postalAddress in that order. The Employee 
         structure will be a nested structure with the instance variables name 
         and Address address in that order. 
         Put the necessary blocks of code in the correct order, with Address defined before Employee.
         -----
         struct Address {
         =====
         Struct Address {  #distractor
         =====
            int houseNumber;
         =====
            string state;
         =====
            int postalAddress;
         =====
            Employee employee;  #distractor
         =====
         };
         =====
         struct Employee {
         =====
         Struct Employee {  #distractor
         =====
            string name;
         =====
            Address address;
         =====
         };
         =====
            string address;  #distractor
         =====
            Address;  #distractor
         =====
         }  #distractor

   .. tab:: Q8

      .. parsonsprob:: mucp_8_8
         :numbered: left
         :adaptive:

         Let's write the code for the printAddress function. printAddress takes
         an Employee as a parameter and should print out the information of the employee in the 
         following format: name (id) lives at houseNumber in state, postalAddress.
         Put the necessary blocks of code in the correct order.
         -----
         void printAddress (Employee e) {
         =====
         string printAddress (Employee& e) {  #paired 
         =====
            cout << e.name << " (" << e.id << ") lives at ";
         =====
            cout << e.address.name << " (" << e.address.id << ") lives at ";  #distractor
         =====
            cout << e.name << "(" << e.address.id << ") lives at";  #distractor
         =====
            cout << e.address.houseNumber << " in " << e.address.state << ", " << e.address.postalAddress << endl;
         =====
            cout << e.houseNumber << " in " << e.state << ", " << e.postalAddress << endl;  #distractor
         =====
         }

   .. tab:: Q9

      .. parsonsprob:: mucp_8_9
         :numbered: left
         :adaptive:

         Sometimes employees will move around and thus we'll need to update their addresses.
         Let's write the code for the updateAddress function. updateAddress takes an
         Employee and a new Address as parameters and sets the employee's address to the new address.
         Put the necessary blocks of code in the correct order.
         -----
         void updateAddress (Employee& e, Address a) {
         =====
         void updateAddress (Employee e, Address& a) {  #distractor
         =====
         void updateAddress (Employee e, Address a) {  #distractor
         =====
         Employee updateAddress (Employee e, Address a) {  #distractor
         =====
            e.address = a;
         =====
            e.address = address;  #distractor
         =====
            e.address.houseNumber = a.houseNumber;  #distractor
         =====
            e.address.state = a.state;  #distractor
         =====
            e.address.houseNumber = a.houseNumber;  #distractor
         =====
            e.address.postalAddress = a.postalAddress;  #distractor
         =====
         }
         =====
         };  #distractor

   .. tab:: Q10

      .. parsonsprob:: mucp_8_10
         :numbered: left
         :adaptive:

         Let's write the code for the storeEmployeeData function. storeEmployeeData doesn't
         take any parameters and prompts the user for information regarding their
         name, id, salary, and address in that order. It then returns an Employee object with
         the stored data. Declare all variables before prompting the user.
         Put the necessary blocks of code in the correct order.
         -----
         Employee storeEmployeeData () {
         =====
         Employee storeEmployeeData (Employee e) {
         =====
         void storeEmployeeData () {
         =====
            Employee e;
         =====
            cout << "What is your full name? ";
         =====
            getline(cin, e.name);
         =====
            cin >> e.name;  #paired
         =====
            cout << "What is your house number? ";
         =====
            cin >> e.address.houseNumber;
         =====
            cin >> e.houseNumber;  #paired
         =====
            cout << "What state do you live in? ";
         =====
            cin >> e.address.state;
         =====
            cin >> address.state;  #paired
         =====
            cout << "What is your postal address? ";
         =====
            cin >> e.address.postalAddress;
         =====
            return e;
         =====
            return Employee e;  #paired
         =====
         }

