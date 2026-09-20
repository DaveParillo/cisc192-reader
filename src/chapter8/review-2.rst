.. _structures-mixed-up-code-practice:

Mixed Up Code Practice
----------------------

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: mucp_8_1
         :no-indent:

         Let's write the code for the struct definition of ``song``. 
         The song structure will have the instance variables string title, 
         string artist, string album, and int year in that order. 
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            struct song {
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct song {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct song (  #distractor
            {{endgroup}}
            {{group}}
               string title;
            {{endgroup}}
            {{group}}
               string artist;
            {{endgroup}}
            {{group}}
               string album;
            {{endgroup}}
            {{group}}
               int year;
            {{endgroup}}
            {{distractor}}
            {{group}}
               string year;  #distractor
            {{endgroup}}
            {{group}}
            };
            {{endgroup}}
            {{distractor}}
            {{group}}
            } #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            ) #distractor
            {{endgroup}}

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: mucp_8_2
         :no-indent:

         In main, create a song object called fly which holds
         the data for Frank Sinatra's "Fly Me to the Moon" from his 1964 album "It Might as Well Be Swing".
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               song fly;
            {{endgroup}}
            {{distractor}}
            {{group}}
               song fly;
            {{endgroup}}
            {{group}}
               fly.title = "Fly Me to the Moon";
            {{endgroup}}
            {{group}}
               fly.artist = "Frank Sinatra";
            {{endgroup}}
            {{group}}
               fly.album = "It Might as Well Be Swing";
            {{endgroup}}
            {{group}}
               fly.year = 1964;
            {{endgroup}}
            {{distractor}}
            {{group}}
               fly.year = "1964";  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               title = "Fly Me to the Moon";  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               artist.fly = "Frank Sinatra";  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-parsons::
         :name: mucp_8_3
         :no-indent:

         Let's write the code for the ``print_song`` function. print_song
         takes a song as a parameter and prints out the instance variables
         in the following format: "title" by artist (album, year). Put the necessary blocks of 
         code in the correct order.

         .. code-block:: cpp

            {{group}}
            void print_song (song s) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            struct print_song (song s) {
            {{endgroup}}
            {{group}}
               using std::cout;
            {{endgroup}}
            {{group}}
               cout << '"' << s.title << "\" by " << s.artist;
            {{endgroup}}
            {{group}}
               cout << " (" << s.album << ", " << s.year << ")\n";
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << title << artist << album << year;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << '"' << title << "\" by " << artist;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << """ << s.title << "" by " << s.artist;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << " (" << album << ", " << year << ")\n";  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q4

      .. tb-parsons::
         :name: mucp_8_4

         Let's write the code for the struct definition of ``unicorn``. 
         The unicorn structure will have the instance variables name, 
         age, horn_length, hair_color, and is_sparkly in that order. A unicorn's
         horn length is measured to the nearest tenth of a unit.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            struct unicorn {
            {{endgroup}}
            {{distractor}}
            {{group}}
            Struct Unicorn {  #distractor
            {{endgroup}}
            {{group}}
               string name;
            {{endgroup}}
            {{group}}
               int age;
            {{endgroup}}
            {{group}}
               double horn_length;
            {{endgroup}}
            {{group}}
               string hair_color;
            {{endgroup}}
            {{group}}
               bool is_sparkly;
            {{endgroup}}
            {{distractor}}
            {{group}}
               int horn_length;  #distractor
            {{endgroup}}
            {{group}}
            };
            {{endgroup}}
            {{distractor}}
            {{group}}
            } #distractor
            {{endgroup}}

   .. tb-tab:: Q5

      .. tb-parsons::
         :name: mucp_8_5

         Let's write the code for the ``convert_to_human_age`` function. convert_to_human_age
         takes a unicorn as a parameter and returns the equivalent human age.
         If a unicorn is sparkly, then its equivalent human age is three times its age in unicorn years
         plus the length of its horn. If a unicorn is not sparkly, then its equivalent human age is
         four times its age in unicorn years plus twice the length of its horn.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            int convert_to_human_age (unicorn u) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void convert_to_human_age (unicorn u) {
            {{endgroup}}
            {{group}}
               if (u.is_sparkly) {
            {{endgroup}}
            {{distractor}}
            {{group}}
               if (is_sparkly) {
            {{endgroup}}
            {{group}}
                  return 3 * u.age + u.horn_length;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  return 3 * age + horn_length;
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{group}}
               else {
            {{endgroup}}
            {{group}}
                  return 4 * u.age + 2 * u.horn_length;
            {{endgroup}}
            {{distractor}}
            {{group}}
                  return 4 * age + 2 * horn_length;  #distractor
            {{endgroup}}
            {{group}}
               }
            {{endgroup}}
            {{distractor}}
            {{group}}
               int human_years;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q6

      .. tb-parsons::
         :name: mucp_8_6

         Let's write the code for the ``unicorn_power`` function. unicorn_power
         takes a unicorn as a parameter and 
         sets is_sparkly to true and changes the color to rainbow.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void unicorn_power (unicorn& u) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void &unicorn_power (unicorn u) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            void unicorn_power (unicorn u) {  #distractor
            {{endgroup}}
            {{group}}
               u.is_sparkly = true;
            {{endgroup}}
            {{distractor}}
            {{group}}
               u.is_sparkly == true;
            {{endgroup}}
            {{group}}
               u.color = "rainbow";
            {{endgroup}}
            {{distractor}}
            {{group}}
               u.color = rainbow;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q7

      .. tb-parsons::
         :name: mucp_8_7

         Let's write the code for the struct definitions of address and employee. 
         The address structure will have the instance variables house_number, 
         state (abbreviation), and postal_address in that order. The employee 
         structure will be a nested structure with the instance variables name 
         and address address in that order. 
         Put the necessary blocks of code in the correct order, with address defined before employee.

         .. code-block:: cpp

            {{group}}
            struct address {
            {{endgroup}}
            {{distractor}}
            {{group}}
            Struct address {  #distractor
            {{endgroup}}
            {{group}}
               int house_number;
            {{endgroup}}
            {{group}}
               string state;
            {{endgroup}}
            {{group}}
               int postal_address;
            {{endgroup}}
            {{distractor}}
            {{group}}
               employee employee;  #distractor
            {{endgroup}}
            {{group}}
            };
            {{endgroup}}
            {{group}}
            struct employee {
            {{endgroup}}
            {{distractor}}
            {{group}}
            Struct employee {  #distractor
            {{endgroup}}
            {{group}}
               string name;
            {{endgroup}}
            {{group}}
               address address;
            {{endgroup}}
            {{group}}
            };
            {{endgroup}}
            {{distractor}}
            {{group}}
               string address;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               address;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            }  #distractor
            {{endgroup}}

   .. tb-tab:: Q8

      .. tb-parsons::
         :name: mucp_8_8

         Let's write the code for the print_address function. print_address takes
         an employee as a parameter and should print out the information of the employee in the 
         following format: name (id) lives at house_number in state, postal_address.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void print_address (employee e) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            string print_address (employee& e) {
            {{endgroup}}
            {{group}}
               cout << e.name << " (" << e.id << ") lives at ";
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << e.address.name << " (" << e.address.id << ") lives at ";  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << e.name << '(' << e.address.id << ") lives at";  #distractor
            {{endgroup}}
            {{group}}
               cout << e.address.house_number << " in " << e.address.state << ", " << e.address.postal_address << '\n';
            {{endgroup}}
            {{distractor}}
            {{group}}
               cout << e.house_number << " in " << e.state << ", " << e.postal_address << '\n';  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q9

      .. tb-parsons::
         :name: mucp_8_9

         Sometimes employees will move around and thus we'll need to update their addresses.
         Let's write the code for the update_address function. update_address takes an
         employee and a new address as parameters and sets the employee's address to the new address.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            void update_address (employee& e, address a) {
            {{endgroup}}
            {{distractor}}
            {{group}}
            void update_address (employee e, address& a) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            void update_address (employee e, address a) {  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
            employee update_address (employee e, address a) {  #distractor
            {{endgroup}}
            {{group}}
               e.address = a;
            {{endgroup}}
            {{distractor}}
            {{group}}
               e.address = address;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               e.address.house_number = a.house_number;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               e.address.state = a.state;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               e.address.house_number = a.house_number;  #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
               e.address.postal_address = a.postal_address;  #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}
            {{distractor}}
            {{group}}
            };  #distractor
            {{endgroup}}

   .. tb-tab:: Q10

      .. tb-parsons::
         :name: mucp_8_10

         Let's write the code for the store_employee_data function. store_employee_data doesn't
         take any parameters and prompts the user for information regarding their
         name, id, salary, and address in that order. It then returns an employee object with
         the stored data. Declare all variables before prompting the user.
         Put the necessary blocks of code in the correct order.

         .. code-block:: cpp

            {{group}}
            employee store_employee_data () {
            {{endgroup}}
            {{group}}
            employee store_employee_data (employee e) {
            {{endgroup}}
            {{group}}
            void store_employee_data () {
            {{endgroup}}
            {{group}}
               employee e;
            {{endgroup}}
            {{group}}
               cout << "What is your full name? ";
            {{endgroup}}
            {{group}}
               getline(cin, e.name);
            {{endgroup}}
            {{distractor}}
            {{group}}
               cin >> e.name;
            {{endgroup}}
            {{group}}
               cout << "What is your house number? ";
            {{endgroup}}
            {{group}}
               cin >> e.address.house_number;
            {{endgroup}}
            {{distractor}}
            {{group}}
               cin >> e.house_number;
            {{endgroup}}
            {{group}}
               cout << "What state do you live in? ";
            {{endgroup}}
            {{group}}
               cin >> e.address.state;
            {{endgroup}}
            {{distractor}}
            {{group}}
               cin >> address.state;
            {{endgroup}}
            {{group}}
               cout << "What is your postal address? ";
            {{endgroup}}
            {{group}}
               cin >> e.address.postal_address;
            {{endgroup}}
            {{group}}
               return e;
            {{endgroup}}
            {{distractor}}
            {{group}}
               return employee e;
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

