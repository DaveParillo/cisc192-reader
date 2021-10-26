Multiple Choice Exercises
-------------------------

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: mce_6_1
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

             int main() {
               int x = 0;
               int i = 1;
               while (i < 10) {
                 x = i;
                 i++;
               }
               cout << x;
             }

          - 0

            - ``x`` is initialized to 0, but it's value is reassigned in the while loop. Can you figure out what the final value assigned to ``x`` is?
          
          - 1
          
            - When ``i`` is 1, ``x`` is assigned the value of ``i``, so ``x`` is 1. However, the while loop continuously increments i, so the final value of ``x`` is not 1. 
          
          - 9
          
            + ``x`` is assigned the value of 9 during the last iteration of the while loop, and thus 9 is the output of the program.
          
          - 10
          
            - ``i`` is incremented to a value of 10, but since ``i < 10`` is false, the contents of the while loop is not executed, so ``x`` is never assigned the value of 10.

   .. tab:: Q2

      .. mchoice:: mce_6_2
          :practice: T

          What is the final value of ``i`` when the code is finished running?

          .. code-block:: cpp

             int main() {
               int x = 0;
               int i = 1;
               while (i < 10) {
                 x = i;
                 i++;
               }
               cout << x;
             }

          - 0
          
            - ``i`` is initialized with a value of 1 and is incremented, so it will never have a value of 0.
          
          - 1
          
            - ``i`` is initialized with a value of 1 but it is incremented during the while loop.
          
          - 9
          
            - This is the final value of ``x`` when the code is finished running.
          
          - 10
          
            + In order for the while loop to terminate, the condition ``i < 10`` must be false, and this is achieved when ``i`` is incremented to 10.

   .. tab:: Q3

      .. mchoice:: mce_6_3
          :practice: T

          How many times does the following while loop run?

          .. code-block:: cpp

             int main() {
               int i = 6;
               while (i > 2) {
                 i = i + 4;
                 if (i > 8) {
                   i = i - 5;
                 }
               }
             }

          - 1
          
            - Take a closer look at the while loop and conditional.
          
          - 3
          
            - Take a closer look at the while loop and conditional.
          
          - 5
          
            - Take a closer look at the while loop and conditional.
          
          - The loop will run infinitely.
          
            + The value of ``i`` will always be greater than 2, resulting in an infinite loop.

   .. tab:: Q4

      .. mchoice:: mce_6_4
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

             int main() {
               int n = 10;
               // cout << "Da ";
               cout << "na ";
               while (n != 3) {
                 cout << "na ";
                 n--;
               }
               cout << "Batman!";
             }

          - na na na na na na na na Batman!
          
            + The code prints out eight "na"s before printing out "Batman!"
          
          - na na na na na na na Batman!
          
            - Look over the code carefully. There are output statements before the while loop.
          
          - Da na na na na na na na na Batman!
          
            - Will "Da" ever be printed?
          
          - It will result in an infinite loop.
          
            - Since we repeatedly decrement ``n`` inside the while loop, it will eventually be equal to 3 and the while loop will terminate.

   .. tab:: Q5

      .. mchoice:: mce_6_5
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

             int main() {
               int n = 10;
               cout << "Da ";
               cout << "na ";
               while (n != 3) {
                 cout << "na ";
               }
               cout << "Batman!";
             }

          - Batman!
          
            - Take a closer look at the while loop.
          
          - Da Batman!
          
            - Take a closer look at the while loop.
          
          - Da na na na na na na na na Batman!
          
            - Take a closer look at the while loop.
          
          - It will result in an infinite loop.
          
            + Since we never change the value of ``n``, 10 will never equal 3 so the code will run forever.

   .. tab:: Q6

      .. mchoice:: mce_6_6
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

             int main() {
               int x = 1;
               while (x < 6) {
                 cout << x << "\t" << pow (x, 5) / pow (x, 3) << endl;
                 x++;
               }
             }

          - The first six perfect fifths.

            - Take a closer look at the while loop and what ``x`` was initialized to.
          
          - The first six perfect squares.

            - Take a closer look at the while loop and what ``x`` was initialized to.
          
          - The first five perfect squares.

            + Dividing ``x`` to the power of 5 by ``x`` to the power of 3 effectively results in perfect squares.
          
          - The first five perfect cubes.
          
            - Take a closer look at the mathematical expression inside the while loop.

   .. tab:: Q7

      .. mchoice:: mce_6_7
          :practice: T

          Why are we allowed to use the variable ``x`` in both ``main`` and in the function definition of ``superSecretFunction``?

          .. code-block:: cpp
         
             int superSecretFunction (int n) {
               int x = 0;
               return (2 + (n * n) - 5 * n / 7) * x;
             }

             int main() {
               int x = 1;
               cout << "After using the super secret function, we get " << superSecretFunction (x);
             }

          - We're using the same variable, but just reassigning the value from 0 to 1.

            - We are actually using two different variables that happen to have the same name.

          - Although the name of both variables is ``x``, they represent different locations in memory, and thus are different variables.
          
            + One ``x`` is a local variable of ``superSecretFunction`` while the other is a local variable of ``main``.

          - We can assign them different values but not the same value. Thus, if both were initialized to 0, then we'd get an error.

            - Since they are not in the same storage location, they can store any value, including the same value.

          - We're not allowed to do this. The code will result in an error.

            - The code does not produce an error.

   .. tab:: Q8

      .. mchoice:: mce_6_8
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp
         
             int loopFive (int n) {
               while (n % 5 != 0) {
                 n = n + 3;
               }
               return n;
             }
 
             int main() {
               cout << loopFive (2);
               cout << loopFive (3);
               cout << loopFive (4);
             }

          - 51510

            + ``n`` is repeatedly incremented by 3 until it is divisible by 5, and this happens when ``n`` is 5, 15, and 10 for the inputs of 2, 3, and 4 respectively.

          - 234
          
            - Although the function returns ``n``, ``n`` might not be its original value.

          - 5 15 10

            - Take a closer look at the output statements.

          - 567

            - Take a closer look at the ``while`` loop in the function.

   .. tab:: Q9

      .. mchoice:: mce_6_9
          :practice: T

          The super evil villian RePete wants to annoy the city by
          hacking into the city's helper robots and making them repeat
          everything they say 5 times. However, there's an error in his 
          code and now the robots won't stop repeating! Can you find the
          error?

          .. code-block:: cpp
         
             void repeat_bot (string input) {
               int n = 0;
               while (n < 5) {
                 cout << input << ' ';
                 n--;
               }
             }

             int main() {
               repeat_bot ("Hello, how may I help you?");
             }

          - ``repeat_bot`` can only take one word as an argument.

            - A ``string`` is any number of characters or words surrounded by double quotes, not just one word.

          - ``n`` is declared to be 0 and 0 is always less than 5.
          
            - The code doesn't loop infinitely because of the value ``n`` was declared to be.

          - Every time the ``while`` loop runs, ``n`` is reset to 0, so it will always be less than 5.

            - The initialization of ``n`` occurs outside the ``while`` loop, so the value of ``n`` does not get reset to 0.

          - ``n`` is declared to be 0 and we continuously decrement ``n`` so it will always be less than 5.

            + Since ``n`` starts at 0 and gets smaller, the conditional for the ``while`` loop will always be true, and thus the code runs forever.

   .. tab:: Q10

      .. mchoice:: mce_6_10

          After making some changes to his code, RePete tries again.
          This time, however, the robots don't repeat anything!
          Can you find the new error?

          .. code-block:: cpp
         
           void repeat_bot (string input) {
             int n = 0;
             while (n > 5) {
               cout << input << ' ';
               n++;
             }
           }

           int main() {
             repeat_bot ("Hello, how may I help you?");
           }

          - ``n > 5`` is not a valid conditional, so the ``while`` loop doesn't execute.

            - ``n > 5`` is a boolean statement and thus is a valid conditional.

          - The value of ``n`` never gets modified in the ``while`` loop.
          
            - ``n`` is incremented in the ``while`` loop after the ``cout`` statement.

          - In the ``cout`` statement, only spaces are printed.

            - ``input`` is also printed.

          - The conditional for the ``while`` loop is not met.

            + Since ``n`` is declared to be 0, 0 is not greater than 5, so the ``while`` loop does not execute.

