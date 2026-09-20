Rectangles
----------

Now let’s say that we want to create a structure to represent a
rectangle. The question is, what information do I have to provide in
order to specify a rectangle? To keep things simple let’s assume that
the rectangle will be oriented vertically or horizontally, never at an
angle.

There are a few possibilities: I could specify the center of the
rectangle (two coordinates) and its size (width and height), or I could
specify one of the corners and the size, or I could specify two opposing
corners.

The most common choice in existing programs is to specify the upper left
corner of the rectangle and the size. To do that in C++, we will define
a structure that contains a ``point`` and two doubles.

::

   struct rectangle {
     point corner;
     double width, height;
   };

Notice that one structure can contain another. In fact, this sort of
thing is quite common. Of course, this means that in order to create a
``rectangle``, we have to create a ``point`` first:

::

     point corner = { 0.0, 0.0 };
     rectangle box = { corner, 100.0, 200.0 };

This code creates a new ``rectangle`` structure and initializes the
instance variables. The figure shows the effect of this assignment.

.. digraph:: state
   :align: center
   :alt: rectangle struct state diagram

   fontname = "Bitstream Vera Sans"
   label="rectangle object state diagram";
   labelloc=bottom;
   node [
      shape=record
      fontname = "Bitstream Vera Sans"
      fontsize = 11
      style=filled
      fillcolor=lightblue
   ]

   subgraph cluster_0 {
      labelloc=top;
      label="box"
      subgraph cluster_0 {
         label="corner"
         point [label="x: 0 | y: 0"]
      }
      w [label="width:  100"]
      h [label="height: 200"]
   }

   point -> w -> h [style=invis]

We can access the ``width`` and ``height`` in the usual way:

::

     box.width += 50.0;
     cout << box.height;

In order to access the instance variables of ``corner``, we can use a
temporary variable:

::

     point temp = box.corner;
     double x = temp.x;

Alternatively, we can compose the two statements:

::

     double x = box.corner.x;

It makes the most sense to read this statement from right to left:
“Extract ``x`` from the ``corner`` of the ``box``, and assign it to the
local variable ``x``.”

While we are on the subject of composition, I should point out that you
can, in fact, create the ``point`` and the ``rectangle`` at the same
time:

::

     rectangle box = { { 0.0, 0.0 }, 100.0, 200.0 };

.. index::
   pair: structure; nested structure  

The innermost curly braces are the coordinates of the corner point;
together they make up the first of the three values that go into the new
``rectangle``.
This statement is an example of a **nested structure**.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      The active code below uses the ``rectangle`` structure. Feel free to
      modify the code and experiment around!

      .. tb-code:: cpp
         :name: rectangles_AC_1
         :caption: Example rectangles_AC_1
         :compileargs: ['-Wall', '-std=c++20']

         #include <iostream>

         struct point {
             double x, y;
         };

         struct rectangle {
             point corner;
             double width, height;
         };

         int main() {
             using std::cout;
             using std::endl;
             rectangle box = { { 0.0, 0.0 }, 100.0, 200.0 };
             box.width += 50.0;
             cout << box.height << endl;
             cout << box.width << endl;
         }

   .. tb-tab:: Q2

      .. tb-choice::
         :name: rectangles_1

         How can you combine these two statements into one?

         .. code-block:: cpp

            Point temp = box.corner;
            double y = temp.y;


         - [ ] ``double y = corner.box.y;``

           - Try again.

         - [x] ``double y = box.corner.y;``

           + Correct!

         - [ ] ``double y = corner.y;``

           - Try again.

         - [ ] ``double y = box.y;``

           - Try again.


   .. tb-tab:: Q3

      .. tb-click::
         :name: rectangles_2

         Click on the legal ways to create a point and rectangle structure, assuming that the point and rectangle structures are declared above the main function in the same way as in the active code above.

         .. code-block:: cpp

            def main() {
                point corner = { 0.0, 0.0 );
                rectangle box = { ( 0.0, 0.0 ), 100.0, 200.0 }
                rectangle box = { { 0.0, 0.0 }, 100.0, 200.0 };
                point corner = { 0.0, 0.0 };
                rectangle box = { corner, 100.0, 200.0 };
            }


         .. tb-miss:: text:def main() {

            Re-read the text above and try again.

         .. tb-miss:: text:point corner = { 0.0, 0.0 );

            Re-read the text above and try again.

         .. tb-miss:: text:rectangle box = { ( 0.0, 0.0 ), 100.0, 200.0 }

            Re-read the text above and try again.

         .. tb-hit:: text:rectangle box = { { 0.0, 0.0 }, 100.0, 200.0 };

            Correct.

         .. tb-hit:: text:point corner = { 0.0, 0.0 };

            Correct.

         .. tb-hit:: text:rectangle box = { corner, 100.0, 200.0 };

            Correct.

