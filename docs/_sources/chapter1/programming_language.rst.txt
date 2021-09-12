What is a Programming Language?
-------------------------------

.. index::
   single: high-level language

The programming language you will be learning is C++. It is a **high-level language**.

.. index::
   single: low-level language

As you might infer from the name “high-level language,” there are also
**low-level languages**, sometimes referred to as machine language or
assembly language. Loosely-speaking, computers can only execute programs
written in low-level languages. Thus, programs written in a high-level
language have to be translated before they can run. This translation
takes some time, which is a small disadvantage of high-level languages.

.. index::
   single: portable

But the advantages are enormous. First, it is *much* easier to program
in a high-level language; by “easier” I mean that the program takes less
time to write, it’s shorter and easier to read, and it’s more likely to
be correct. Secondly, high-level languages are **portable**, meaning
that they can run on different kinds of computers with few or no
modifications. Low-level programs can only run on one kind of computer,
and have to be rewritten to run on another.

Due to these advantages, almost all programs are written in high-level
languages. Low-level languages are only used for a few special
applications.

.. index::
   single: interpreter
   single: interpret

There are two ways to translate a program; interpreting or
compiling. An **interpreter** is a program that reads a high-level
program and does what it says. In effect, it translates the program
line-by-line, alternately reading lines and carrying out commands.

.. digraph:: interpreters
   :align: center
   :alt: Simplified interpreter process

   fontname = "Bitstream Vera Sans"
   node [
      fontname = "Bitstream Vera Sans"
      fontsize = 11
      style=filled
      fillcolor=lightblue
   ]
   edge [constraint=false]

   label="Simplified interpreter process";
   labelloc=bottom;
   src [label="source \ncode", shape="box"];
   exe [label="executable\nprogram", shape="box"];
   src -> interpreter -> exe;

   node [
       shape="plain"
       style=none
   ]
   edge [style=invis, constraint=true]
   t1 [label="The interpreter\lreads the\lsource code ...\l"];
   t2 [label="... and the result\lappears on\lthe screen ...\l"];
   src -> t1;
   interpreter -> t1;
   interpreter -> t2;
   exe -> t2;
   {rank=sink; t1 t2};


.. index::
   single: compiler
   single: compile

.. index::
   single: source code

.. index::
   single: object code

.. index::
   single: executable

A **compiler** is a program that reads a high-level program and translates
it all at once, before executing any of the commands. Often you compile
the program as a separate step, and then execute the compiled code
later. In this case, the high-level program is called the **source
code**, and the translated program is called the **object code** or the
**executable**.

As an example, suppose you write a program in C++. You might use a text
editor to write the program (a text editor is a simple word processor).
When the program is finished, you might save it in a file named
program.cpp, where “program” is an arbitrary name you make up, and the
suffix .cpp is a convention that indicates that the file contains C++
source code.

Then, depending on what your programming environment is like, you might
leave the text editor and run the compiler. The compiler would read your
source code, translate it, and create a new file named program.o to
contain the object code, or program.exe to contain the executable.


.. digraph:: compilers
   :align: center
   :alt: Simplified compilation process

   fontname = "Bitstream Vera Sans"
   node [
      fontname = "Bitstream Vera Sans"
      fontsize = 11
      style=filled
      fillcolor=lightblue
   ]
   edge [constraint=false]

   label="Simplified compilation process";
   labelloc=bottom;
   rankdir=LR;
   src [label="source\ncode", shape="box"];
   obj [label="object\ncode", shape="box"];
   exe [label="executable\nprogram", shape="box"];
   src -> compiler -> obj -> linker -> exe;


   node [
       shape="plain"
       style=none
   ]
   edge [style=invis, constraint=true]
   t1 [label="The compiler\lreads the\lsource code ...\l"];
   t2 [label="... and generates\lobject code.\l"];
   t3 [label="the linker combines\lall the object files\linto an executable."];
   t4 [label="which can be run\land the result\lappears on\lthe screen ...\l"];
   src -> t1;
   compiler -> t1;
   compiler -> t2;
   obj  -> t2;
   obj  -> t3;
   linker  -> t3;
   linker  -> t4;
   exe  -> t4;

   {rank=sink; t1 t2 t3 t4};


The next step is to run the program, which requires some kind of
executor. The role of the executor is to load the program (copy it from
disk into memory) and make the computer start executing the program.

Although this process may seem complicated, the good news is that in
most programming environments (sometimes called development
environments), these steps are automated for you. Usually you will only
have to write a program and type a single command to compile and run it.
On the other hand, it is useful to know what the steps are that are
happening in the background, so that if something goes wrong you can
figure out what it is.


.. tabbed:: tab_check

   .. tab:: Q1

      .. fillintheblank:: program_lang_1

         A(n) |blank| translates a high-level program line by line, executing 
         commands as they come.  A(n) |blank| translates a high-level program 
         all at once, before executing any of the commands!

         - :[Ii][Nn][Tt][Ee][Rr][Pp][Rr][Ee][Tt][Ee][Rr]: Correct!
           :.*: Try again!
         - :[Cc][Oo][Mm][Pp][Ii][Ll][Ee][Rr]: Correct!
           :.*: Try again!

   .. tab:: Q2

      .. mchoice:: program_lang_2
         :multiple_answers:
         :answer_a: Almost all programs are written in high-level languages.
         :answer_b: Programs written in a high-level language must be translated before they can be run.
         :answer_c: It's easier to program in a low-level language than a high-level language.
         :answer_d: Computers can only execute programs written in high-level languages.
         :answer_e: High-level programs can only run on one kind of computer (you'd have to rewrite the program if you wanted to use a different machine).
         :correct: a,b
         :feedback_a: High-level languages are efficient and easy to understand, an obvious choice for writing a program!
         :feedback_b: All programs in high-level language must be translated to a low-level language before the computer can execute them!
         :feedback_c: Actually, its much the other way around!
         :feedback_d: Computers actually can't understand high-level languages as they are written.
         :feedback_e: High-level programs are portable, meaning they can run on different kinds of computers with little to no modification.

         **Multiple Response** Which is true about a high-level programming language?


   .. tab:: Q3

      .. mchoice:: program_lang_3
         :answer_a: To translate the program line by line.
         :answer_b: To copy the program from disk to memory and make the computer run the program.
         :answer_c: To translate the program all at once.
         :answer_d: To give an error message if something is preventing the code from being translated.
         :correct: b
         :feedback_a: This is the role of an interpreter!
         :feedback_b: The role of an executor is to carry out, or execute, the program!
         :feedback_c: This is the role of a compiler!
         :feedback_d: This happens automatically when we try to compile/interpret our program.

         What is the role of an executor?

   .. tab:: Q4

      .. dragndrop:: program_lang_4
         :feedback: Try again!
         :match_1: source code|||our program written in C++
         :match_2: object code|||translated version of our program that the computer can understand and execute

         Match each term to an example of it!
