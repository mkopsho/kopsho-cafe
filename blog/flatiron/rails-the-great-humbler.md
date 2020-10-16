# Hark, Rails! The Great Humbler!
#### July 2020

![me_irl](../../images/rails/buster_keaton_rails.gif)

This post details my third project for the Flatiron School software development bootcamp. It was primarily written in Rails. You can check out the code [here](https://github.com/mkopsho/yapa).

## YAPA: Yet Another Productivity App

Thinking of coding project is hard. Very hard. Normally, if I know I have a project week coming up, I will spend the week or so before building a mental list of project ideas. Then I'll pick one the weekend preceding project week and start to design the app in my head.

![also_me_irl](../../images/rails/idea_manatee.gif)

This time, the well was dry. Very dry. I tried to source ideas from friends and family, which I have compiled [here](https://trello.com/b/ID33C6vC/code-project-ideas), but most of them felt too "big" to get done within a week's time.

Enter YAPA. I have a background in people and project management, and one of the major pieces of those roles is productivity and collaboration tools. I decided to build one!

## Models and generators and bears, oh my!

My sequential plan of attack started off simply:
1. Build model relationships,
2. Build user singup/login/logout,
3. Build RESTful routes (and actions, and views) for my models,
4. Build permissions checks for resources,
5. Refactor with helper methods and form partials,
6. Frontend stuffs!

The goal was to make sure that I get the foundational stuff right *first* so that I don't run into issues down the road. Models are a big part of this strategy; if models and their relationships are planned out first, the app will accommodate and design itself around the models.

One of the things that both impressed and kind of worried me was just how much *stuff* the Rails helpers give you:

```
~/git // ● > rails new rails-app
      create  
      create  README.md
      create  Rakefile
      create  .ruby-version
      create  config.ru
      create  .gitignore
      create  Gemfile
         run  git init from "."
Initialized empty Git repository in /Users/michaelkopsho/git/rails-app/.git/
      create  package.json
      create  app
      create  app/assets/config/manifest.js
      create  app/assets/stylesheets/application.css
      create  app/channels/application_cable/channel.rb
      create  app/channels/application_cable/connection.rb
      create  app/controllers/application_controller.rb
      create  app/helpers/application_helper.rb
      create  app/javascript/channels/consumer.js
      create  app/javascript/channels/index.js
      create  app/javascript/packs/application.js
      create  app/jobs/application_job.rb
      create  app/mailers/application_mailer.rb
      create  app/models/application_record.rb
      create  app/views/layouts/application.html.erb
      create  app/views/layouts/mailer.html.erb
      create  app/views/layouts/mailer.text.erb
      create  app/assets/images
      create  app/assets/images/.keep
      create  app/controllers/concerns/.keep
      create  app/models/concerns/.keep
      ...
```

This is just a portion of the `rails new` output; there were plenty of other directories and files created and many gems installed. This is awesome in two ways: it makes a developer's job easier, but it's also a vast amount of code that you may or may not be using in your app! 

Rails generators also express this awesome duality:
```
~/git/rails-app // ● > rails g resource User username:string email:string
Running via Spring preloader in process 46868
      invoke  active_record
      create    db/migrate/20200801163459_create_users.rb
      create    app/models/user.rb
      invoke    test_unit
      create      test/models/user_test.rb
      create      test/fixtures/users.yml
      invoke  controller
      create    app/controllers/users_controller.rb
      invoke    erb
      create      app/views/users
      invoke    test_unit
      create      test/controllers/users_controller_test.rb
      invoke    helper
      create      app/helpers/users_helper.rb
      invoke      test_unit
      invoke    assets
      invoke      scss
      create        app/assets/stylesheets/users.scss
      invoke  resource_route
       route    resources :users
```

This relatively simple command gave us a migration file (with a `users` table, the columns we specified, and their datatypes), a `User` model, a `User` controller, and a `users` directory where we can put our related view files.

It also built some a helper file, some test files, and part of the Rails asset pipeline. This is a lot of helpful stuff! Conversely, a lot of these files were not used in the final version of the app.

## Challenges and lessons learned

One of the major challenges I faced was trying to keep the design of my app in my head as I was working. Rails is the most complex coding framework that I've dealt with so far, and knowing where things lived and what tools were available to me was half the battle. 

I felt like I spent more time reading Rails documentation than churning out Ruby code. This is probably a good thing considering Rails' philosophy of [convention over configuration](https://en.wikipedia.org/wiki/Convention_over_configuration), but learning a framework's conventions is almost as complicated learning an entirely new coding language at times.

One of the things that I can do in the future is to fully embrace the concept of a low-fidelity wireframe and sketch out major parts of the app, including but not limited to:
* Model/table relationships,
* User "flow" through the app,
* The design of specific views and access to nested resources.

I think the above wireframe would have helped to solidify concepts earlier in the project and would have saved me a bit of time when jumping from concept to concept!

## They can't all be winners

Overall, I'm content with how my project turned out. I don't think many people would use it over, say, Trello or Asana or any of the multitude of productivity apps on the market, but I'm still glad to have built it. I learned a lot about Rails conventions and how to to build a bona fide web app with the framework. As with all of my projects, I would like to revisit the app in the future to further refine and refactor, and maybe make it more useful. Thanks for reading!

[⟵   back to blog](./blog-home.html)
