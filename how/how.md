!SLIDE transition=toss

# How do we use SecondBase?


!SLIDE transition=uncover 

# Use bundler

    # Update your Gemfile
    gem "secondbase"
    
    $ bundle install
    


!SLIDE transition=uncover 

# Update database.yml

    development:
      adapter: oracle_enhanced
      database: oracle.local/SID
      
    test:
      ....
      
    secondbase:
      development:
        adapter: mysql
        database: dev_db
    
      test:
        ...


!SLIDE transition=uncover 

# Create your migration

    $ rails generate secondbase:migration Products
    > create db/migrate/secondbase/201...products.rb



!SLIDE transition=uncover 

# Migrate your database

    $ rake db:create
    $ rake db:migrate


!SLIDE transition=uncover 

# Create your model
    @@@ Ruby
    require 'secondbase/model'
    
    class Product < SecondBase::Base
    end


!SLIDE transition=uncover 

# Probably a better way...
    @@@ Ruby
    require 'secondbase/model'
    
    class Ods < SecondBase::Base
      self.abstract_class = true
    end
    
    class Product < Ods
    end
    

!SLIDE transition=uncover 

# Integrate your data stores
    @@@ Ruby
    class Order < ActiveRecord::Base
      has_many :products
    end

    class Product < Ods
      belongs_to :order
    end



!SLIDE transition=fade 

# It's that simple!