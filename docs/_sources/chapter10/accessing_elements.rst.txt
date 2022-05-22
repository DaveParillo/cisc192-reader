Accessing elements
------------------

.. index::
   single: vector indexing

The ``[]`` operator reads and writes the elements of a vector in much
the same way it accesses the characters in an ``string``.
This is called **vector indexing**.
As with ``string``\ s, the indices start at zero, so ``count[0]`` 
refers to the "zeroeth" (or *first*) element of the vector,
and ``count[1]`` refers to the *second* element.
You can use the ``[]`` operator anywhere in an expression:

::

     std::vector<int count(5);
     count[0] = 7;              // assignment
     int first = count[0];      // access
     count[1] = count[0] * 2;
     ++count[2];
     count[3] -= 60;

All of these are legal assignment statements.
The effect of this code fragment is:

.. graphviz::
   :align: center
   :alt: Vector assignment

   digraph c {
     rankdir=LR
     nodesep=0
     fontname = "Bitstream Vera Sans"
     label="Vector assignment"
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
        label = "{7|14|1|-60|0}"
     ]
     node [ shape=plain]
     idx [style="", 
        label = "0  1  2   3   4"
     ]
     }
     count [shape=plain, style=""]
     count->arr [style=invis]
   }


.. index::
   single: index

.. warning::
   Since elements of this vector are numbered from 0 to 4, there is no
   element with the index 5. It is a common error to go beyond the bounds
   of a vector, which causes a run-time error (if you are lucky. 
   The program may print an error and quit or it may
   simply produce incorrect results, but continue running.

You can use any expression as an **index**, as long as it has type ``int``.
A common way to index a vector is with a loop variable.
For example:

::

     int i = 0;
     while (i < 5) {
       cout << count[i] << endl;
       ++i;
     }

This ``while`` loop counts from 0 to 5; when the loop variable ``i`` is
5, the condition fails and the loop terminates. Thus, the body of the
loop is only executed when ``i`` is 0, 1, 2, 3, and 4.

Each time through the loop we use ``i`` as an index into the vector,
outputting the ``i``\ th element. This type of vector traversal is very
common.

.. activecode:: accessing_elements_AC_1
   :language: cpp
   :compileargs: ['-Wall', '-std=c++11']
   :nocodelens:

   Take a look at the active code below.
   We can modify the vectors by accessing its elements.
   ~~~~
   #include <cstddef>   // size_t
   #include <iostream>
   #include <vector>

   using std::cout;

   void print_vec(std::vector<int> data) {
       cout << '[';
       size_t i = 0;
       while (i < data.size()) {
           cout <<  data[i] << ',';
           ++i;
       }
       cout << "]\n";
   }

   int main() {
       // notice we used a list to initialize values
       std::vector<int> count = {1,2,3,4};
       cout << "Before we make any changes, count = "; print_vec(count);
       count[0] = 7;
       count[1] = count[0] * 2;
       count[2]++;
       count[3] -= 60;
       cout << "After we made the above changes, count = "; print_vec(count);
   }

Note we use the type ``size_t`` instead of ``int`` in this example.
The data type returned from the vector :vector:`size` function is ``size_t``.
It is a type capable of storing the largest possible array (or vector) index
on your computer.
The maximum size will vary among different types of computers.

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: accessing_elements_1

          **Multiple Response** How would you increment the third element of ``vector<int> vec`` by one?

          -   ``vec[3] = vec[3]++;``

              -   Incorrect! This is actually incrementing the 4th element of **vec**, since vectors are zero indexed.

          -   ``vec(3) = vec(3) + 1;``

              -   Incorrect! This is not proper syntax.

          -   ``vec[2] = vec[2]++;``

              +   ``vec[2]`` is the third element and we increment it by using the ``++`` operator.

          -   ``vec(2) = vec(2)++;``

              -   This is not proper syntax.

          -   ``vec[2] = vec[2] + 1``

              +   ``vec[2]`` is the third element and we increment it by adding 1.


   .. tab:: Q2

      .. fillintheblank:: accessing_elements_2

          What is the highest index reached by ``while(i < 7)``?

          - :6: Correct!
            :7: The loop runs 7 times, but vectors are zero indexed, so the loop never reaches the 7th index!
            :.*: Try again.
