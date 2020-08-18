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

