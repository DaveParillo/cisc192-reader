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

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: return_main_1
         :answer_a: string
         :answer_b: integer
         :answer_c: nothing
         :answer_d: anything
         :correct: b
         :feedback_a: Look at the function definition for main.
         :feedback_b: Correct!  You should always return an integer to avoid issues down the road.
         :feedback_c: Main is supposed to return something!
         :feedback_d: Main has a return type, check its function definition.

         What data type is the main function supposed to return?


   .. tab:: Q2

      .. fillintheblank:: return_main_2

          Usually, we return |blank| to exit main.  However, if there are
          any errors that we catch, we might return |blank|.

          - :[0]: Correct!
            :x: Try again!
          - :-1: Correct!
            :.*: Try again!

   .. tab:: Q3

      .. mchoice:: return_main_3
         :multiple_answers:
         :answer_a: "its night time Day time"
         :answer_b: "its night time afternoon"
         :answer_c: nothing is printed
         :answer_d: "its night time" 
         :correct: d
         :feedback_a: a return statment if encountered before reaching the second ``if``.
         :feedback_b: a return statment is encountered before and ``sun_set`` is false.
         :feedback_c: ``sun_set`` is true so the "its night time" gets printed
         :feedback_d: Correct! Once the ``return`` statement is encountered nothing else is printed

         what gets printed?

         ::

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
            

-----

.. admonition:: More to Explore

   - From cppreference.com

     - :lang:`Main function <main_function>`
