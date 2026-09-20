Coding Practice
---------------


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-group::
         :name: cp_8_1

         .. tb-tab:: Question

            Write the function ``rectangle_info`` which prompts the user for the width
            and height of a rectangle. Then ``rectangle_info`` prints out the area and 
            perimeter of the rectangle.

            .. tb-code:: cpp
               :name: cp_8_AC_1q
               :caption: Example cp_8_AC_1q
               :compileargs: ['-Wall', '-std=c++11']
               :stdin: 4, 6

               #include <iostream>
               using namespace std;

               void rectangle_info () {
                   // Write your implementation here.
               }

               int main() {
                   rectangle_info ();
               }


         .. tb-tab:: Answer

            Below is one way to implement the program. We prompt the user for input
            using ``cin`` before printing the area and perimeter.

            .. tb-code:: cpp
               :name: cp_8_AC_1a
               :caption: Example cp_8_AC_1a
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>

               void rectangle_info () {
                   int height, width;
                   std::cout << "Please enter the height and width of a rectangle separated by spaces: ";
                   std::cin >> height >> width;
                   std::cout << "The area of the rectangle is " << height * width << '\n';
                   std::cout << "The perimeter of the rectangle is " << 2 * (height + width) << '\n';
               }

               int main() {
                   rectangle_info ();
               }

   .. tb-tab:: Q2

      Write a simple function called ``greet_user`` which prompts the user 
      for their full name. Then the function outputs "Hello ``full_name``!".

      .. tb-code:: cpp
         :name: cp_8_AC_2q
         :caption: Example cp_8_AC_2q
         :compileargs: ['-Wall', '-std=c++11']
         :stdin: Captain America

         #include <iostream>

         void greet_user () {
             // Write your implementation here.
         }

         int main() {
             greet_user ();
         }

   .. tb-tab:: Q3

      .. tb-group::
         :name: cp_8_3

         .. tb-tab:: Question

            In the not so distant future, robots have replaced humans to do any kind of imaginable
            work or chore. Define the ``robot`` structure, which has instance variables ``string name``,
            ``string model``, ``int serial_number``, ``int battery_level_percentage``,
            and ``string task`` in that order. Then write the ``print_robot_data`` function, which
            takes a ``robot`` as a parameter and prints out the robot's data in the following format: 
            ``name`` (``model`` ``serial_number``) has ``battery_level_percentage`` 
            percent battery and is currently executing the task "``task``".

            .. tb-code:: cpp
               :name: cp_8_AC_3q
               :caption: Example cp_8_AC_3q
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>

               // Write your code for the struct robot here.

               // Write your code for the function print_robot_data here.

               int main() {
                   robot rob = { "Rob", "XLV", 9800, 45, "washing dishes" };
                   std::cout << "Your output:\n";
                   print_robot_data (rob); 
                   std::cout << "Correct output:\n";
                   std::cout << "Rob (XLV 9800) has 45 percent battery and is currently executing the task \"washing dishes\"";
               }


         .. tb-tab:: Answer

            Below is one way to implement the program. First we declare the instance variables
            in the ``struct`` definition. Next, we use dot notation to access
            the instance variables and output them using ``cout``.

            .. tb-code:: cpp
               :name: cp_8_AC_3a
               :caption: Example cp_8_AC_3a
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>
               using namespace std;

               struct robot {
                   string name;
                   string model;
                   int serial_number;
                   int battery_level_percentage;
                   string task;
               };

               void print_robot_data (robot r) {
                    cout << r.name << " (" << r.model << ' ' << r.serial_number 
                         << ") has " << r.battery_level_percentage 
                         << " percent battery and is currently executing the task \"" 
                         << r.task << '"' << '\n';
               }

               int main() {
                   robot rob = { "Rob", "XLV", 9800, 45, "washing dishes" };
                   cout << "Your output:" << '\n';
                   print_robot_data (rob); 
                   cout << "Correct output:" << '\n';
                   cout << "Rob (XLV 9800) has 45 percent battery and is currently executing the task \"washing dishes\"";
               }

   .. tb-tab:: Q4

      Robots will naturally deplete their charge as they carry out tasks.
      Write a function called ``charge_robot`` which takes a ``robot`` as 
      a parameter and charges the robot to 100 percent. Then output the statement
      "robot ``name`` is fully charged!". 

      .. tb-code:: cpp
         :name: cp_8_AC_4q-support
         :hidden:
         :compileargs: ['-Wall', '-std=c++11']

         void print_robot_data (robot r) {
             cout << r.name << " (" << r.model << ' ' << r.serial_number 
                     << ") has " << r.battery_level_percentage 
                     << " percent battery and is currently executing the task \"" 
                     << r.task << '"' << '\n';
         }


      .. tb-code:: cpp
         :name: cp_8_AC_4q
         :caption: Example cp_8_AC_4q
         :run-after: cp_8_AC_4q-support
         :compileargs: ['-Wall', '-std=c++11']

         #include <iostream>
         using namespace std;

         struct robot {
             string name;
             string model;
             int serial_number;
             int battery_level_percentage;
             string task;
         };

         void print_robot_data (robot r);

         // Write your code for the function charge_robot here.

         int main() {
             robot bob = { "Bob", "MKZ", 143, 65, "sweeping floors" };
             charge_robot (bob);
             cout << "Your output:" << '\n';
             print_robot_data (bob); 
             cout << "Correct output:" << '\n';
             cout << "Bob (MKZ 143) has 100 percent battery and is currently executing the task \"sweeping floors\"";
         }

   .. tb-tab:: Q5

      .. tb-group::
         :name: cp_8_5

         .. tb-tab:: Question

            In case a robot malfunctions, let's write the function ``reset_robot``. ``reset_robot`` 
            takes a ``robot`` as a parameter and resets its name to "EnterAName",
            recharges the battery to 100 percent, and resets the task to "Idle".

            .. tb-code:: cpp
               :name: cp_8_AC_5q-support
               :hidden:
               :compileargs: ['-Wall', '-std=c++11']

               void print_robot_data (robot r) {
                    cout << r.name << " (" << r.model << ' ' << r.serial_number 
                         << ") has " << r.battery_level_percentage 
                         << " percent battery and is currently executing the task \"" 
                         << r.task << '"' << '\n';
               }



            .. tb-code:: cpp
               :name: cp_8_AC_5q
               :caption: Example cp_8_AC_5q
               :run-after: cp_8_AC_5q-support
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>
               using namespace std;

               struct robot {
                   string name;
                   string model;
                   int serial_number;
                   int battery_level_percentage;
                   string task;
               };

               void print_robot_data (robot r);

               // Write your code for the function reset_robot here.

               int main() {
                   robot a = { "Bot", "RSO", 1985, 32, "gardening" };
                   reset_robot (a);
                   cout << "Your output:" << '\n';
                   print_robot_data (a); 
                   cout << "Correct output:" << '\n';
                   cout << "EnterAName (RSO 1985) has 100 percent battery and is currently executing the task \"Idle\"";
               }

         .. tb-tab:: Answer

            Below is one way to implement the program. We can create another ``robot`` 
            with the settings after being reset. Then we set ``r`` equal to the new
            ``robot`` we created. Notice we use dot notation to ensure that the 
            ``model`` and ``serial_number`` are the same.

            .. tb-code:: cpp
               :name: cp_8_AC_5a-support
               :hidden:
               :compileargs: ['-Wall', '-std=c++11']

               void print_robot_data (robot r) {
                    cout << r.name << " (" << r.model << ' ' << r.serial_number 
                         << ") has " << r.battery_level_percentage 
                         << " percent battery and is currently executing the task \"" 
                         << r.task << '"' << '\n';
               }    


            .. tb-code:: cpp
               :name: cp_8_AC_5a
               :caption: Example cp_8_AC_5a
               :run-after: cp_8_AC_5a-support
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>
               using namespace std;

               struct robot {
                   string name;
                   string model;
                   int serial_number;
                   int battery_level_percentage;
                   string task;
               };

               void print_robot_data (robot r);

               void reset_robot(robot& r) {
                   robot reset = { "EnterAName", r.model, r.serial_number, 100, "Idle" };
                   r = reset;
               }

               int main() {
                   robot a = { "Bot", "RSO", 1985, 32, "gardening" };
                   reset_robot (a);
                   cout << "Your output:" << '\n';
                   print_robot_data (a); 
                   cout << "Correct output:" << '\n';
                   cout << "EnterAName (RSO 1985) has 100 percent battery and is currently executing the task \"Idle\"";
               }

   .. tb-tab:: Q6

      Write the ``pokemon`` structure, which has instance variables ``string poke_name``,
      ``string type``, ``int level``, and ``int health_percentage`` in that order. 
      Next, write the function ``print_poke_info``, which takes a ``pokemon`` as a parameter and outputs the
      pokemon's info in the following format: ``poke_name`` (Lv. ``level``, ``health_percentage``\% HP). 

      .. tb-code:: cpp
         :name: cp_8_AC_6q
         :caption: Example cp_8_AC_6q
         :compileargs: ['-Wall', '-std=c++11']

         #include <iostream>
         using namespace std;

         // Write your code for the struct pokemon here.

         // Write your code for the function print_poke_info here.

         int main() {
             pokemon magikarp = { "Magikarp", "Water", 12, 100 };
             cout << "Your output:" << '\n';
             print_poke_info (magikarp); 
             cout << "Correct output:" << '\n';
             cout << "Magikarp (Lv. 12, 100% HP)";
         }  

   .. tb-tab:: Q7

      .. tb-group::
         :name: cp_8_7

         .. tb-tab:: Question

            Now write the ``trainer`` structure, which has instance variables 
            ``string trainer_name``, ``char gender``, ``int num_badges``, and six ``pokemon`` objects 
            named ``first``, ``second``, etc., in that order. Then, write the function 
            ``print_trainer_info``, which takes a ``trainer`` as a parameter and outputs the
            trainer's info. For example, the code below should print:

            .. code-block:: text

               trainer Red has 8 badges and Red's team consists of 
               Pikachu (Lv. 81, 100% HP)
               Espeon (Lv. 72, 100% HP)
               Snorlax (Lv. 75, 100% HP)
               Venusaur (Lv. 77, 100% HP)
               Charizard (Lv. 77, 100% HP)
               Blastoise (Lv. 77, 100% HP)

            .. tb-code:: cpp
               :name: cp_8_AC_7q-support
               :hidden:
               :compileargs: ['-Wall', '-std=c++11']

               void print_poke_info(pokemon p) {
                   cout << p.poke_name << " (Lv. " << p.level << ", " << p.health_percentage << "% HP)" << '\n';
               }



            .. tb-code:: cpp
               :name: cp_8_AC_7q
               :caption: Example cp_8_AC_7q
               :run-after: cp_8_AC_7q-support
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>
               using namespace std;

               struct pokemon {
                   string poke_name;
                   string type;
                   int level;
                   int health_percentage;
               };

               // Write your code for the struct trainer here.

               void print_poke_info(pokemon p);

               // Write your code for the function print_trainer_info here.

               int main() {
                   pokemon pikachu = { "Pikachu", "Electric", 81, 100 };
                   pokemon espeon = { "Espeon", "Psychic", 72, 100 };
                   pokemon snorlax = { "Snorlax", "Normal", 75, 100 };
                   pokemon venusaur = { "Venusaur", "Grass & Poison", 77, 100 };
                   pokemon charizard = { "Charizard", "Fire & Flying", 77, 100 };
                   pokemon blastoise = { "Blastoise", "Water", 77, 100 };
                   trainer red = { "Red", 'M', 8, pikachu, espeon, snorlax, venusaur, charizard, blastoise };
                   print_trainer_info (red);
               }  

         .. tb-tab:: Answer

            Below is one way to implement the program. First we declare the instance variables
            in the ``struct`` definition. Next, we call ``print_poke_info`` on each ``pokemon``
            in ``trainer`` and output the trainer's info in the correct format.

            .. tb-code:: cpp
               :name: cp_8_AC_7a-support
               :hidden:
               :compileargs: ['-Wall', '-std=c++11']

               void print_poke_info(pokemon p) {
                   cout << p.poke_name << " (Lv. " << p.level << ", " << p.health_percentage << "% HP)" << '\n';
               }


            .. tb-code:: cpp
               :name: cp_8_AC_7a
               :caption: Example cp_8_AC_7a
               :run-after: cp_8_AC_7a-support
               :compileargs: ['-Wall', '-std=c++11']

               #include <iostream>
               using namespace std;

               struct pokemon {
                   string poke_name;
                   string type;
                   int level;
                   int health_percentage;
               };

               struct trainer {
                   string trainer_name;
                   char gender;
                   int num_badges;
                   pokemon first, second, third, fourth, fifth, sixth;
               };

               void print_poke_info(pokemon p);

               void print_trainer_info(trainer t) {
                   cout << "trainer " << t.trainer_name << " has " << t.num_badges
                        << " badges and " << t.trainer_name << "'s team consists of " << '\n';
                   print_poke_info(t.first);
                   print_poke_info(t.second);
                   print_poke_info(t.third);
                   print_poke_info(t.fourth);
                   print_poke_info(t.fifth);
                   print_poke_info(t.sixth);
               }

               int main() {
                   pokemon pikachu = { "Pikachu", "Electric", 81, 100 };
                   pokemon espeon = { "Espeon", "Psychic", 72, 100 };
                   pokemon snorlax = { "Snorlax", "Normal", 75, 100 };
                   pokemon venusaur = { "Venusaur", "Grass & Poison", 77, 100 };
                   pokemon charizard = { "Charizard", "Fire & Flying", 77, 100 };
                   pokemon blastoise = { "Blastoise", "Water", 77, 100 };
                   trainer red = { "Red", 'M', 8, pikachu, espeon, snorlax, venusaur, charizard, blastoise };
                   print_trainer_info (red);
               }  

   .. tb-tab:: Q8

      When pokemon are injured, they can be healed up at the pokemon Center.
      Write the function ``heal_pokemon``, which takes a ``trainer`` as a parameter
      and heals the trainer's pokemon to 100 percent health.

      .. tb-code:: cpp
         :name: cp_8_AC_8q-support
         :hidden:
         :compileargs: ['-Wall', '-std=c++11']

         void print_poke_info(pokemon p) {
             cout << p.poke_name << " (Lv. " << p.level << ", " << p.health_percentage << "% HP)" << '\n';
         }

         void print_trainer_info(trainer t) {
             cout << "trainer " << t.trainer_name << " has " << t.num_badges
                 << " badges and " << t.trainer_name << "'s team consists of " << '\n';
             print_poke_info(t.first);
             print_poke_info(t.second);
             print_poke_info(t.third);
             print_poke_info(t.fourth);
             print_poke_info(t.fifth);
             print_poke_info(t.sixth);
         }


      .. tb-code:: cpp
         :name: cp_8_AC_8q
         :caption: Example cp_8_AC_8q
         :run-after: cp_8_AC_8q-support
         :compileargs: ['-Wall', '-std=c++11']

         #include <iostream>
         using namespace std;

         struct pokemon {
             string poke_name;
             string type;
             int level;
             int health_percentage;
         };

         struct trainer {
             string trainer_name;
             char gender;
             int num_badges;
             pokemon first, second, third, fourth, fifth, sixth;
         };

         void print_poke_info(pokemon p);
         void print_trainer_info(trainer t);

         // Write your code for the function heal_pokemon here.

         int main() {
             pokemon exeggutor = {"Exeggutor", "Grass & Psychic", 58, 78};
             pokemon alakazam = {"Alakazam", "Psychic", 54, 0};
             pokemon arcanine = {"Arcanine", "Fire", 58, 24};
             pokemon rhydon = {"Rhydon", "Ground & Rock", 56, 55};
             pokemon gyarados = {"Gyarados", "Water & Flying", 58, 100};
             pokemon pidgeot = {"Pidgeot", "Normal & Flying", 56, 35};
             trainer blue = {"blue", 'M', 8, exeggutor, alakazam, arcanine, rhydon, gyarados, pidgeot};
             print_trainer_info(blue);
             heal_pokemon(blue);
             print_trainer_info(blue);  // pokemon should now all be healed to 100% health
         }  

   .. tb-tab:: Q9

      .. tb-group::
         :name: cp_8_9

         .. tb-tab:: Question

            Now write the function ``poke_center`` which takes a ``trainer`` as a parameter and 
            prompts the user if they'd like to heal their pokemon. Below are the 
            possible outputs (y, n, or an invalid input). If user inputs 'y', call ``heal_pokemon``
            and output the correct dialogue. If user inputs 'n', don't call ``heal_pokemon``
            and output the correct dialogue. If user inputs an invalid character, output the error message.

            .. code-block:: text

               Welcome to the Pokémon Center. Would you like me to take your Pokémon? (y/n) y
               Okay, I'll take your Pokémon for a few seconds.
               Your Pokémon are now healed. We hope to see you again. 

               or

               Welcome to the Pokémon Center. Would you like me to take your Pokémon? (y/n) n
               We hope to see you again.

               or

               Welcome to the Pokémon Center. Would you like me to take your Pokémon? (y/n) h
               Sorry, not a valid input.

            .. tb-code:: cpp
               :name: cp_8_AC_9q-support
               :hidden:
               :compileargs: ['-Wall', '-std=c++11']
               :stdin: y

               void print_poke_info(pokemon p) {
                   cout << p.poke_name << " (Lv. " << p.level << ", " << p.health_percentage << "% HP)" << '\n';
               }

               void print_trainer_info(trainer t) {
                   cout << "trainer " << t.trainer_name << " has " << t.num_badges
                        << " badges and " << t.trainer_name << "'s team consists of " << '\n';
                   print_poke_info(t.first);
                   print_poke_info(t.second);
                   print_poke_info(t.third);
                   print_poke_info(t.fourth);
                   print_poke_info(t.fifth);
                   print_poke_info(t.sixth);
               }

               void heal_pokemon(trainer& t) { 
                   t.first.health_percentage = 100;
                   t.second.health_percentage = 100;
                   t.third.health_percentage = 100;
                   t.fourth.health_percentage = 100;
                   t.fifth.health_percentage = 100;
                   t.sixth.health_percentage = 100;
               }


            .. tb-code:: cpp
               :name: cp_8_AC_9q
               :caption: Example cp_8_AC_9q
               :run-after: cp_8_AC_9q-support
               :compileargs: ['-Wall', '-std=c++11']
               :stdin: y

               #include <iostream>
               using namespace std;

               struct pokemon {
                   string poke_name;
                   string type;
                   int level;
                   int health_percentage;
               };

               struct trainer {
                   string trainer_name;
                   char gender;
                   int num_badges;
                   pokemon first, second, third, fourth, fifth, sixth;
               };

               void print_poke_info(pokemon p);
               void print_trainer_info(trainer t);
               void heal_pokemon(trainer& t);

               // Write your code for the function poke_center here.

               int main() {
                   pokemon exeggutor = {"Exeggutor", "Grass & Psychic", 58, 78};
                   pokemon alakazam = {"Alakazam", "Psychic", 54, 0};
                   pokemon arcanine = {"Arcanine", "Fire", 58, 24};
                   pokemon rhydon = {"Rhydon", "Ground & Rock", 56, 55};
                   pokemon gyarados = {"Gyarados", "Water & Flying", 58, 100};
                   pokemon pidgeot = {"Pidgeot", "Normal & Flying", 56, 35};
                   trainer blue = {"blue", 'M', 8, exeggutor, alakazam, arcanine, rhydon, gyarados, pidgeot};
                   print_trainer_info(blue);
                   poke_center(blue);
                   print_trainer_info(blue);  // pokemon should now all be healed to 100% health
               }  

         .. tb-tab:: Answer

            Below is one way to implement the program. We use conditionals to perform 
            the correct output and operation depending on the user's input.

            .. tb-code:: cpp
               :name: cp_8_AC_9a-support
               :hidden:
               :compileargs: ['-Wall', '-std=c++11']
               :stdin: y

               void print_poke_info(pokemon p) {
                   cout << p.poke_name << " (Lv. " << p.level << ", " << p.health_percentage << "% HP)" << '\n';
               }

               void print_trainer_info(trainer t) {
                   cout << "trainer " << t.trainer_name << " has " << t.num_badges
                        << " badges and " << t.trainer_name << "'s team consists of " << '\n';
                   print_poke_info(t.first);
                   print_poke_info(t.second);
                   print_poke_info(t.third);
                   print_poke_info(t.fourth);
                   print_poke_info(t.fifth);
                   print_poke_info(t.sixth);
               }

               void heal_pokemon(trainer& t) { 
                   t.first.health_percentage = 100;
                   t.second.health_percentage = 100;
                   t.third.health_percentage = 100;
                   t.fourth.health_percentage = 100;
                   t.fifth.health_percentage = 100;
                   t.sixth.health_percentage = 100;
               }


            .. tb-code:: cpp
               :name: cp_8_AC_9a
               :caption: Example cp_8_AC_9a
               :run-after: cp_8_AC_9a-support
               :compileargs: ['-Wall', '-std=c++11']
               :stdin: y

               #include <iostream>
               using namespace std;

               struct pokemon {
                   string poke_name;
                   string type;
                   int level;
                   int health_percentage;
               };

               struct trainer {
                   string trainer_name;
                   char gender;
                   int num_badges;
                   pokemon first, second, third, fourth, fifth, sixth;
               };

               void print_poke_info(pokemon p);
               void print_trainer_info(trainer t);
               void heal_pokemon(trainer& t);

               void poke_center(trainer& t) {
                   char response;
                   cout << "Welcome to the Pokémon Center. Would you like me to take your Pokémon? (y/n) ";
                   cin >> response;
                   if (response == 'y') {
                       cout << "Okay, I'll take your Pokémon for a few seconds." << '\n';
                       heal_pokemon(t);
                       cout << "Your Pokémon are now healed. We hope to see you again." << '\n';
                   }
                   else if (response == 'n') {
                       cout << "We hope to see you again." << '\n';
                   }
                   else {
                       cout << "Sorry, not a valid input." << '\n';
                   }
               }

               int main() {
                   pokemon exeggutor = {"Exeggutor", "Grass & Psychic", 58, 78};
                   pokemon alakazam = {"Alakazam", "Psychic", 54, 0};
                   pokemon arcanine = {"Arcanine", "Fire", 58, 24};
                   pokemon rhydon = {"Rhydon", "Ground & Rock", 56, 55};
                   pokemon gyarados = {"Gyarados", "Water & Flying", 58, 100};
                   pokemon pidgeot = {"Pidgeot", "Normal & Flying", 56, 35};
                   trainer blue = {"blue", 'M', 8, exeggutor, alakazam, arcanine, rhydon, gyarados, pidgeot};
                   print_trainer_info(blue);
                   poke_center(blue);
                   print_trainer_info(blue);  // pokemon should now all be healed to 100% health
               }  

   .. tb-tab:: Q10

      Ever wanted to know how much you'd weigh on each planet? Write the ``convert_weight``
      function, which takes a ``double earth_weight`` and ``int planet`` as parameters. First, 
      in ``main``, prompt the user to enter their weight in pounds and a number corresponding to
      a planet (Mercury is 1, Venus is 2, etc.). Next, call the ``convert_weight`` function using
      the user's input. Finally, print out their weight on that planet.
      If the user inputs an invalid planet, print out an error message. 
      The weight conversion are as follows (multiply the number by ``earth_weight`` to get the weight on that planet):
      Mercury - 0.38, Venus - 0.91, Earth - 1.00, Mars - 0.38, Jupiter - 2.34, Saturn - 1.06, Uranus - 0.92, and Neptune - 1.19.
      Below are some examples.

      :: 

          Please enter your weight in pounds: 145.6
          Please select a planet: 3
          Your weight on Earth is 145.6 pounds.

          or

          Please enter your weight in pounds: 170
          Please select a planet: 1
          Your weight on Mercury is 64.6 pounds.

          or

          Please enter your weight in pounds: 170
          Please select a planet: 23
          Error, not a valid planet.

      .. tb-code:: cpp
         :name: cp_8_AC_10q
         :caption: Example cp_8_AC_10q
         :compileargs: ['-Wall', '-std=c++11']
         :stdin: 145, 2

         #include <iostream>
         using namespace std;

         // Write your code for the function convert_weight here.

         int main() {
             // Write your implementation here.
         }  

