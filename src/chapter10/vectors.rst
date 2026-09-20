Vectors
=======

.. index::
   single: vector

A :container:`vector` is a set of values where each value is identified by a
number (called an index). A ``string`` is similar to a vector, since it
is made up of an indexed set of characters. The nice thing about vectors
is that they can be made up of any type of element, including basic
types like ``int``\ s and ``double``\ s, and user-defined types like
``Point`` and ``Time``.

.. note::
   All elements of a vector must have the same type.

The ``vector`` type is defined in the C++ Standard Template Library
(STL). In order to use it, you have to include the header file
``vector``; again, the details of how to do that depend on your
programming environment.

You can create a vector the same way you create other variable types:

::

     vector<int> count;
     vector<double> doubleVector;

The type that makes up the vector appears in angle brackets (``<`` and
``>``). The first line creates a vector of integers named ``count``; the
second creates a vector of ``double``\ s. 
Each of these statements create empty vectors (their size is zero).
It is common to specify the size of the vector in parentheses:

::

     vector<int> count (5);

.. index::
   single: constructor

The syntax here is a little odd; it looks like a combination of a
variable declarations and a function call. 
In fact, that’s exactly what it is. 
The function we are invoking is a ``vector`` constructor. 
A **constructor** is a special function that creates new objects and
initializes their instance variables. 
In this case, the constructor takes a single argument, 
which is the size of the new vector.

The following figure shows how ``count`` could be represented in a state
diagram:

.. graphviz::
   :align: center
   :alt: Vector state diagram

   digraph c {
     rankdir=LR
     nodesep=0
     fontname = "Bitstream Vera Sans"
     label="Vector state diagram"
     node [
        fontname = "Courier"
        fontsize = 14
        shape = "record"
        style=filled
        fillcolor=lightblue
     ]
     subgraph cluster_0 {
     label=""
     arr [
        label = "{0|0|0|0|0}"
     ]
     node [ shape=plain]
     idx [style="", 
        label = "0  1  2  3  4"
     ]
     }
     count [shape=plain, style=""]
     count->arr [style=invis]
   }

.. index::
   single: elements

The numbers inside the shaded boxes are the **elements** of the vector.
The numbers below the boxes are the indices used to identify each box. 
When you allocate a new vector this way, 
the elements are "default initialized".
That is, each element is assigned the default value for whatever type
of data the vector stores.


There is another constructor for ``vector``\ s that takes two parameters.
The second parameter is a "fill value" -- the value that will be
assigned to each of the elements.

::

     vector<int> count (5, 3);

This statement creates a vector of five elements and initializes all of
them to three. 

.. graphviz::
   :align: center
   :alt: Vector filled with 3

   digraph c {
     rankdir=LR
     nodesep=0
     fontname = "Bitstream Vera Sans"
     label="Vector filled with 3"
     node [
        fontname = "Courier"
        fontsize = 14
        shape = "record"
        style=filled
        fillcolor=lightblue
     ]
     subgraph cluster_0 {
     label=""
     arr [
        label = "{3|3|3|3|3}"
     ]
     node [ shape=plain]
     idx [style="", 
        label = "0  1  2  3  4"
     ]
     }
     count [shape=plain, style=""]
     count->arr [style=invis]
   }

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-choice::
         :name: vectors_1

         would you create a vector of five words and initialize all of them to empty strings?

         ``vector<string> words ("", 5);``

         - [x] Incorrect! Vector parameters are in the wrong order.

         ``vector<string> words (5);``

         +   Correct! Vector elements are initialized to default values.

         ``vector<string> words (5, "");``

         - [ ] Partly correct! This works, but there is a simpler way that does not create redunadant strings

         ``vector<char> words (5, '');``

         - [ ] Incorrect! words should be a vector of strings. A char is not a string.

   .. tb-tab:: Q2

      .. tb-choice::
         :name: vectors_2




         - [ ] 1

           Incorrect! This is an integer, not a string.
         - [x] "a"

           Correct!
         - [ ] 'a'

           Incorrect! This is a character, not a string.
         - [x] "word"

           Correct!
         - [x] "1"

           Correct!

   .. tb-tab:: Q3

      .. tb-choice::
         :name: vectors_3



         - [ ] initializer

           Incorrect! Go back and read to find the answer!
         - [x] constructor

           Correct!
         - [ ] creator

           Incorrect! Go back and read to find the answer!
         - [ ] instance function

           Incorrect! Go back and read to find the answer!

   .. tb-tab:: Q4

      .. tb-choice::
         :name: vectors_4

         t are the values of ``number``'s elements after this declaration?

         code-block::

         vector<int> numbers(6);

          undefined (we don't know the values)

          - [x] These elements do have values

          0

          +    Yes, we have 6 default initialized integers.

          6

          - [ ] 6 is the size of the vector, not the values.

          0,1,2,3,4,5

          - [ ] These are the indices, not the values.

