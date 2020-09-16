# 30 Days of Ruby

## Purpose 

Learn and improve Ruby language skills by practicing it for 30 days

Using: https://www.railstutorial.org/book   


## Day Tracker

#### Day 1 - Aug 14

* Day 1!
* Installed RVM, Yarn, and Node.JS
* Got through [section 1.2.2 of railstutorial.org](https://www.railstutorial.org/book/beginning#sec-rails_server)

#### Day 2 - Aug 15

* Learned about models, views, routes
    * Configured `application#hello` and `application#goodbye`
* Setup deployments via Heroku cli
    * Had to install Heroku CLI
    * Had to explicitly install `git-subtree` (`sudo dnf install git-subtree`) since `hello_app` is in a sub-directory of this repo
        * [This helped a bunch](https://medium.com/@shalandy/deploy-git-subdirectory-to-heroku-ea05e95fce1f)
* Started `toy-app/`
* Setting up multiple dynos for Heroku in a single repo:
    * Rename dyno with `heroku rename`
    * Change git config and remote name
    * Push via subtree `git subtree push --prefix toy_app mencarellic-toy-app master`
* Finished up to [2.1.1](https://www.railstutorial.org/book/toy_app#sec-modeling_demo_users)

#### Day 3 - Aug 16

* Ran first migration! 
* Used `rails generate scaffold` to generate a basic users table
* Looked at the Users model and users views
* Added `microposts` table and ran migration
* Added some form validation via app models
* Edited `users` view to show microposts for each user
* Finished up to [3.0.0](https://www.railstutorial.org/book/static_pages)

#### Day 4 - Aug 17

* Created `sample_app`
* Created a `StaticPages` controller to server (mostly) static content
    * Home, About, Help, and Contact
* Starting doing tests using `rails test`
    * Test Driven Design is a method that you define the failing tests first and then write the code to make it pass
    * Wrote a test to make sure that retrieving each of the static pages return and have the proper HTML title
* Added dynamic content via ERB
* Finished through [4.0.0](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/rails_flavored_ruby)

#### Day 5 - Aug 18

* Learning Rails flavored Ruby (Basic conventions of Ruby)
* `?` is a boolean check
* `!!` forces a value to return a boolean
    * `!!nil` returns false, but everything else returns true
* `!` at the end of some methods mutates the variable it's called on:
```ruby
2.7.0 :154 > a = [1, 5, 10]
2.7.0 :155 > a.shuffle!
 => [5, 1, 10] 
2.7.0 :156 > a
 => [5, 1, 10] 
```
* Ranges: `1..5` or `('a'..'z')`
* Learned about blocks
    * `('a'..'z').to_a.map { |char| char.upcase }` and `('a'..'z').to_a.map(&:upcase)` are the same!
* Got through [4.3.3](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/rails_flavsored_ruby/other_data_structures/hashes_and_symbols#sec-hashes_and_symbols)

#### Day 6 - Aug 19

* Rails flavored Ruby, part 2
* Hashes first: `user = {}` and `user["first"] = "Carlo"`
* Symbols
    * More common than strings for hash keys
    * `user = { :first => "Carlo" }`
    * Can also use: `user = { first: "carlo" }`
* Ruby-isms:
    * `Parentheses on function calls are optional`
    * `Curly braces on final hash arguments are optional`
* Can use a named constructor:
    * `arr = Array.new([1, 2, 3])`
    * `hash = Hash.new(0)`
        * This sets 0 as a default value for nonexistent keys!
* `everything in Ruby is an object`
* `initialize` is a special ruby method that's called on `new`
* attribute accessors create getter and setter methods that allow the gets/sets of instance variables
* Finished through [5.0.0](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/filling_in_the_layout)

#### Day 7 - Aug 20

* Used the `link_to` helper to create links. 
* Learned about partials. Super easy way to piece views together.
* Finished through [5.2](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/filling_in_the_layout/sass_and_the_asset_pipeline#sec-sass_and_the_asset_pipeline)
 
#### Day 8 - Aug 21

* Asset pipeline overview uses three standard directories
    * `app/assets`
    * `lib/assets`
    * `vender/assets`
* Can use manifest files to tell Rails how to combine CSS and JS into single files
* Sass nesting and variables can help make CSS more DRY and easier to read.
* Using named routes can change from `get 'static_pages/help'` to `get '/help', to: 'static_pages#help'`
    * Lets you have clean URLs and it is easier to read
    * Drop these into the partials as the 2nd argument of the link_to functions
* Creating integration tests for the layout
    * Ideally keep these pretty simple since layouts can change, but this is really cool to make sure content that you want is always on the page.
* Got through [5.4](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/filling_in_the_layout/user_signup#sec-user_signup)

#### Day 9 - Aug 22

* Created users controller, filled in the users_path route, fixed integration and controller tests.
* Created a users models consisting of a name(string) and email(string). 
    * This is added to the DB with a migration.
    * The `rails generate` command also created a special field called 'timestamps' which creates a `created_at` and `updated_at` field
* `rails console --sandbox` - Super userful. Commands rolled back at end of session
* Create models with `User.new` and can save to a variable with `user = User.new`
* `find`, `find_by(param: "val")`, and `find_by_name("val")` are ways to search
* Can update records a few ways:
    * `user.name = "Carlo"`
    * `user.update(name: "Carlo" ....)` - Need to specify all attributes here
    * `user.update_attributes(:name, "Carlo")`
* Got through [6.2](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/modeling_users/user_validations#sec-user_validations)

#### Day 10 - Aug 23

* User validation
    * Use the `validates` method in the model to make sure the data looks like it's supposed to
    * `presence`, `length`, `format`, `uniqueness` are some of the options that can be used
* Fixtures: Sample data for database
* `has_secure_password` method
    * Ability to save `password_digest` attribute to DB
    * authenticate method that returns the user when the password is correct (and false otherwise)
    * Added via a migration to add the `password_digest` field (string)
* Got through [7.0](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/sign_up)

#### Day 11 - Aug 24

* Three types of environments in Rails: `production`, `test`, `development`
* Mixins can do bulk includes in SCSS
* Added a `Users` resource to `routes.rb`
* `debugger` is useful to drop extra details into the rails server session
* Added a gravatar helper that takes a MD5 digest of a lowercase email address and retrieves the gravatar
* Got through [7.2](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/sign_up/signup_form#sec-signup_form)

#### Day 12 - Aug 25

* Used the `form_with` method to create a new user
* `User.new` was expecting a params hash, however the base one in Rails passes in everything including potentially malicious attributes that could lead to breaches. To combat this, the practice is to specify what you're expecting and what is permitted
* Did integration testing using `assert_no_difference` to get the pre and post form submission value to ensure bad values don't result in a successful form submission
* `redirect_to` is a way to do redirects in app
* `flash` can be used to show a message. In this case after a successful signup
* Got through [8.0](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/basic_login)

#### Day 13 - Aug 26

* Create sessions controller
    * Specified specific REST actions for the routes: `GET`, `POST`, `DELETE`   
* Added 3 helpers to allow logging in, checking if a user is logged in, and what the current user id is (if it exists)
* Did some mobile styling by adding JQuery and Bootstrap via YARN.
* Got through [8.2.4](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/basic_login/logging_in/testing_layout_changes#sec-testing_layout_changes)

#### Day 14 - Aug 27

* Added first fixture, which is a way to preload the test db
    * Needed to be able to define a `password_digest` in the fixture, so this involved essentially copying the `password_digest` method from `has_secure_password`
* Added a test that logs in, follows the redirect, and checks for the presence (or absence) or specific links
* Made it so newly created users are logged in by added `reset_session` and `log_in @user` to `Users#create`
* Add a logout function by passing `reset_session` and then setting `@current_user = nil` in the sessions_controller.
* Got through [9.0](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/advanced_login)

#### Day 15 - Aug 28

* Craeted a migration to add a `remember_digest` field
* Using attr_accessors, added the token generated to the user object
* Created the cookie on login and recognized the cookie and logged user in if found and validated
* Got through [9.1.3](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/advanced_login/remember_me/forgetting_users#sec-forgetting_users)

#### Day 16 - Aug 29

* Created a checkbox for remembering a user's session
    * This creates a value in the session parameters for `remember_me`
* Adding logic in the login process to check for the value of it and setting the cookie appropriately
* Learned how to find untested code blocks by adding a `raise`. If it's untested, the tests will still pass.
* Got through [10.0](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/updating_and_deleting_users)

#### Day 17 - Aug 30

* Created the edit page
    * Added the link to the menu
* Created unsuccessful test
* Created successful test (using TDD)
* Wrote tests and got them passing to protect user edit pages from logged in and non-logged in users
* Added friendly forwards when logging in so the user should be forwarded to the URL they were trying to get to
* Got through [10.3](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/updating_and_deleting_users/showing_all_users#sec-showing_all_users)

#### Day 18 - Aug 31

* Created a user index view which shows all users when logged in
* Used the Faker gem to fake user account creation with `db/seeds.rb`
* Added the `will_paginate` gem to have multiple pages on the user index view
* Added a boolean to determine if the user is an admin
* Got through [11.0](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/account_activation)

#### Day 19 - Sep 1

* Created a `before_create` and `before_save` call to assign an activation token to a new user.
* Configured Dev to work with email previews used in ActionMailer
* Extracted the `authenticated?` method to be more generic. Allowing it to be used with `remember_digest` and `activation_digest`
* Refactored to add the `user.activate` and `user.send_activation_email` methods
* Got through [12.0](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/password_reset)

#### Day 20 - Sep 2

* Created a new controller for password resets and a migration to add a reset digest and a date/time for when it was sent
* Setup the password reset form view
* Created logic to check if the email being submitted for reset is valid
* Got through [12.2](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/password_reset/password_reset_emails#sec-password_reset_emails)

#### Day 21 - Sep 3

* Created a several methods in the password_resets_controller to update the password after it is reset.
    * Also captured some failure cases such as an empty form and expired password
* Integration tests for the password_reset
* Got through [13.0](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/user_microposts#cha-user_microposts)

#### Sep 4 - Sep 13

* Took short break during a vacation

#### Day 22 - Sep 14

* Created a new model: `microposts`
* Created a one -> has many relationship between users and microposts
* Set a default scope for the microposts to order them from most recent to oldest
* Got through [13.2](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/user_microposts/showing_microposts#sec-showing_microposts)

#### Day 23 - Sep 15

* Created a new controller for microposts. Though only used it for the `show` view
* Added micropost seed data
* Added user profile test which uses similar loop as the db seed.
  * See the use of `assert_select` and learn what `response.body` is
* Got through [13.3](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/user_microposts/manipulating_microposts#sec-manipulating_microposts)

