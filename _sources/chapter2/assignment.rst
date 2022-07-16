Assignment
----------

.. index::
   single: assignment
   single: assignment statement

Now that we have created some variables, we would like to store values
in them. We do that with an **assignment statement**.

::

    first_letter = 'a';  // give first_letter the value 'a'
    hour = 11;           // assign the value 11 to hour
    minute = 59;         // set minute to 59

This example shows three assignments, and the comments show three
different ways people sometimes talk about assignment statements. The
vocabulary can be confusing here, but the idea is straightforward:

-  When you declare a variable, you create a named storage location.

-  When you make an assignment to a variable, you give it a value.

.. note::

   We could have created these 3 variables llike this:

   ::

      // These storage locations are defined,
      // but there is no value stored yet!

      char first_letter;
      int hour;
      int minute;

      // perhaps we try to read a value from one of our
      // three variables here?
      int next_hour = hour + 1;  // This is an error


      char first_letter = 'a';  // give first_letter the value 'a'
      int hour = 11;            // assign the value 11 to hour
      int minute = 59;          // set minute to 59

   Using unitialized variables is a commonn source of error.
   That's why in C++ it is considered a best practice to
   always initialize a new variable with a value, if possible.

.. index::
   single: state diagram

A common way to represent variables on paper is to draw a box with the
name of the variable on the outside and the value of the variable on the
inside. This kind of figure is called a **state diagram** because is
shows what state each of the variables is in (you can think of it as the
variable’s "state of mind"). This diagram shows the effect of the three
assignment statements:

.. digraph:: state
   :align: center
   :alt: Variable state diagram

   fontname = "Bitstream Vera Sans"
   node [
      fontname = "Bitstream Vera Sans"
      fontsize = 11
      style=filled
      fillcolor=lightblue
   ]
   edge [style=invis, constraint=false]

   label="Variable state diagram";
   labelloc=bottom;
   letter [label="'a'"];
   hour [label="12", shape="box"];
   min [label="59", shape="box"];
   letter -> hour -> min;

   node [
       shape="plain"
       style=none
   ]
   edge [constraint=true]
   t1 [label="first_letter"];
   t2 [label="hour"];
   t3 [label="minute"];
   letter -> t1;
   hour -> t2;
   min -> t3;
   {rank=sink; t1 t2 t3};


I sometimes use different shapes to indicate different variable types.
These shapes should help remind you that one of the rules in C++ is that
a variable has to have the same type as the value you assign it.

.. Warning::
   The variable type that you declare must match the type of the value 
   assigned to it.  A type mismatch will generate a compile error.

For example, you cannot store a string in an ``int`` variable. The following
statement generates a compile error.

::

    int hour;
    hour = "Hello.";       // WRONG !!

This rule is sometimes a source of confusion, because there are many ways
that you can convert values from one type to another, and C++ sometimes
converts things implicitly (automatically).  But for now you should remember
that as a general rule variables and values have the same type, and we’ll
talk about special cases later.

Another source of confusion is that some strings *look* like integers,
but they are not. For example, the string "123", which is made up of the
characters 1, 2 and 3, is not the same thing as the *number* 123. This
assignment is illegal:

::

    int minute = "59";         // WRONG!

.. tabbed:: tab_check

   .. tab:: Q1

      .. fillintheblank:: assignment_1

         A(n) |blank| statement gives a value to a variable.

         - :[Aa][Ss][Ss][Ii][Gg][Nn][Mm][Ee][Nn][Tt]: Correct!
           :.*: Try again!


   .. tab:: Q2

      .. mchoice:: assignment_2
         :practice: T
         :answer_a: Change the type of variable q from int to char.
         :answer_b: Change the type of both variables (p and q) from int to char.
         :answer_c: Change the type of variable p from int to char.
         :answer_d: Nothing needs to change! The code will work just fine!
         :correct: b
         :feedback_a: Yes, but take a look at variable p.
         :feedback_b: Both variables are a character surrounded by single quotes, so they should be type char.
         :feedback_c: Yes, but take a look at variable q.
         :feedback_d: This compiles and runs, but the code is not quite right.

         What must be changed in order for this code block to work?

         ::

             // main: generate some simple output

             int main () {
               int p;
               int q;
               p = 'h';
               q = '9';
             }


   .. tab:: Q3

      .. parsonsprob:: assignment_3
         :numbered: left
         :adaptive:
         
         You love your car, and you decide to keep track of its make, model, and year.  You do so using three assignment statements IN THAT ORDER.  For the sake of this problem, suppose you drive a 2001 Jeep Cherokee.  Hint: there are a couple ways to write an assignment statement.
         -----
         string make;
         make = "Jeep";
         =====
         string make = Jeep; #paired
         =====
         make = "Jeep;" #paired
         =====
         string model = "Cherokee";
         =====
         string model; #paired
         model = Cherokee;
         =====
         string model = Cherokee; #paired
         =====
         int year = 2001;
         =====
         int year; #paired
         2001 = year;
         =====
         int year; #paired
         year = 2001

-----

.. admonition:: More to Explore

   - From cppreference.com

     - C++ :lang:`identifiers` and :lang:`type`
     - :cpp:`std::string <string>`


