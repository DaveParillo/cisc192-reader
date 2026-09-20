Returning from main
-------------------

Now that we have functions that return values, I can let you in on a
secret. main should have a return statement too. It’s supposed
to return an integer:

::

    int main () {
      return 0;
    }

The usual return value from main is 0, which indicates that the program
succeeded at whatever it was supposed to do. If something goes wrong, it
is common to return -1, or some other value that indicates what kind of
error occurred.

The main function is special in a few ways.
One of them is that it is the only function where the compiler will add
``return 0;`` if main does not already have a return statement.

Of course, you might wonder who this value gets returned to, since we
never call main ourselves. It turns out that when the system executes a
program, it starts by calling main in pretty much the same way it calls
all the other functions.

There are even some parameters that are passed to main by the system,
but we are not going to deal with them for a little while.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: return_main_1




         - [ ] string

           Look at the function definition for main.
         - [x] integer

           Correct!  You should always return an integer to avoid issues down the road.
         - [ ] nothing

           Main is supposed to return something!
         - [ ] anything

           Main has a return type, check its function definition.

   .. tb-tab:: Q2

      .. tb-blank::
         :name: return_main_2

         Usually, we return {{blank:blank1}} to exit main.  However, if there are
         any errors that we catch, we might return {{blank:blank2}}.

         .. tb-answer:: blank1
            :match: [0]
            :feedback: Correct!

         .. tb-answer:: blank2
            :hint: x; Try again!

         .. tb-answer:: blank3
            :match: -1
            :incorrect: Try again!

   .. tb-tab:: Q3

      .. tb-choice::
         :name: return_main_3

         t gets printed?



         int main(){
           bool sun_set=true;
           if(sun_sunset){
             cout << "its night time ";
             sun_set=false;
             return 0;
           }
           if(!sunset){
             cout << "Day time ";
           }
           else{
             cout << "afternoon ";
           }
         }


         - [ ] "its night time Day time"

           a return statment if encountered before reaching the second ``if``.
         - [ ] "its night time afternoon"

           a return statment is encountered before and ``sun_set`` is false.
         - [ ] nothing is printed

           ``sun_set`` is true so the "its night time" gets printed
         - [x] "its night time"

           Correct! Once the ``return`` statement is encountered nothing else is printed

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Main function <main_function>`

