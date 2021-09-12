.. _formal:

Formal and Natural Languages
----------------------------

.. index::
   single: natural language

**Natural languages** are the languages that people speak, like English,
Spanish, and French. They were not designed by people (although people
try to impose some order on them); they evolved naturally.

.. index::
   single: formal language
   
**Formal languages** are languages that are designed by people for
specific applications. For example, the notation that mathematicians use
is a formal language that is particularly good at denoting relationships
among numbers and symbols. Chemists use a formal language to represent
the chemical structure of molecules. And most importantly:

.. note::
   Programming languages are **formal languages** that have been designed
   to express computations.

As I mentioned before, formal languages tend to have strict rules about
syntax. For example, :math:`3+3=6` is a syntactically correct
mathematical statement, but :math:`3=+6\$` is not. Also, :math:`H_2O` is
a syntactically correct chemical name, but :math:`_2Zz` is not.

Syntax rules come in two flavors, pertaining to tokens and structure.
Tokens are the basic elements of the language, like words and numbers
and chemical elements. One of the problems with 3=+6$ is that $ is not a
legal token in mathematics (at least as far as I know). Similarly,
:math:`_2Zz` is not legal because there is no element with the
abbreviation :math:`Zz`.

The second type of syntax error pertains to the structure of a
statement; that is, the way the tokens are arranged. The statement 3=+6$
is structurally illegal, because you can’t have a plus sign immediately
after an equals sign. Similarly, molecular formulas have to have
subscripts after the element name, not before.

When you read a sentence in English or a statement in a formal language,
you have to figure out what the structure of the sentence is (although
in a natural language you do this unconsciously). 

.. index::
   single: parse

.. note::
   The process of examining a program and analysing the syntactic structure
   is called **parsing**.

For example, when you hear the sentence, “The other shoe fell,” you
understand that “the other shoe” is the subject and “fell” is the verb.
Once you have parsed a sentence, you can figure out what it means, that
is, the semantics of the sentence. Assuming that you know what a shoe
is, and what it means to fall, you will understand the general
implication of this sentence.

Although formal and natural languages have many features in
common—tokens, structure, syntax and semantics—there are many
differences.

ambiguity:
    Natural languages are full of ambiguity, which people deal with by
    using contextual clues and other information. Formal languages are
    designed to be nearly or completely unambiguous, which means that
    any statement has exactly one meaning, regardless of context.

redundancy:
    In order to make up for ambiguity and reduce misunderstandings,
    natural languages employ lots of redundancy. As a result, they are
    often verbose. Formal languages are less redundant and more concise.

literalness:
    Natural languages are full of idiom and metaphor. If I say, “The
    other shoe fell,” there is probably no shoe and nothing falling.
    Formal languages mean exactly what they say.

People who grow up speaking a natural language (everyone) often have a
hard time adjusting to formal languages. In some ways the difference
between formal and natural language is like the difference between
poetry and prose, but more so:

poetry:
    Words are used for their sounds as well as for their meaning, and
    the whole poem together creates an effect or emotional response.
    Ambiguity is not only common but often deliberate.

prose:
    The literal meaning of words is more important and the structure
    contributes more meaning. Prose is more amenable to analysis than
    poetry, but still often ambiguous.

programs:
    The meaning of a computer program is unambiguous and literal, and
    can be understood entirely by analysis of the tokens and structure.

Here are some suggestions for reading programs (and other formal
languages). First, remember that formal languages are much more dense
than natural languages, so it takes longer to read them. Also, the
structure is very important, so it is usually not a good idea to read
from top to bottom, left to right. Instead, learn to parse the program
in your head, identifying the tokens and interpreting the structure.
Finally, remember that the details matter. Little things like spelling
errors and bad punctuation, which you can get away with in natural
languages, can make a big difference in a formal language.

.. tabbed:: tab_check

   .. tab:: Q1

      .. mchoice:: formal_natural_1
         :multiple_answers:
         :answer_a: C++
         :answer_b: scientific notation
         :answer_c: Mandarin
         :answer_d: English
         :answer_e: chemical formulas
         :correct: a,b,e
         :feedback_a: All programming languages are formal languages!
         :feedback_b: Scientific notation is designed to denote large numbers.
         :feedback_c: Mandarin is a natural language.
         :feedback_d: English is a natural language.
         :feedback_e: Chemical formulas represent what elements a compound is made of! For example CO2 is is carbon dioxide!

         **Multiple Response** Select all **formal** languages from the choices below.

   .. tab:: Q2

      .. fillintheblank:: formal_natural_2

         Analyzing the structure of a sentence or a program is called |blank|.
          
         - :[Pp][Aa][Rr][Ss][Ii][Nn][Gg]: Correct!
           :.*: Try again!


   .. tab:: Q3

      .. dragndrop:: formal_natural_3
         :feedback: Try again!
         :match_1: ambiguity|||being unclear and open to interpretation
         :match_2: redundancy|||being repetetive to get the point across
         :match_3: literalness|||meaning exactly what is said, nothing more

         Match each term to an example of it!


   .. tab:: Q4

      .. mchoice:: formal_natural_4
         :multiple_answers:
         :answer_a: ambiguous
         :answer_b: redundant
         :answer_c: literal
         :answer_d: verbose
         :answer_e: concise
         :correct: c,e
         :feedback_a: Formal languages are designed to be unambiguous, so that each statement has only one meaning.
         :feedback_b: Formal language is straight to the point.
         :feedback_c: Formal languages mean exactly what they say.
         :feedback_d: Formal language is straight to the point.
         :feedback_e: Formal language is straight to the point.

         **Multiple Response** Formal languages are...

