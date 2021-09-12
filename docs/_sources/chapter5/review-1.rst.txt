Multiple Choice Exercises
-------------------------

.. tabbed:: self_check

   .. tab:: Q1

      .. mchoice:: mce_5_1
          :practice: T

          What should be the return type of the function ``convertToCelsius``?

          .. code-block:: cpp

            ______ convertToCelsius (double fahrenheit) {
              double celsius;
              celsius = (fahrenheit - 32) * 5 / 9;
              return celsius;
            }
              
          - ``int``

            - What variable are we returning in the function, and what is the variable's type? 

          - ``double``

            + The function returns ``celsius``, which is a ``double``.

          - ``string``

            - What variable are we returning in the function, and what is the variable's type? 

          - ``void``

            - Since we are returning something in the function, the function is not ``void``.

   .. tab:: Q2

      .. mchoice:: mce_5_2
          :practice: T

          What would be returned by ``secretFunction`` if the input was 14?

          .. code-block:: cpp

            int secretFunction (int input) {
              if (input % 2 == 0) {
                return 3 * input - 2;
              }
              else {
                if (input % 7 == 0) {
                  return input;
                }
                return 2 * input + 9;
              }
              return input + 4;
            }  

          - 14

            - Although 14 is divisible by 7, take another look at the conditionals. 

          - 18

            - The flow of code would never reach the last return statement.

          - 36

            - Check your order of operations! 

          - 37

            - Take a closer look at the conditional statements. 

          - 40

            + Since 14 is divisible by 2, the function returns two less than three times 14.

   .. tab:: Q3

      .. mchoice:: mce_5_3
                :practice: T

          If we wanted to create a boolean function called ``isPrime``, which takes an ``int input``
          as a parameter, which of the following would be the correct function header?

          - ``boolean isPrime (int input) {``

            - In C++, use the ``bool`` keyword for a boolean. 

          - ``bool isPrime (input) {``

            - In a function header, the type of each variable must be specified in the parameter list.

          - ``bool isPrime (int input) {`` 

            + This is the correct function header for the function.

          - ``int isPrime (bool input) {``

            - Take a closer look at what the return type is.

   .. tab:: Q4

      .. mchoice:: mce_5_4
          :practice: T

          If we wrote the following function, which of the other functions below can we also legally write
          and add to the program?

          .. code-block:: cpp

            int func (double x, bool y);

          - ``int func (double a, bool b);``

            - Since this function has the same name and parameter types as the given function, it is not allowed.

          - ``int foo (double x, bool y);``

            + This function has a different name from the given function, so it is allowed.

          - ``int func (double x);``

            + Although this function has the same name as the given function, it has a different number of parameters, so it is allowed.

          - ``void func (double x, bool y);``

            - Although this function has a different return type, its parameter list is the same as the given function, so it is not allowed.

          - ``int func (bool y, double x);``

            + Although this function has the same name as the given function, its parameter list is in a different order, so it is allowed.

   .. tab:: Q5

      .. mchoice:: mce_5_5
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

            int main() {
              bool x = 2 < 3;
              cout << x;
              cout << false;
              cout << ((1 + 4) * 4 > 24);
              cout << (23 == (32 + 2 - 11));
            }

          - 1001

            + Since the first and last statements are true and the middle two are false, this is the correct output.

          - truefalsefalsetrue

            - In C++, boolean values are outputted as 0 or 1.

          - 1false01

            - Since the second ``cout`` statement doesn't have quotes around the word "false", the value of 0 is outputted.

          - 0110

            - Remember that if a boolean expression is true, it has a value of 1.

   .. tab:: Q6

      .. mchoice:: mce_5_6
          :practice: T

          What is the output of the code below?

          .. code-block:: cpp

            int main() {
              bool w = !(2 * 3 == 6 || 4 - 3 > 8);
              bool x = true || 4 > 6;
              bool y = 3 != 6 - 3 && 23 >= 23;
              bool z = (4 + 9 < 15 && 3 != 4) || 2 + 5 == 7;  
              cout << w << x << y << z;
            }

          - 0101

            + Since the expressions are false, true, false, and true, the output is 0101.

          - 1010

            - Remember that ``true`` outputs to 1 and ``false`` outputs to 0.

          - 1101

            - Remember the NOT operator (!) inverts the value of a boolean.

          - 0100

            - Take a closer look at the order of operations.

          - 0110

            - Take a closer look at the expressions.

   .. tab:: Q7

      .. mchoice:: mce_5_7
          :practice: T

          Are there any issues with the code below?

          .. code-block:: cpp

            bool isEven (int num) {
              if (num % 2 == 0) {
                return true;
              }
            }

          - Yes, we have to return either 0 or 1.

            - Returning a 0 or 1 would be returning an ``int``, even though booleans evaluate to 0 or 1.

          - Yes, we cannot pass an ``int`` into a ``bool`` function.

            - The type of variables in the parameter list do not affect the return type.

          - Yes, there is no case for odd numbers.

            + Since we never established an else clause, if the input was an odd number, the function would not return anything despite not being a void function.

          - There are no issues with the code.

            - There is an issue with the code. Can you find it?

   .. tab:: Q8

      .. mchoice:: mce_5_8
          :practice: T

          Are there any issues with the code below?

          .. code-block:: cpp

            double Free_time (int day) {
              if (day==1||day==2||day==3||day==4) {
                cout<<"Better study on weekday!"<<endl;
                return day*0.25;
              }
              else{
                cout<<"Happy weekend"<<endl;
                return day;
              }
            }

          - Yes, we might not return anything.

            - We have an else clause in which we return a value. 

          - Yes, we cannot return an entire expression like ``day*0.25``.

            - If the result of the expression is compatible with the return type we can return it.

          - Yes, we are returning an ``int`` (in the ``else`` block) where as the return type is ``double``.

            - Implicit conversion from an int to double is ok in c++!

          - There are no issues with the code.

            + Correct! implicit conversion from int to double are ok!

   .. tab:: Q9

      .. mchoice:: mce_5_9
          :practice: T

          Are there any issues with the code below?

          .. code-block:: cpp

            void moonWeight (double earth) {
              double moon = 0.165 * earth;
              cout << "You would weigh " << moon << " pounds on the moon." << endl;
              return moon;
            }

          - Yes, we cannot have ``cout`` statements in a function.

            - We are allowed to use ``cout`` statements in a function.

          - Yes, we cannot return anything.

            + ``void`` functions do not have return values, so we cannot return ``moon``.

          - Yes, we need to return the output statement.

            - ``void`` functions do not have return values.

          - There are no issues with the code.

            - There is an issue with the code. Can you find it?

   .. tab:: Q10

      .. mchoice:: mce_5_10
          :practice: T

          What is the return type of main?

          - ``void``

            - What keyword do we use before ``main()`` in every program?

          - ``bool``

            - What keyword do we use before ``main()`` in every program?

          - ``double``

            - What keyword do we use before ``main()`` in every program?

          - ``int``

            + Yes, ``main`` is supposed to return an integer, which is why programmers often return 0 at the end of ``main``.

   .. tab:: Q11

      .. mchoice:: mce_5_11
          :practice: T

          What is the base case of the ``factorial`` recursive function?

          .. code-block:: cpp

            int factorial (int n) {
              if (n == 0) {
                return 1;
              }
              else {
                int recurse = factorial (n-1);
                int result = n * recurse;
                return result;
              }
            }

          - ``n = 0``

            + When ``n`` is 0, the function returns the value 1 without making a recursive call.

          - ``n = 1``

            - When ``n`` is 1, the function makes a recursive call in the else statement.

          - ``n = -1``

            - ``n`` never becomes -1.

          - There is no base case.

            - If there was no base case, the function would recurse infinitely.

   .. tab:: Q12

      .. mchoice:: mce_5_12
          :practice: T

          What is printed?

          .. code-block:: cpp

            void print_sequence (int n) {
              if (n == 0) {
                 cout<<1;
                 return;
                 //we can have an empty return to a void function
              }
              else {
                cout<<n<<" ";
                print_sequence(n-1);
              }
            }

            int main(){
                int val=6;
                print_sequence(val);
            }

          - 6 5 4 3 2 1 0

            - Check what the base case prints.

          - 6 6 6 6 6 6 1

            - What value do we give the recursive call?

          - 6 5 4 3 2 1

            - The base case prints something!

          - 6 5 4 3 2 1 1

            + We print a number and decrement it till we reach 0 then we print 1.
