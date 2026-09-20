.. _random-numbers-mixed-up-code-exercises:

Mixed-Up Code Exercises
-----------------------

Answer the following **Mixed-Up Code** questions to assess what you have learned in this chapter.

.. tb-group::
   :name: self_check

   .. tb-tab:: Q1

      .. tb-parsons::
         :name: random_p1
         :no-indent:

         Suppose you run Club Keno, and you are in charge of picking the 20
         random numbered balls between 1 and 80. 
         Construct a block of code that chooses these random numbers,
         then saves them to a vector called <code>keno</code>.

         .. code-block:: cpp

            {{group}}
            std::vector<int> keno;
            {{endgroup}}
            {{group}}
            std::random_device device;
            {{endgroup}}
            {{group}}
            std::default_random_engine eng(device());
            {{endgroup}}
            {{group}}
            for (int i = 0; i < 20; ++i) {
            {{endgroup}}
            {{group}}
             int x = std::uniform_int_distribution<int> {1, 81} (eng);
            {{endgroup}}
            {{group}}
             keno.push_back(x);
            {{endgroup}}
            {{group}}
            }
            {{endgroup}}
            {{distractor}}
            {{group}}
            for (int i = 0; i <= 20; ++i) { #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             int x = std::uniform_int_distribution<int> {0, 80} (eng); #distractor
            {{endgroup}}
            {{distractor}}
            {{group}}
             keno.push_back(i); #distractor
            {{endgroup}}

