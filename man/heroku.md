# BASIC COMMANDS
# --------------

# Installation path
(Bundle is installed into ./.bundle/gems/)

# Apps deployed
http://jteso.heroku.com/
http://aliases.heroku.com/
http://jtesoblog.heroku.com/

# Basic commands
git push heroku master 		#deploy in cloud
heroku rename <New app name> 	#change heroku app name
heroku rake db:reset
heroku rake db:migrate
heroku logs

# Example of how to set env variables (OAuth case)
heroku config:add CONSUMER_KEY=<your_consumer_key> CONSUMER_SECRET=<your_consumer_secret> CALLBACK_URL=<your_callback_url>

# How to read env variables within your code:
ENV['CONSUMER_KEY']
