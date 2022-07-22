Boolean Variables
-----------------
..	index::
	  single: bool variables

As usual, for every type of value, there is a corresponding type of
variable. In C++ the boolean type is called **bool**. Boolean variables
work just like the other types:

::

    bool fred;
    fred = true;
    bool test_result = false;

The first line is a simple variable declaration; the second line is an
assignment, and the third line is a combination of a declaration and as
assignment, called an initialization.

As I mentioned, the result of a comparison operator is a boolean, so you
can store it in a ``bool`` variable

::

    bool even = (n % 2 == 0);     // true if n is even
    bool plus = (x > 0);          // true if x is positive

and then use it as part of a conditional statement later:

::

    if (even) {
      cout << "n was even when I checked it";
    }

..	index::
	  pair: bool variable; flag

A variable used in this way is called a **flag**, since it flags the
presence or absence of some condition.


.. tabbed:: self_check

   .. tab:: Q1

      .. dragndrop:: bool_var_1
         :feedback: Try again!
         :match_1: x * 2 > 4|||false
         :match_2: x >= 2|||true

         Match the conditional statement to the correct boolean, given x = 2.

   .. tab:: Q2

      .. dragndrop:: bool_var_2
         :feedback: Try again!
         :match_1: bool fred;|||variable declaration
         :match_2: fred = true;|||assignment
         :match_3: bool testResult = false;|||initialization

         Match the statement to the word that describes it best.

   .. tab:: Q3

      .. mchoice:: bool_var_3
         :answer_a: n was even when I checked it x was positive when I checked it
         :answer_b: x was positive when I checked it n was even when I checked it
         :answer_c: x was positive when I checked it
         :answer_d: n was even when I checked itx was positive when I checked it
         :answer_e: x was positive when I checked itn was even when I checked it
         :correct: d
         :feedback_a: A space is not automatically added.
         :feedback_b: Make sure you follow the correct order of execution.  Also, a space is not automatically added.
         :feedback_c: Take another look at the result from the modulus operator.
         :feedback_d: Both flags are made, and no space is added.
         :feedback_e: Make sure you follow the correct order of execution.

         What will print?

         ::

             int n = 16;
             int x = 4;

             bool even = (n % 2 == 0);
             bool plus = (x > 0);

             if (even) {
               cout << "n was even when I checked it ";
             }

             if (plus) {
               cout << "x was positive when I checked it";
             }

   .. tab:: Q4

      .. mchoice:: bool_var_4
         :answer_a: nothing will print
         :answer_b: "Charging your phone"
         :answer_c: "Battery is charged" 
         :answer_d: "There is no power"
         :correct: b
         :feedback_a: The value of ``low_battery`` is true so we enter the first ``if`` block.
         :feedback_b: correct! ``low_battery`` stays true and we set ``power_outage`` to false.
         :feedback_c: ``low_battery`` is true so we don't reach this ``else``.
         :feedback_d: We change the value of ``power_outage`` to false before hand.

         What will print?

         ::

             bool low_battery=true;
             bool power_outage=true;

             if(low_battery){

                if(power_outage){
                    power_outage=!power_outage;
                }
                else{
                    low_battery=false;
                }

                if(!power_outage){
                  
                  if(low_battery){
                      cout<<"Charging your phone\n";
                  }
                  else{
                      cout<<"Battery is charged\n";
                  }

                }
                else{
                  cout<<"There is no power\n";
                }

             }

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Fundamental types <types>` -- including bool
     - C++ :cpp:`keywords`
