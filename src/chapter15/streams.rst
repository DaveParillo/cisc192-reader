Streams
-------

To get input from a file or send output to a file, you have to create an
``ifstream`` object (for input files) or an ``ofstream`` object (for
output files). These objects are defined in the header file ``fstream``,
which you have to include.

.. index::
   single: stream

A **stream** is an abstract object that represents the flow of data from
a source like the keyboard or a file to a destination like the screen or
a file.

We have already worked with two streams: ``cin``, which has type
``istream``, and ``cout``, which has type ``ostream``. ``cin``
represents the flow of data from the keyboard to the program. Each time
the program uses the ``>>`` operator or the ``getline`` function, it
removes a piece of data from the input stream.

Similarly, when the program uses the ``<<`` operator on an ``ostream``,
it adds a datum to the outgoing stream.

.. tb-blank::
   :name: c192_question15_2_1

   You create an {{blank:blank1}} object to write data to a file, and a {{blank:blank2}} object to read data from a file.
   in order to define objects to input from a file or send output to a file, you must include the ``<`` {{blank:blank3}} ``>`` header file.

   .. tb-answer:: blank1
      :match: (?
      :feedback: o|O)(?:f|F)(?:s|S)(?:t|T)(?:r|R)(?:e|E)(?:a|A)(?:m|M): Correct!

   .. tb-answer:: blank2
      :match: x

   .. tb-answer:: blank3
      :match: [Ff][Ss][Tt][Rr][Ee][Aa][Mm]
      :incorrect: Incorrect! Try re-reading!

.. tb-choice::
   :name: question15_2_2

   What is a stream object?

   - [ ] an abstract object that works exclusively with cin and cout statements

     Incorrect! Stream objects do work with cin and cout, but that is not all that they do!
   - [x] an abstract object on which input and ouput operations are performed

     Correct!
   - [ ] an abstract object that works only with file data

     Incorrect! Stream objects do work with file data, but they do other things too.
   - [ ] an abstract object that controls the flow of statements

     Incorrect! This is not at all what stream objects do, you should try re-reading to get a better understanding!

.. tb-match::
   :name: c192_question15_1_3

    Match the stream to its type.

   std::cin
      std::istream
   std::cout
      std::ostream
