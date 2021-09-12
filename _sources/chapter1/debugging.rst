What is Debugging?
------------------

.. index::
   single: bug

.. index::
   single: debug

Programming is a complex process, and since it is done by human beings,
it often leads to errors. For whimsical reasons, programming errors are
called **bugs** and the process of tracking them down and correcting
them is called **debugging**.

There are a few different kinds of errors that can occur in a program,
and it is useful to distinguish between them in order to track them down
more quickly.

Compile-time errors
~~~~~~~~~~~~~~~~~~~

.. index::
   single: syntax error
   single: compile error

The compiler can only translate a program if the program is
syntactically correct; otherwise, the compilation fails and you will not
be able to run your program.
 
.. index::
   single: syntax

.. note::
   **Syntax** refers to the structure of your program and the rules about 
   that structure.

For example, in English, a sentence must begin with a capital letter and
end with a period. this sentence contains a syntax error. So does this
one

For most readers, a few syntax errors are not a significant problem,
which is why we can read the poetry of e e cummings without spewing
error messages.

Compilers are not so forgiving. If there is a single syntax error
anywhere in your program, the compiler will print an error message and
quit, and you will not be able to run your program.

To make matters worse, there are more syntax rules in C++ than there are
in English, and the error messages you get from the compiler are often
not very helpful. During the first few weeks of your programming career,
you will probably spend a lot of time tracking down syntax errors. As
you gain experience, though, you will make fewer errors and find them
faster.

.. _run-time:

Run-time errors
~~~~~~~~~~~~~~~

.. index::
   single: run-time error

The second type of error is a **run-time error**, so-called because the
error does not appear until you run the program.

For the simple sorts of programs we will be writing for the next few
weeks, run-time errors are rare, so it might be a little while before
you encounter one.

Logic errors and semantics
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. index::
   single: logical error
   single: semantic error

The third type of error is the **logical** or **semantic** error. 

.. index::
   single: semantics

.. note::
   **Semantics** refer to the meaning of the program.

If there is a semantic error in your program, it will compile and run
successfully, in the sense that the computer will not generate any error
messages, but it will not do the right thing. It will do something else.
**Specifically, it will do what you told it to do.**

The problem is that the program you wrote is not the program you wanted
to write. The meaning of the program is wrong. Identifying semantic errors 
can be tricky, since it requires you to work backwards by looking at the 
output of the program and trying to figure out what it is doing.

Experimental debugging
~~~~~~~~~~~~~~~~~~~~~~

One of the most important skills you should acquire from working with
this book is debugging. Although it can be frustrating, debugging is one
of the most intellectually rich, challenging, and interesting parts of
programming.

In some ways debugging is like detective work. You are confronted with
clues and you have to infer the processes and events that lead to the
results you see.

Debugging is also like an experimental science. Once you have an idea
what is going wrong, you modify your program and try again. If your
hypothesis was correct, then you can predict the result of the
modification, and you take a step closer to a working program. If your
hypothesis was wrong, you have to come up with a new one. As Sherlock
Holmes pointed out, “When you have eliminated the impossible, whatever
remains, however improbable, must be the truth.” (from A. Conan Doyle’s
*The Sign of Four*).

For some people, programming and debugging are the same thing. That is,
programming is the process of gradually debugging a program until it
does what you want. The idea is that you should always start with a
working program that does *something*, and make small modifications,
debugging them as you go, so that you always have a working program.

For example, Linux is an operating system that contains thousands of
lines of code, but it started out as a simple program Linus Torvalds
used to explore the Intel 80386 chip. According to Larry Greenfield,
“One of Linus’s earlier projects was a program that would switch between
printing AAAA and BBBB. This later evolved to Linux” (from *The Linux
Users’ Guide* Beta Version 1).

In later chapters I will make more suggestions about debugging and other
programming practices.


.. tabbed:: tab_check

   .. tab:: Q1

      .. fillintheblank:: debugging_1

         Another word for an error is a(n) |blank|.  The process of finding 
         and fixing errors is called |blank|.
          
         - :[Bb][Uu][Gg]: Correct!
           :.*: Try again!
         - :[Dd][Ee][Bb][Uu][Gg][Gg][Ii][Nn][Gg]: Correct!
           :.*: Try again!

   .. tab:: Q2

      .. dragndrop:: debugging_2
         :feedback: Try again!
         :match_1: syntax (compile-time) error|||an error that surfaces when something is wrong with the structure of your program
         :match_2: run-time error|||an error that comes up when your program is executed
         :match_3: semantic error|||your program does what you told it to do, not what you intended for it to do

         Match each term to its definition!

   .. tab:: Q3

      .. fillintheblank:: debugging_3

         The structure of your program and the rules it must follow are called the |blank|.
          
         - :[Ss][Yy][Nn][Tt][Aa][Xx]: Correct!
           :.*: Try again!
