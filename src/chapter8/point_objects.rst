.. _structures-point-objects:

``point`` objects
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

The result of these assignments is shown in the state diagram in
:numref:`fig_point_object_state`:

.. digraph:: state
   :name: fig_point_object_state
   :caption: Point object instance state diagram
   :alt: point object instance state diagram
   :align: center

   fontname = "Bitstream Vera Sans"
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

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: point_objects_1

         Which of the following would be the correct way to initialize the ``x`` instance variable of the ``point`` object?

         .. code-block:: cpp

            struct point () {
              double x, y;
            };

            int main() {
              point nice;
            }

         - [ ] blank.x = 3.0;

           This declaration would not work for the specific code block below.
         - [ ] point.x = 3.0;

           The specific name of the structure should be used, not its type.
         - [x] nice.x = 3.0;

           Yes, we can access and modify the instance variables using the dot operator.
         - [ ] nice.x( ) = 3.0;

           You are not calling a function therefore brackets for an argument list aren't required.

   .. tb-tab:: Q2

      .. tb-parsons::
         :name: point_objects_2

         Construct a block of code that correctly creates variables of a certain structure's type.

         .. code-block:: cpp

            {{group}}
            struct point {
            {{endgroup}}
            {{group}}
               double x;
            {{endgroup}}
            {{group}}
               double y;
            {{endgroup}}
            {{group}}
            };
            {{endgroup}}
            {{group}}
            int main() {
            {{endgroup}}
            {{group}}
               point blue;
            {{endgroup}}
            {{group}}
               blue.x = 3.0;
            {{endgroup}}
            {{distractor}}
            {{group}}
               point.x = 3.0; #distractor
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}

   .. tb-tab:: Q3

      .. tb-choice::
         :name: point_objects_3

         ``struct`` definitions occur...

         - [ ] outside of any function definition, usually at the beginning of the program

           Read over the other answer choices as well.
         - [ ] after the main function

           The struct cannot be defined after the main function or else it can't be used in the program.
         - [ ] after the include statements

           Read over the other answer choices as well.
         - [x] both a and c

           Yes, structs are usually defined after the include statements and before the main function.

