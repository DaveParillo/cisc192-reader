Composition
-----------

.. index::
   single: composition

By now we have seen several examples of **composition** (the ability to
combine language features in a variety of arrangements). One of the
first examples we saw was using a function invocation as part of an
expression. Another example is the nested structure of statements: you
can put an ``if`` statement within a ``while`` loop, or within another
``if`` statement, etc.

Having seen this pattern, and having learned about vectors and objects,
you should not be surprised to learn that you can have vectors of
objects. In fact, you can also have objects that contain vectors (as
instance variables); you can have vectors that contain vectors; you can
have objects that contain objects, and so on.

In the next two chapters we will look at some examples of these
combinations, using ``playing_card`` objects as a case study.

.. tb-choice::
   :name: c192_composition_1



   - [x] You can have vectors that contain other vectors and objects that contain other objects.

     This is called composition!
   - [ ] You can have vectors that contain other vectors, but you can never have objects that contain other objects.

     in this chapter you will see how you can have objects that contain other objects.
   - [ ] You can never have vectors that contain other vectors, but you can have objects that contain other objects.

     in this chapter you will see how you can have vectors that contain other vectors.
   - [ ] You can never have vectors that contain other vectors, nor objects that contain other objects.

     Vectors and objects can have nested compositons!

.. tb-blank::
   :name: c192_composition_2

   There are many different arrangements to combine language features.  This is called __________.

   {{blank}}

   .. tb-answer::
      :match: ([Cc]omposition)|(COMPOSITION)
      :feedback: Correct!
      :incorrect: Incorrect!  Try again!

