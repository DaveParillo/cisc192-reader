Mixed Up Code Practice
----------------------

.. tb-parsons::
   :name: c192_mucp_12_1
   :no-indent:

   Let's write the struct definition for song. song should have
   instance variables title, artist, and num_likes. Put the necessary
   blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      struct song {
      {{endgroup}}
      {{distractor}}
      {{group}}
      Struct song {  #distractor
      {{endgroup}}
      {{group}}
         std::string title;
      {{endgroup}}
      {{group}}
         std::string artist;
      {{endgroup}}
      {{group}}
         std::size_t num_likes;
      {{endgroup}}
      {{group}}
      };
      {{endgroup}}
      {{distractor}}
      {{group}}
      }  #distractor
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_12_2
   :no-indent:

   Let's make an album! Write the struct definition for
   album, which should have instance variables name, year and
   a vector of Songs. Put the necessary
   blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      struct album {
      {{endgroup}}
      {{distractor}}
      {{group}}
      std::string album {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::string title;  #distractor
      {{endgroup}}
      {{group}}
         std::string name;
      {{endgroup}}
      {{group}}
         int year;
      {{endgroup}}
      {{distractor}}
      {{group}}
         song song;  #distractor
      {{endgroup}}
      {{group}}
         std::vector<song> songs;
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::vector<string> song;  #distractor
      {{endgroup}}
      {{group}}
      };
      {{endgroup}}
      {{distractor}}
      {{group}}
      }  #distractor
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_12_3
   :no-indent:

   Two Songs are equal if the title and artist of the Songs are equal.
   Write the function song_equal, which takes two Songs as parameters
   and returns true if they are equal. Put the necessary
   blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      bool song_equal (const song& a, const &song b) {
      {{endgroup}}
      {{distractor}}
      {{group}}
      bool song_equal (song const &a, song const &b) {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
      bool song::song_equal (const song& song) {  #distractor
      {{endgroup}}
      {{group}}
         if (a.title == b.title && a.artist == b.artist) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         if (title == b.title && artist == b.artist) {  #distractor
      {{endgroup}}
      {{group}}
            return true;
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         else {
      {{endgroup}}
      {{group}}
            return false;
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_12_4

   What if we'd like to search an album for our favorite song?
   Write the album member function search_album which takes a
   song as a parameter and returns the location of the song in
   the album. If the song isn't found, return -1. Use the
   song_equal function we defined earlier! Put the necessary
   blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      std::ptrdiff_t album::search_album (const song& a) {
      {{endgroup}}
      {{distractor}}
      {{group}}
      std::ptrdiff_t search_album (const album& album, const song& a) {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
      bool search_album (song const &a) {  #distractor
      {{endgroup}}
      {{group}}
         for (std::size_t i = 0; i < songs.size(); ++i) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         for (std::size_t i = 0; i < album.size(); ++i) {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         for (std::size_t i = 0; i < song.size(); ++i) {  #distractor
      {{endgroup}}
      {{group}}
            if (song_equal (songs[i], a)) {
      {{endgroup}}
      {{distractor}}
      {{group}}
            if (songs[i] == a) {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
            if (album.song == a) {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
            if (song[i] == a) {  #distractor
      {{endgroup}}
      {{group}}
               return static_cast<std::ptrdiff_t>(i);
      {{endgroup}}
      {{distractor}}
      {{group}}
               return true;  #distractor
      {{endgroup}}
      {{group}}
            }
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         return -1;
      {{endgroup}}
      {{distractor}}
      {{group}}
         return false;  #distractor
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_12_5

   What's the most popular song within an album? Let's write
   the album member function most_liked_song, which prints out
   the information of the most liked song in the format "The most
   liked song is title by artist with num_likes likes." Put the necessary
   blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      void album::most_liked_song () {
      {{endgroup}}
      {{distractor}}
      {{group}}
      int album::most_liked_song () {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
      void album::most_liked_song (const song& a) {  #distractor
      {{endgroup}}
      {{group}}
         std::size_t max_index = 0;
      {{endgroup}}
      {{group}}
         std::size_t max_likes = 0;
      {{endgroup}}
      {{group}}
         for (std::size_t i = 0; i < songs.size(); ++i) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         for (std::size_t i = 0; i < album.size(); ++i) {  #distractor
      {{endgroup}}
      {{group}}
            if (songs[i].num_likes > max_likes) {
      {{endgroup}}
      {{group}}
               max_index = i;
      {{endgroup}}
      {{group}}
               max_likes = songs[i].num_likes;
      {{endgroup}}
      {{distractor}}
      {{group}}
               i = max_likes;  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
               max_likes = num_likes;  #distractor
      {{endgroup}}
      {{group}}
            }
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         std::cout << "The most liked song is " << songs[max_index].title;
      {{endgroup}}
      {{group}}
         std::cout << " by " << songs[max_index].artist << " with ";
      {{endgroup}}
      {{group}}
         std::cout << songs[max_index].num_likes << " likes." << std::endl;
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_12_6

   Let's write the struct definition for product. product should have
   instance variables name and price. Put the necessary
   blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      struct product {
      {{endgroup}}
      {{distractor}}
      {{group}}
      struct product {  #distractor
      {{endgroup}}
      {{group}}
         std::string name;
      {{endgroup}}
      {{group}}
         double price;
      {{endgroup}}
      {{distractor}}
      {{group}}
         int price;  #distractor
      {{endgroup}}
      {{group}}
      };
      {{endgroup}}
      {{distractor}}
      {{group}}
      }  #distractor
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_12_7

   Let's make a shopping list! Write the struct definition for
   list, which should have instance variables type and
   a vector of Products. Put the necessary
   blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      struct list {
      {{endgroup}}
      {{distractor}}
      {{group}}
      Struct list {  #distractor
      {{endgroup}}
      {{group}}
         std::string type;
      {{endgroup}}
      {{distractor}}
      {{group}}
         product type;  #distractor
      {{endgroup}}
      {{group}}
         std::vector<product> products;
      {{endgroup}}
      {{distractor}}
      {{group}}
         std::vector<> product;  #distractor
      {{endgroup}}
      {{group}}
      };
      {{endgroup}}
      {{distractor}}
      {{group}}
      }  #distractor
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_12_8

   Two Products are equal if the name and price of the Products are equal.
   Write the function product_equal, which takes two Products as parameters
   and returns true if they are equal. What if we want to check to see if
   we have bananas in our shopping list? Write the list member function
   search_list, which takes a product as a parameter and returns the location
   of the product in the list. Return -1 if it's not in the list. Put the necessary
   blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      bool product_equal (const product& a, const &product b) {
      {{endgroup}}
      {{distractor}}
      {{group}}
      bool product_equal (product const &a, product const &b) {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         if (a.name == b.name) {  #distractor
      {{endgroup}}
      {{group}}
         if (a.name == b.name && a.price == b.price) {
      {{endgroup}}
      {{group}}
            return true;
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         else {
      {{endgroup}}
      {{group}}
            return false;
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}
      {{group}}
      std::ptrdiff_t list::search_list (const product& a) {
      {{endgroup}}
      {{distractor}}
      {{group}}
      std::ptrdiff_t search_list (const product& a) {  #distractor
      {{endgroup}}
      {{group}}
         for (std::size_t i = 0; i < products.size(); ++i) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         for (std::size_t i = 0; i < num_products; ++i) {  #distractor
      {{endgroup}}
      {{group}}
            if (product_equal (products[i], a)) {
      {{endgroup}}
      {{distractor}}
      {{group}}
            if (album.song == a) {  #distractor
      {{endgroup}}
      {{group}}
               return static_cast<std::ptrdiff_t>(i);
      {{endgroup}}
      {{group}}
            }
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         return -1;
      {{endgroup}}
      {{distractor}}
      {{group}}
         return 1;  #distractor
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_12_9

   Time to checkout! Write the list member function total_price
   which calculates and returns the total price of all the Products.
   Put the necessary blocks of code in the correct order.

   .. code-block:: c++

      {{group}}
      double list::total_price () {
      {{endgroup}}
      {{distractor}}
      {{group}}
      double list : total_price () {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
      int total_price () {  #distractor
      {{endgroup}}
      {{group}}
         double total = 0;
      {{endgroup}}
      {{distractor}}
      {{group}}
         double total;
      {{endgroup}}
      {{group}}
         for (std::size_t i = 0; i < products.size(); ++i) {
      {{endgroup}}
      {{distractor}}
      {{group}}
         for (double i = 0; i < products.size(); ++i) {  #distractor
      {{endgroup}}
      {{distractor}}
      {{group}}
         for (std::size_t i = 0; i > products.size(); ++i) {  #distractor
      {{endgroup}}
      {{group}}
            total += products[i].price;
      {{endgroup}}
      {{distractor}}
      {{group}}
            total += products.price;
      {{endgroup}}
      {{group}}
         }
      {{endgroup}}
      {{group}}
         return total;
      {{endgroup}}
      {{group}}
      }
      {{endgroup}}

.. tb-parsons::
   :name: c192_mucp_12_10

   Remove the product at index, filling its position with the last product. Reject an invalid index. The order of the remaining products need not be preserved.

   .. code-block:: c++

      {{group}}
      void list::remove_product(std::size_t index) {
      {{endgroup}}
      {{group}}
          if (index >= products.size()) throw std::out_of_range("product index");
      {{endgroup}}
      {{group}}
          products[index] = products.back();
      {{endgroup}}
      {{group}}
          products.pop_back();
      }
      {{endgroup}}

