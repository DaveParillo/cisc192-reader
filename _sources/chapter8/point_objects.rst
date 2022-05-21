``Point`` objects
-----------------

As a simple example of a compound structure, consider the concept of a
mathematical point. At one level, a point is two numbers (coordinates)
that we treat collectively as a single object. In mathematical notation,
points are often written in parentheses, with a comma separating the
coordinates. For example, :math:`(0, 0)` indicates the origin, and
:math:`(x, y)` indicates the point :math:`x` units to the right and
:math:`y` units up from the origin.

A natural way to represent a point in C++ is with two ``double``\ s. The
question, then, is how to group these two values into a compound object,
or structure. The answer is a ``struct`` definition:

::

   struct point {
     double x;
     double y;
   };

``struct`` definitions appear outside of any function definition,
usually at the beginning of the program (after the ``include``
statements).

.. index::
   pair: variables; instance variables

This definition indicates that there are two elements in this structure,
named ``x`` and ``y``. These elements are called **instance variables**,
for reasons I will explain a little later.

.. warning::
   It is a common error to leave off the semi-colon at the end of a
   structure definition. It might seem odd to put a semi-colon after a
   curly-brace, but you’ll get used to it.

Once you have defined the new structure, you can create variables with
that type:

::

     point blank;
     blank.x = 3.0;
     blank.y = 4.0;

The first line is a conventional variable declaration: ``blank`` has
type ``point``. The next two lines initialize the instance variables of
the structure. The "dot notation" used here is similar to the syntax for
invoking a function on an object, as in ``fruit.size()``. Of course,
one difference is that function names are always followed by an argument
list, even if it is empty.

The dot notation is officially called the *member access operator*
because it is the operator used to access the members of a struct.

The result of these assignments is shown in the following state diagram:

.. digraph:: state
   :align: center
   :alt: point struct state diagram

   fontname = "Bitstream Vera Sans"
   label="blank object instance state diagram";
   labelloc=bottom;
   node [
      shape=record
      fontname = "Bitstream Vera Sans"
      fontsize = 11
      style=filled
      fillcolor=lightblue
   ]

   subgraph cluster_0 {
      label="blank"
      stack [label="x: 3 | y: 4"]
   }

As usual, the name of the variable ``blank`` appears outside the boxes and
its value appears inside the boxes. In this case, that value is a compound
object with two named instance variables.

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: point_objects_1
         :practice: T
         :answer_a: blank.x = 3.0;
         :answer_b: point.x = 3.0;
         :answer_c: nice.x = 3.0;
         :answer_d: nice.x = 3.0
         :correct: c
         :feedback_a: This declaration would not work for the specific code block below.
         :feedback_b: The specific name of the structure should be used, not its type.
         :feedback_c: Yes, we can access and modify the instance variables using the member access operator.
         :feedback_d: The semi-colon is missing at the end.

         Which of the following would be the correct way to initialize the instance variables
         of the ``point`` object?

         .. code-block:: cpp

            struct point () {
              double x;
              double y;
            };

            int main() {
              point nice;
            }

   .. tab:: Q2

      .. parsonsprob:: point_objects_2
         :numbered: left
         :adaptive:

         Construct a block of code that correctly creates variables of a certain structure's type.
         -----
         struct point {

            double x;
            double y;

         };

         int main() {

            point blue;

            blue.x = 3.0;

            point.x = 3.0; #distractor
         }

   .. tab:: Q3

      .. mchoice:: point_objects_3
         :practice: T
         :answer_a: outside of any function definition, usually at the beginning of the program
         :answer_b: after the main function
         :answer_c: after the include statements
         :answer_d: both a and c
         :correct: d
         :feedback_a: Read over the other answer choices as well.
         :feedback_b: The struct cannot be defined after the main function or else it can't be used in the program.
         :feedback_c: Read over the other answer choices as well.
         :feedback_d: Yes, structs are usually defined after the include statements and before the main function.

         When do ``struct`` definitions occur?

