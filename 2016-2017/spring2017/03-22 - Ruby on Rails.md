### Back-End Web Development with Ruby on Rails

#### ACM Meeting Agenda — March 22, 2017

***
<div id="announcements"></div>

##### Announcements

- **Programming Competition** - next week!

***
<div id="setup"></div>

##### Setup

- Go to [RailsInstaller.org](http://railsinstaller.org/en) and download the relevant installer for your operating system. Run the installer.

***
<div id="briefintro"></div>

##### A Brief Introduction to Ruby and Ruby on Rails

- **Ruby** is a programming language designed to be fairly intuitive and very readable for humans.

    - "Hello World!" in Java:
    ```java
    public class Hello
    {
        public static void main(String[] args)
        {
            System.out.println("Hello World!");
        }
    }
    ```

    - "Hello World!" in Ruby:
    ```ruby
    puts "Hello World!"
    ```

- **Rails** is a *framework* for Ruby to make back-end web development -- applications running on servers -- far easier.

    - Rails has three core tenets for development:

        1. *Don't Repeat Yourself* - [By not writing the same information over and over again, our code is more maintainable, more extensible, and less buggy.](http://guides.rubyonrails.org/getting_started.html)

        2. *Convention over Configuration* - [Rails is opinionated software. It makes the assumption that there is a "best" way to do things, and it's designed to encourage that way - and in some cases to discourage alternatives.](http://guides.rubyonrails.org/getting_started.html)

        3. *Model-View-Controller Architecture*  - the internal states of the program (**model**), the program display (**view**), and the program interface (**controller**) should have an enforced separation between them

- Ruby is open-source and enjoys enthusiastic support from a large community.

    - This means solutions to almost any problem you may have can be found online.

    - It also means a wide variety of **gems** - the Ruby equivalent of packages - can be found to fit your needs.

***
<div id="rubyintro"></div>

##### Introduction to Programming in Ruby

- Ruby is a high-level, object-oriented programming language.

- Ruby's variables, [much like JavaScript's](https://github.com/OKStateACM/meetingnotes/blob/master/2017-02-22%20-%20agenda.md), are dynamically-typed. Creating variables is easy.
    ```ruby
    foo = 20
    bar = "Hello World"
    ```

- Ruby doesn't use braces for codeblocks like Java or C, and nor is it whitespace-sensitive like Python. Rather, codeblocks start with a line like a method header or an `if` statement and end with an `end` statement.
    ```ruby
    # if statements
    if user_num < 0
        puts "You picked a negative integer!"
        puts "Why would you do that?"
    elsif user_num > 0
        puts "You picked a positive integer!"
        puts "Congrats!"
    else
        puts "You picked zero!"
        puts "ಠ_ಠ"
    end
    ```

- To create a method called `my_method` in Ruby, you would use the following code.
    ```ruby
    def my_first_method
        # Ruby code goes here
    end
    ```

    - Alternatively, if you need parameters like `name` and `age`...
        ```ruby
        def my_second_method(name, age)
            # Ruby code goes here
        end
        ```

    - Calling your method works familiarly. Call `my_second_method()` with the following code:
        ```ruby
        my_second_method("Pistol Pete", 21)
        ```

        - If, as in `my_first_method()`, you don't have any parameters, parentheses are optional:
            ```ruby
            my_first_method
            # ... works the same as ...
            my_first_method()
            ```

- As Ruby is object-oriented, you can create classes:
    ```ruby
    class Student
        # class variables -- think of Java's static variables -- are denoted by "@@"
        @@species = "human"

        # initialize() is Student's constructor
        def initialize(name, school, gpa)
            # the "@" makes these variables *instance variables*...
            # ...they'll be accessible to all methods of the instance of this class
            @name = name
            @school = school
            @gpa = gpa
        end

        def graduate
            # Ruby code goes here
        end

        def flunk
            # Ruby code goes here
        end
    end
    ```

    - You can now construct an instance of `Student` like so:
        ```ruby
        pistol_pete = Student.new("Pistol Pete", "Oklahoma State University", 4.0)
        ```

- Finally, everything in Ruby is an object... even data literals.

    - You can get the length of a string literal, for instance, by calling
        ```ruby
        "Hello".length
        ```

    - This is also exploited in a kind of for-loop present in Ruby: `.times`:
        ```ruby
        # The following code prints "Hello!" five times
        5.times do
            puts "Hello!"
        end
        ```

        - Ruby does have other loops, but they're fairly standard and easy to research.

***
<div id="firstrailsapp"></div>

##### Creating Your First Rails Application


- Create a brand new folder for your application and name it `rubytut`.

- In your newly Ruby-enabled terminal (for Windows users, this will be a new Command Prompt program called `Command Prompt with Ruby and Rails`), navigate into your `rubytut` folder.

- Inside `rubytut`, we'll create our first Rails app, called `first_app`, using the command `rails new first_app`. This will likely take a bit.

    - If we had wanted to create a Rails app using a specific version of Rails, like 5.0.1 for instance, we could have used `rails _5.0.1_ new first_app`.

    - If you're getting a "The system cannot find the path specified" error, [here's the fix](http://stackoverflow.com/a/35730896).

- Rails has now created a whole directory for `first_app`.
```
└───first_app
    ├───app                         # Core app components
    │   ├───assets
    │   │   ├───config
    │   │   ├───images
    │   │   ├───javascripts
    │   │   │   └───channels
    │   │   └───stylesheets
    │   ├───channels
    │   │   └───application_cable
    │   ├───controllers
    │   │   └───concerns
    │   ├───helpers
    │   ├───jobs
    │   ├───mailers
    │   ├───models
    │   │   └───concerns
    │   └───views
    │       └───layouts
    ├───bin                         # Binary executables
    ├───config                      # App configuration
    │   ├───environments
    │   ├───initializers
    │   └───locales
    ├───db                          # Database files
    ├───lib                         # Non-vendor libraries
    │   ├───assets
    │   └───tasks
    ├───log                         # App log files
    ├───public                      # Files accessible to public
    ├───test                        # App tests
    │   ├───controllers
    │   ├───fixtures
    │   │   └───files
    │   ├───helpers
    │   ├───integration
    │   ├───mailers
    │   └───models
    ├───tmp                         # Temporary files
    │   └───cache
    │       └───assets
    ├───vendor                      # Third-party code such as plugins and gems
    │   └───assets
    │       ├───javascripts
    │       └───stylesheets
    ├───.gitignore
    ├───config.ru
    ├───Gemfile                     # App's gem dependencies
    ├───Gemfile.lock                # Specific versions of dependencies used
    ├───Rakefile
    └───README.md
```

- Rails also makes it really easy to host a Rails server locally to run our application. While inside your `first_app` directory, call the `rails server` command.

    - Your server should now be running at `localhost:3000` (3000 is the default port for Rails applications). You can navigate to [localhost:3000](http://localhost:3000) in your web browser to see your application's default landing page.

- We're going to make `first_app` into a commenting platform. This webapp will contain two kinds of objects: users and comments. We'll start with creating user functionality. To do this, we'll need an internal representation (**model**) of a user, as well as a database to store users in. For our purposes, users will have a string field (`name`) for the user's name and a string field (`email`) for the user's email address. Rails, being a framework designed for back-end development, allows you to easily generate the back-end code to make this happen using a technique called *scaffolding*. In your application's folder, call the following line to scaffold your comment model and database into existence:
    ```bash
    rails generate scaffold User name:string email:string
    ```

    - This should generate:

        1. Model: `\app\models\user.rb` -- the class representation of a user

        2. Controller: `\app\controllers\user_controller.rb` -- the user manager (in other words, the program that bosses around the user models and databases)

        3. View: `\app\views\users` -- web interface for users

            - Rails employs *Embedded Ruby* (or *eRuby*), which infuses Ruby into text files, namely HTML files. This is how visiting the same webpage on webapps like Twitter will show personalized content for different users. The `.html.erb` files in this folder are Ruby-enabled HTML webpages.

        4. Several files in the `\db` folder which facilitate database management for storing users.

- Call `rails db:migrate` to make our new database go live. In general, you'll want to call this whenever you update your database to sync it with the live version.

- We can already view our handiwork online! Run your local server with `rails server`. If you visit `localhost:3000/users`, you'll see your new Comments page. Trying creating a user!

***
<div id="mvc"></div>

##### Model-View-Controller Architecture

> Rails is built around the [model-view-controller](https://betterexplained.com/articles/intermediate-rails-understanding-models-views-and-controllers/) pattern. It’s a simple concept: separate the data, logic, and display layers of your program. This lets you split functionality cleanly, just like having separate HTML, CSS and JavaScript files prevents your code from mushing together. Here’s the MVC breakdown:
> * __Models__ _[which, in MVC, are typically the program's data, state, and logic]_ are classes that talk to the database. You find, create and save models, so you don’t (usually) have to write SQL. Rails has a class to handle the magic of saving to a database when a model is updated.
> * __Controllers__ take user input (like a URL) and decide what to do (show a page, order an item, post a comment). They may initially have business logic, like finding the right models or changing data. As your Rails ninjitsu improves, constantly refactor and move business logic into the model ([fat model, skinny controller](http://weblog.jamisbuck.org/2006/10/18/skinny-controller-fat-model)). Ideally, controllers just take inputs, call model methods, and pass outputs to the view (including error messages).
> * __Views__ display the output, usually HTML. They use ERB and this part of Rails is like PHP – you use HTML templates with some Ruby variables thrown in. Rails also makes it easy to create views as XML (for web services/RSS feeds) or JSON (for AJAX calls).
> The MVC pattern is key to building a readable, maintainable and easily-updateable web app.

<sup>--[Starting Ruby on Rails: What I Wish I Knew │ BetterExplained](https://betterexplained.com/articles/starting-ruby-on-rails-what-i-wish-i-knew/)</sup>

***
<div id="commenting"></div>

##### Adding Commenting Functionality to Our Webapp

- Simply having users does not a commenting platform make, so let's scaffold commenting functionality into existence. Our comments will have two components: longer-form text forming the body of the comment (`content`) and an integer ID pertaining to the user that posted the comment (`user_id`).
    ```bash
    rails generate scaffold Comment content:text user_id:integer
    ```

- Since we have a new database that has yet to go live, call `rails db:migrate` again.

- Now we want to link users and comments internally. The relationship between these two is that one user *has many* comments, and a comment *belongs to* a user. To link these two, we'll need to modify the User and Comment models.

    - In `app/models/user.rb`:
        ```ruby
        class User < ApplicationRecord
            has_many :comments
        end
        ```

    - In `app/models/comment.rb`:
        ```ruby
        class Comment < ApplicationRecord
            belongs_to :user
        end
        ```

- Our user models/database and comment models/database are now linked behind the scenes. Unfortunately, this doesn't change anything in our view yet, so this change isn't observable until you modify your view to show a user's comments, something which is outside of the scope of today's meeting.

- How exactly does the controller get the user input to know when and how to boss around the model? Rails uses **routing**, or mapping requests from the browser (visiting a URL or clicking a link) to controllers or controller actions (Ruby methods inside of Rails controllers). Routing is done by a program in your application called the **router**.

    - Let's do some simple routing and redirect the homepage (or **root**), which for us is `localhost:3000`, to be the Users page. Change your `config/routes.rb` file to read
        ```ruby
        Rails.application.routes.draw do
            resources :comments
            resources :users
            root 'users#index'
        end
        ```

        - This points the `root` route (the homepage) towards the `index` action of the User controller. If you open `app/controllers/user_controller.rb`, you can find the `index` action, which returns a list of all users:
            ```ruby
            # GET /users
            # GET /users.json
            def index
                @users = User.all
            end
            ```

***
<div id="gems"></div>

##### Using Gems

- In Ruby, **gems** are libraries created to make doing jobs easier. Rails is one example of a gem.

- Gems are hosted on [RubyGems.org](https://rubygems.org).

- We can use the [*Simple Calendar*](https://github.com/excid3/simple_calendar) gem to render a monthly calendar on our site:

    1. *Modify the Gemfile*: The **Gemfile** is a list of all gem dependencies we want our app to have. Open `Gemfile` and add this line to the bottom:
        ```ruby
        gem "simple_calendar", "~> 2.0"
        ```

        - This tells our project that we want the `simple_calendar` gem. The squiggly arrow (`~>`) tells our project we want version 2.0 of the gem *at least*, but also we won't accept versions 3.0 or above.

    2. *Run Bundler*: **Bundler** is a gem that came preinstalled with the Rails Installer. Its job is to fetch and install all gems used in the project, including the gems' own dependencies. To run Bundler, call
        ```bash
        bundle install
        ```

    3. *Create the calendar page*: This itself contains several steps.

        1. *Controller*: We need a controller to parse a user's request to view the calendar. We *could* create a brand new controller, but that's a little overkill for this purpose, so we'll just adapt the application controller. Change your `app/controllers/application_controller.rb`, to reflect the following:
            ```ruby
            class ApplicationController < ActionController::Base
                protect_from_forgery with: :exception

                def calendar
                end
            end
            ```

        2. *View*: Let's now create a view for our Calendar page. ApplicationController expects that its views will be in `app/controllers/application`, so you'll need to create that folder. Inside that folder, create a new file called `calendar.html.erb`. In that file, put the following code, made possible by the *Simple Calendar* gem:
            ```html
            <%= month_calendar do |date| %>
                <%= date %>
            <% end %>
            ```

        3. *Routing*: We want people to be able to access our calendar view at `/calendar`. In your `config/routes.rb` file, add the following line:
            ```ruby
            get '/calendar' => 'application#calendar'
            ```
- You can now access your calendar at `localhost:3000/calendar`.

***
<div id="resources"></div>

##### Further Resources

- This meeting plan is indebted to Michael Hartl's *[Ruby on Rails Tutorial: Learn Web Development with Rails](https://www.railstutorial.org/book)*
