# ==============
# BASIC COMMANDS
# ==============

rails new Application
rails generate controller Users new
rails generate model User name:string email:string
rails server --environment production
rails generate rspec:install # Tell Rails to use RSpec in place of Test::Unit

(db/migration/*.rb)
rake db:migrate  # migrating up   - Executes self.up
rake db:rollback # migrating down - Executes self.down
rake db:test:prepare # development.sqlite3 is reflected in the test.sqlite3
rake db:migrate RAILS_ENV=production # create a production DB
rake db:reset # remove all records inserted in DB
rake test # Run your tests
rake db:seed # Populate your seed data in your DB



bundle install   # executes the Gemfile (install all required gems)
annotate         # annotate all our models

rails console --sandobox # Modification in DB will be rolled back on exit
rails console <enviroment> #enviroment=[test|development|production]

# Rails Environments and Configuration

- Environment dictated according with variable RAILS_ENV (SEE ALSO: RACK_ENV)
- According with value in RAILS_ENV, the file /config/environment/#{RAILS_ENV}.rb will be loaded.
- Gemfile sintaxis:
  group :test do
    gem "rspec"
    gem "faker"
  end

  grup :development, :test do
    ... more gems here
  end
- Commands:
    - bundle install
    - bundle package (package up all your gems in the vendor/cache directory inside your rails app) 

- Use 'rails console' to see how the pluralize works, for example:
  > ActiveSupport::Inflector.pluralize "project"
  > "pensum".pluralize # Inflector features are mixed into String by default.

- 'config.cache_classes = false (will use 'load' which it will not cache the classes). 
- 'config.cache_classes = true (will use 'require' which it makes use of the cache for classes)

- If problems to load a class is found, go to console (rails console)
  and type:
 > $LOAD_PATH #to see the routes that rails use for Rails class loader
  Note: you will require this files manually, otherwise put them in the autoload_paths in config/application.rb 
  for automatic loading.

- Auto loading code in Rails by examples:
   EstimationCalculator becomes 'require "estimation_calculator" '
  MacGyver::SwissArmyKnife becomes 'require "mac_gyver/swiss_arby_knife,in other words Rails will expect to find a swiss_army_knife.rb file in
the foldoer mac_gyver somewhere in the ruby's load path (app subdirs, lib or plugin lib).

- Rails log files: 
  > rake log:clear # Truncates al the log files in log/ to zero bytes
  > tail -f log/development log # Tip





