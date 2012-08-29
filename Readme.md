Facebook Charity Demo App
==================================

This is a sample app showing use of the Facebook Graph API, written in Ruby, designed for deployment to [Heroku](http://www.heroku.com/).

Run locally
-----------

You will need [postgres](http://postgresapp.com/), [ruby 1.9](http://www.ruby-lang.org/en/downloads/) and [bundler](http://gembundler.com/) installed.

Install dependencies:

    $ bundle install

[Create an app on Facebook](https://developers.facebook.com/apps) and set the Website URL to `http://localhost:5000/`.

Copy the App ID and Secret from the Facebook app settings page into your `.env`:

    echo FACEBOOK_APP_ID=12345 >> .env
    echo FACEBOOK_SECRET=abcde >> .env

Launch the app with [Foreman](http://blog.daviddollar.org/2011/05/06/introducing-foreman.html):

    $ foreman start


To debug in the console you can run

    $ foreman run irb -r ./app.rb

You can delete votes from the console using datamapper:

    $ foreman run irb -r ./app.rb
    > Vote.last.destroy


Deploy to Heroku via Facebook integration
-----------------------------------------

The easiest way to deploy is to create an app on Facebook and click Cloud Services -> Get Started, then choose Ruby from the dropdown.  You can then `git clone` the resulting app from Heroku.

Deploy to Heroku directly
-------------------------

If you prefer to deploy yourself, push this code to a new Heroku app on the Cedar stack, then copy the App ID and Secret into your config vars:

    heroku create --stack cedar
    git push heroku master
    heroku config:add FACEBOOK_APP_ID=12345 FACEBOOK_SECRET=abcde

Enter the URL for your Heroku app into the Website URL section of the Facebook app settings page, then you can visit your app on the web.

