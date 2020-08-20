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
* Got through [4.3.3](https://www.learnenough.com/ruby-on-rails-6th-edition-tutorial/rails_flavored_ruby/other_data_structures/hashes_and_symbols#sec-hashes_and_symbols)

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
