Tinder Pyro
===========

A wrapper for the Tinder App API.


Installation
------------

Add this line to your application's `Gemfile`:

    gem 'tinder_pyro', '~> 0.0.1', require: 'pyro'

And then execute:

    $ bundle

Alternatively, install it via command line:

    $ gem install tinder_pyro


Getting Your oauth Token
------------------------

Before using pyro, you must grab your Facebook oauth token. Easiest way is to follow this <a href="https://www.facebook.com/dialog/oauth?client_id=464891386855067&redirect_uri=https://www.facebook.com/connect/login_success.html&scope=basic_info,email,public_profile,user_about_me,user_activities,user_birthday,user_education_history,user_friends,user_interests,user_likes,user_location,user_photos,user_relationship_details&response_type=token">link</a> and read facebook token from url you get redirected to. 

To find your facebook id simply paste into address bar: `http://graph.facebook.com/your_fb_username` and read it from json response.


Usage
-----

**Authenticating**

```ruby
FACEBOOK_ID = '547255555'
FACEBOOK_TOKEN = 'CAAGm0PX4ZCp...'

pyro = TinderPyro::Client.new
pyro.sign_in(FACEBOOK_ID, FACEBOOK_TOKEN)
```

**Interacting with users**

```ruby
# Get nearby users
pyro.get_nearby_users

user_id = '51ddbe849573ef0d12011111'

# Get a user's info
pyro.info_for_user(user_id)

# Swipe Right
pyro.like(user_id)

# Swipe Left
pyro.dislike(user_id)

# Send a saucy message
pyro.send_message(user_id, 'I luv u plz b my friend')
```

**Interacting with yourself**

```ruby
# Update your location
# Note: this request often takes around 30 seconds
latitude = 16.7758
longitude = 3.0094

pyro.update_location(latitude, longitude)

# Fetch updates (messages, likes, etc)
pyro.fetch_updates
```


Contributing
------------

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Add tests and make sure they pass
6. Create new Pull Request


Credits
-------

* [Neal Kemp](http://nealke.mp)
* [Carolyn Atterbury](http://github.com/carocaro1234) for coming up with the
  name

Copyright &copy; 2014 Neal Kemp

Released under the MIT License, which can be found in the repository in `LICENSE.txt`.
