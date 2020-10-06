# Trials and tribulations at the Flatiron School
## Moving on from the hardest thing I've ever done
#### October 2020

I'm nearing the end of my learning journey with the [Flatiron School](https://flatironschool.com/). This post details my journey: where I came from, what I learned, how I learned it, and where I am and intend to go.

## Languages
At Flatiron we learned how to read and write two popular fullstack languages: Ruby and Javascript.

### Ruby
Looking back, I think that Ruby was an effective choice in getting us to learn how to code. Because it is expressive and implicit, the code "feels" like it's doing what I, as a novice programmer, tell it to. It makes a lot of assumptions for me and you can solve a code problem in many different ways (as compared to, say, [Python](https://www.python.org/dev/peps/pep-0020/)). The Ruby community is also very large, beginner-friendly, and there is a *ton* of support out there to help you get started.

My [CLI application](https://github.com/mkopsho/dnd-companion) was written in pure Ruby and is something I'm extremely proud of. It was the first time I wrote a fully-fledged application that others could use and benefit from!

### Javascript
Transitioning to learning Javascript after Ruby was a bit of a challenge for me. Committing to memory the differences in syntax and variable/function definitions was difficult. I often found myself reverting and writing Ruby syntax in my JS programs. While it's probably cliche to mention at this point, JS is also chock-full of interesting idiosyncrasies as a result of its provenance.

However, JS -- especially with the introduction of classes in [ES6](http://es6-features.org/#ClassDefinition) -- shares a lot in common with Ruby and other OOP languages. Having to learn and become proficient in both languages showed me the commonalities and will make it easier for me to learn other languages in the future. I'm specifically interested in learning Python (as well as its frameworks [Flask](https://flask.palletsprojects.com/en/1.1.x/) and [Django](https://www.djangoproject.com/)) and [Go](https://golang.org/) post graduation.

I made [Trout Slayer!](https://github.com/mkopsho/trout-slayer) with vanilla Javascript and a Rails backend. It was a ton of fun but I hit a few novice-level snags on the way; mainly juggling the management of my own ES6 class objects as well as objects that the Google Maps API provides.

## Frameworks
We also learned how to use and write some popular web frameworks for the languages described. It seems to be a rare case to work as a software engineer and write pure code all day, instead, frameworks provide the means to creating a full web app by using their provided code.

### Sinatra
[Sinatra](http://sinatrarb.com/) is a wonderfully packaged "microframework" for Ruby that has a lot of style. While it's more configurable and relies less on conventions (as in Rails), I personally enjoyed using Sinatra for my small [Homebrew Ledger project](https://homebrew-ledger.herokuapp.com/). I'm really proud of this project. It both solved my tangible real-world problems of recipe management and is also publically available for anyone else to use! Sinatra really cemented the need for frameworks; without it, we'd need to write a yachtful of code to a yachtful of functionality that it provides out of the box (web servers, routing, template language, etc.).

### Rails
[Ruby on Rails](https://rubyonrails.org/) is a **large** framework for Ruby that's super popular, and with good reason. A lot of successful, large-scale, and load-bearing applications have used it for years to run their businesses. I made a productivity app aptly named [YAPA](https://github.com/mkopsho/yapa), AKA Yet Another Productivity App. I'm actually not at all proud of this project; I needed to allocate more time for myself to learn, re-learn, and implement foundational Rails conventions. This made it so I had no time to work on the frontend, which doesn't have any of the "normal" interactive features that a typical productivity app has (boards, drag and drop, etc.). This one needs a lot of work, but I'm still glad I made it!

### Side note on frameworks for Ruby/Python
In much the same way that Ruby is compared and contrasted to Python as modern [interpreted](https://en.wikipedia.org/wiki/Interpreted_language) languages, so too do their frameworks share strong comparisons. Ruby's Sinatra is a smaller, barebones web framework akin to Python's Flask framework, while Ruby on Rails is closer to Python's Django framework in terms of complexities and conventions.

### React
[React](https://reactjs.org/) is a large framework for Javascript that's also pretty popular, and I can see why. Splitting large JS codebases into any number of reuseable components is always a plus. Using [Redux](https://redux.js.org/) to maintain application state is also a must for any React project that uses more than a handful of components. I made [STWRDSHP](https://github.com/mkopsho/stwrdshp) with React, and I had a wonderful time doing it. I made everything with "pure" React, then refactored all of my code to use Redux and Thunk where it made sense. The refactoring was therapeutic for me because it created reuseable and "conventionalized" code that anyone could read. I love React!

### Algorithms
One of the things that my pod groups did in our regular meetings was to practice algorithms via [leetcode](https://leetcode.com/). While not part of the standard curriculum at Flatiron, the cohort leads had the freedom to introduce these to their students based on feedback from other graduates. Both algorithms and data structures are common elements of coding and are something we may get tested on during interviews.

Algorithms are **tough** for me. While working on a solution, I'm normally able to come up with *what* to do to solve, but my mind will completely blank on *how* to implement that code. I'll get doubly confused if I attempt to make the code more efficient. This is something that I need to work on and will be a mjor focus of mine in the coming months post-graduation.

## What's next for me?
Whew, we've done a lot and have come so far. But this is just the beginning of my journey. There's more work left to do.

### Job Searching
When I quit my job at [Mailchimp](https://mailchimp.com/) I budgeted enough time to take the bootcamp (~5 months) and 8 weeks to find a job. This would last me until the end of 2020, and I'd like to stick to that schedule and find a job by 2021.

Luckily, Flatiron has a thorough career services program with its own curriculum track. I am assigned a career coach and we'll work together to make me a healthy candidate for any prospective employer. This is awesome follow through and is one of the main reasons I chose to apply to Flatiron in the first place!

### Refactoring, Feature Building, and New Projects
I timeboxed myself to start and end each project within a week's time. This constraint forced me to plan out what I wanted to build, the steps to get there, and outline features that I can feasibly get done within the constraint. But, as constraints do, it limited the amount of things each of these apps can do. So, I'd like to fix that. Here's a sample of what I'd like to improve/add:

* **dnd-companion**:
    1. Created a fully-realized character and NPC generator.
    2. Use a database so that we aren't waiting too long for the API to crawl resources and instantiate an object for each one.

* **homebrew-ledger**:
    1. Add toggleable sections for the actual process of the recipe (e.g., batch or infusion sparge) and form for each of those.

* **YAPA**: 
    1. Scrap it. Seriously. Maybe I will start a new Rails productivity app from scratch that also utilizes JS to make a truly interactive (read: *normal*) productivity app.

* **Trout Slayer!**:
    1. Use JSON web tokens to properly handle user authentication and authorization.
    2. Use Google Maps API's grouping/heatmap to "glob" markers together.
    3. Perhaps some data analysis (e.g., answer questions like "what is the best lure to use in this location under these conditions?").

* **STWRDSHP**:
    1. Add more data for each national park from the NPS API.
    2. Add the ability to create more lists and drag and drop parks to/from these lists.
    3. Fully implement JWT.

I'll probably use the same approach as Flatiron when it comes to new projects: target a new language or framework that I want to learn, set up a hard time constraint to learn it, and then set up another hard time constraint to build a project with it. I'd like to explore Python, Django, and Go.

Like I said, there's more work left to do!

### Algorithms and Data Structures
As if that wasn't enough, I also feel a strong need to practice algorithms and data structures due to the aforementioned difficulty. I can use leetcode to practice algorithms vocationally, and I've signed up for [JavaScript Algorithms and Data Structures Masterclass](https://www.udemy.com/course/js-algorithms-and-data-structures-masterclass/) via Udemy.

Overall, this is one of the hardest things I've ever done. But also one of the most fulfilling and worthwhile. My journey is just beginning, and if you want to start yours, look no further than [Flatiron](https://flatironschool.com/).


[⟵   back to blog](./flatiron-blog.html)
