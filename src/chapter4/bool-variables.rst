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


.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-match::
         :name: bool_var_1

         Match the conditional statement to the correct boolean, given x = 2.

         x * 2 > 4
            false
         x >= 2
            true

   .. tb-tab:: Q2

      .. tb-match::
         :name: bool_var_2

         Match the statement to the word that describes it best.

         bool fred;
            variable declaration
         fred = true;
            assignment
         bool test_result = false;
            initialization

   .. tb-tab:: Q3

      .. tb-choice::
         :name: bool_var_3

         What will print?

         ::

             int n = 16;
             int x = 4;

             bool even_flag = (n % 2 == 0);
             bool plus_flag = (x > 0);

             if (even_flag) {
               cout << "n was even when I checked it ";
             }

             if (plus_flag) {
               cout << "x was positive when I checked it";
             }

         - [x] n was even when I checked it x was positive when I checked it

           Great!
         - [ ] x was positive when I checked it n was even when I checked it

           Make sure you follow the correct order of execution.  Also, a space is not automatically added.
         - [ ] x was positive when I checked it

           Take another look at the result from the modulus operator.
         - [ ] n was even when I checked itx was positive when I checked it

           Both flags are made, But A space is after it.
         - [ ] x was positive when I checked itn was even when I checked it

           Make sure you follow the correct order of execution.

   .. tb-tab:: Q4

      .. tb-choice::
         :name: bool_var_4

         What will print?

         .. code-block::

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
                     cout<<"Charging your phone"<<'\n';
                 }
                 else{
                     cout<<"Battery is charged"<<'\n';
                 }

               }
               else{
                 cout<<"There is no power"<<'\n'>>;
               }
             }


         - [ ] nothing will print

           -   The value of ``low_battery`` is true so we enter the first ``if`` block.

         - [x] "Charging your phone"

           +   correct! ``low_battery`` stays true and we set ``power_outage`` to false.

         - [ ] "Battery is charged"

           -   ``low_battery`` is true so we don't reach this ``else``.

         - [ ] "There is no power"

           -   We change the value of ``power_outage`` to false before hand.

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Fundamental types <types>` -- including bool
     - C++ :cpp:`keywords`

