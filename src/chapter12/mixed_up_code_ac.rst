Activecode Exercises
--------------------

Answer the following **Activecode** questions to assess what you have learned in this chapter.

.. tb-group::
   :name: c192_mucp_12_1_ac

   .. tb-tab:: Question

       Let's write the struct definition for ``song``. song should have
       instance variables title, artist, and num_likes.

      .. tb-code:: cpp
         :name: c192_mucp_12_1_ac_q
         :caption: Example c192_mucp_12_1_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to define the ``song`` struct.

      .. tb-code:: cpp
         :name: c192_mucp_12_1_ac_a
         :caption: Example c192_mucp_12_1_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <cstddef>
         #include <string>
         #include <iostream>

         struct song {
             std::string title;
             std::string artist;
             std::size_t num_likes;
         };

.. tb-group::
   :name: c192_mucp_12_2_ac

   .. tb-tab:: Question

       Let's make an album! Write the struct definition for
       ``album``, which should have instance variables name, year and
       a vector of Songs.

      .. tb-code:: cpp
         :name: c192_mucp_12_2_ac_q
         :caption: Example c192_mucp_12_2_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to define the ``album`` struct.

      .. tb-code:: cpp
         :name: c192_mucp_12_2_ac_a
         :caption: Example c192_mucp_12_2_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct song {
             std::string title;
             std::string artist;
             std::size_t num_likes;
         };

         struct album {
             std::string name;
             int year;
             std::vector<song> songs;
         };

.. tb-group::
   :name: c192_mucp_12_3_ac

   .. tb-tab:: Question

       Two Songs are equal if the title and artist of the Songs are equal.
       Write the function ``song_equal``, which takes two Songs as parameters
       and returns true if they are equal.

      .. tb-code:: cpp
         :name: c192_mucp_12_3_ac_q
         :caption: Example c192_mucp_12_3_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>

         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``song_equal`` function.

      .. tb-code:: cpp
         :name: c192_mucp_12_3_ac_a
         :caption: Example c192_mucp_12_3_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <cstddef>
         #include <string>
         #include <iostream>

         struct song {
             std::string title;
             std::string artist;
             std::size_t num_likes;
         };

         bool song_equal (const song& a, const song& b) {
             if (a.title == b.title && a.artist == b.artist) {
                 return true;
             }
             else {
                 return false;
             }
         }

.. tb-group::
   :name: c192_mucp_12_4_ac

   .. tb-tab:: Question

       What if we'd like to search an album for our favorite song?
       Write the ``album`` member function search_album which takes a
       song as a parameter and returns the location of the song in
       the album. If the song isn't found, return -1. Use the
       song_equal function we defined earlier!

      .. tb-code:: cpp
         :name: c192_mucp_12_4_ac_q
         :caption: Example c192_mucp_12_4_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``album`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_12_4_ac_a
         :caption: Example c192_mucp_12_4_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct song {
             std::string title;
             std::string artist;
             std::size_t num_likes;
         };

         struct album {
             std::string name;
             int year;
             std::vector<song> songs;
         public:
             std::ptrdiff_t search_album(const song& a);
         };

         std::ptrdiff_t album::search_album (const song& a) {
             for (std::size_t i = 0; i < songs.size(); ++i) {
                 if ((songs[i].title == a.title && songs[i].artist == a.artist)) {
                     return static_cast<std::ptrdiff_t>(i);
                 }
             }
             return -1;
         }

.. tb-group::
   :name: c192_mucp_12_5_ac

   .. tb-tab:: Question

       What's the most popular song within an album? Let's write
       the ``album`` member function most_liked_song, which prints out
       the information of the most liked song in the format "The most
       liked song is title by artist with num_likes likes."

      .. tb-code:: cpp
         :name: c192_mucp_12_5_ac_q
         :caption: Example c192_mucp_12_5_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``album`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_12_5_ac_a
         :caption: Example c192_mucp_12_5_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>
         using std::cout;

         struct song {
             std::string title;
             std::string artist;
             std::size_t num_likes;
         };

         struct album {
             std::string name;
             int year;
             std::vector<song> songs;
         public:
             void most_liked_song();
         };

         void album::most_liked_song () {
             if (songs.empty()) { cout << "The album is empty.\n"; return; }
             std::size_t max_index = 0;
             std::size_t max_likes = 0;
             for (std::size_t i = 0; i < songs.size(); ++i) {
                 if (songs[i].num_likes > max_likes) {
                     max_index = i;
                     max_likes = songs[i].num_likes;
                 }
             }
             cout << "The most liked song is " << songs[max_index].title;
             cout << " by " << songs[max_index].artist << " with ";
             cout << songs[max_index].num_likes << " likes." << '\n';
         }

.. tb-group::
   :name: c192_mucp_12_6_ac

   .. tb-tab:: Question

       Let's write the struct definition for ``product``. ``product`` should have
       instance variables name and price.

      .. tb-code:: cpp
         :name: c192_mucp_12_6_ac_q
         :caption: Example c192_mucp_12_6_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to define the ``product`` struct.

      .. tb-code:: cpp
         :name: c192_mucp_12_6_ac_a
         :caption: Example c192_mucp_12_6_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <string>
         #include <iostream>

         struct product {
             std::string name;
             double price;
         };

.. tb-group::
   :name: c192_mucp_12_7_ac

   .. tb-tab:: Question

       Let's make a shopping list! Write the struct definition for
       ``list``, which should have instance variables type and
       a vector of Products.

      .. tb-code:: cpp
         :name: c192_mucp_12_7_ac_q
         :caption: Example c192_mucp_12_7_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to define the ``list`` struct.

      .. tb-code:: cpp
         :name: c192_mucp_12_7_ac_a
         :caption: Example c192_mucp_12_7_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <string>
         #include <iostream>
         #include <vector>

         struct product {
             std::string name;
             double price;
         };

         struct list {
             std::string type;
             std::vector<product> products;
         };

.. tb-group::
   :name: c192_mucp_12_8_ac

   .. tb-tab:: Question

       Two Products are equal if the name and price of the Products are equal.
       Write the function product_equal, which takes two Products as parameters
       and returns true if they are equal. What if we want to check to see if
       we have bananas in our shopping list? Write the list member function
       ``search_list``, which takes a product as a parameter and returns the location
       of the product in the list. Return -1 if it's not in the list.

      .. tb-code:: cpp
         :name: c192_mucp_12_8_ac_q
         :caption: Example c192_mucp_12_8_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``search_list`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_12_8_ac_a
         :caption: Example c192_mucp_12_8_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct product {
             std::string name;
             double price;
         };

         bool product_equal (const product& a, const product& b) {
             if (a.name == b.name && a.price == b.price) {
                 return true;
             }
             else {
                 return false;
             }
         }

         struct list {
             std::string type;
             std::vector<product> products;
             std::ptrdiff_t search_list(const product& a);
         };

         std::ptrdiff_t list::search_list (const product& a) {
             for (std::size_t i = 0; i < products.size(); ++i) {
                 if (product_equal (products[i], a)) {
                     return static_cast<std::ptrdiff_t>(i);
                 }
             }
             return -1;
         }

.. tb-group::
   :name: c192_mucp_12_9_ac

   .. tb-tab:: Question

       time to checkout! Write the list member function ``total_price``
       which calculates and returns the total price of all the Products.

      .. tb-code:: cpp
         :name: c192_mucp_12_9_ac_q
         :caption: Example c192_mucp_12_9_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``total_price`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_12_9_ac_a
         :caption: Example c192_mucp_12_9_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct product {
             std::string name;
             double price;
         };

         struct list {
             std::string type;
             std::vector<product> products;
         public:
             double total_price();
         };

         double list::total_price () {
             double total = 0;
             for (std::size_t i = 0; i < products.size(); ++i) {
                 total += products[i].price;
             }
             return total;
         }

.. tb-group::
   :name: c192_mucp_12_10_ac

   .. tb-tab:: Question

       Oops! We made a mistake and grabbed pineapple pizza.
       What if we want to remove an product from our list?
       Write the list member function ``remove_product``, which takes
       an index as a parameter and removes it. Then it fills
       the gap with the last product in the list.

      .. tb-code:: cpp
         :name: c192_mucp_12_10_ac_q
         :caption: Example c192_mucp_12_10_ac_q
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <iostream>
         #include <vector>
         // YOUR CODE HERE

   .. tb-tab:: Answer

       Below is one way to write the ``remove_product`` member function.

      .. tb-code:: cpp
         :name: c192_mucp_12_10_ac_a
         :caption: Example c192_mucp_12_10_ac_a
         :compileargs: ['-Wall', '-Wextra', '-std=c++20']

         #include <stdexcept>
         #include <cstddef>
         #include <string>
         #include <iostream>
         #include <vector>

         struct product {
             std::string name;
             double price;
         };

         struct list {
             std::string type;
             std::vector<product> products;
         public:
             void remove_product(std::size_t index);
         };

         void list::remove_product (std::size_t index) {
             if (index >= products.size()) throw std::out_of_range("product index");
             products[index] = products.back();
             products.pop_back();
         }

