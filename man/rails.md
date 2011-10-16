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

bundle install   # executes the Gemfile (install all required gems)
annotate         # annotate all our models

rails console --sandobox # Modification in DB will be rolled back on exit
rails console <enviroment> #enviroment=[test|development|production]
