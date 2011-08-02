!SLIDE transition=toss

# What is SecondBase for?


!SLIDE transition=uncover center

# Managing two databases in your Rails application


!SLIDE center transition=uncover

# What about the Rails way?


!SLIDE code transition=uncover

    @@@ Ruby
    class Product < ActiveRecord::Base
      # problem solved!
      establish_connection :ids_db
    end


!SLIDE smbullets incremental transition=fade

# Or is it?

  * How do you make sure your 2nd database is set up?  
  * How do you make updates to your 2nd database?
  * How do you test code pointing to your 2nd database?
  * How do you migrate your 2nd database to other environments?
