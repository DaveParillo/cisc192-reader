Mixed-Up Code Exercises
-----------------------

Answer the following **Mixed-Up Code** questions to assess what you have learned in this chapter.

.. tabbed:: self_check

   .. tab:: Q1

      .. parsonsprob:: random_p1
         :numbered: left
         :adaptive:
         :noindent:

         Suppose you run Club Keno, and you are in charge of picking the 20
         random numbered balls between 1 and 80. 
         Construct a block of code that chooses these random numbers,
         then saves them to a vector called <code>keno</code>.
         -----
         std::vector<int> keno;
         =====
         std::random_device device;
         =====
         std::default_random_engine eng(device());
         =====
         for (int i = 0; i < 20; ++i) {
         =====
          int x = std::uniform_int_distribution<int> {1, 81} (eng);
         =====
          keno.push_back(x);
         =====
         }
         =====
         for (int i = 0; i <= 20; ++i) { #distractor
         =====
          int x = std::uniform_int_distribution<int> {0, 80} (eng); #distractor
         =====
          keno.push_back(i); #distractor

