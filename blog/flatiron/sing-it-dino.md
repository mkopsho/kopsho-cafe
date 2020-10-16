# Sing it, Dino! Sinatra and the King of Cool
#### June 2020

![dino-sinatra](../images/sinatra/dino_sinatra.jpg)

This is a rundown of my second project for the Flatiron School software development bootcamp. You can check out a demo of the project [here](https://www.youtube.com/watch?v=o2BMZ_qS2Nc) and the code [here](https://github.com/mkopsho/homebrew-ledger).

## homebrew-ledger

I like to homebrew beer in my free time. It's a deep and productive hobby which I really enjoy. What I *don't* enjoy, however, is keeping track of all of my recipes! I typically go the old-school pen-and-paper route, which leads to messy bookkeeping.

In comes [homebrew-ledger](https://github.com/mkopsho/homebrew-ledger)! It's a small web app built with the lightweight [Sinatra](http://sinatrarb.com/) Ruby framework. homebrew-ledger is meant to store, track, and share homebrew recipes. It can be used either publically or privately!

## Stubbenville, OH
So, I learned my lesson from [last project](../blog/cli-and-rpg-old-school.html) and actually wrote down the low-level design of my project as I was mulling it over last weekend! Huzzah!

![chicken-scratch](../images/sinatra/chicken-scratch.jpg)

This definitely isn't a ton of design notes, but it really helped me to kickstart the progress that I made the following Monday. I was able to stub out the entire project and had a working app within a day. Momentous!

## Challenges
I had a tad of difficulty staying on-task and focusing on the project requirements **first**. It was very easy for me to look at my app and immediately want to do one of two things:
1. Make it pretty,
2. Build more features.

This is because A) newborn Sinatra app deals in raw HTML, which ain't pretty, and B) a useable web app should be chock full of "stuff", right?

![nastay](../images/sinatra/bleh.png)

Well, not really. It was made abundantly clear to me *why* we were told to focus on proper ActiveRecord associations, building RESTful routes, and user authentication/authorization *first*: they are essential building blocks to *any* web application. Without them, you don't really have a web app. Well, at least one that people would want to use!

## Lessons learned
Having my routes and authentication/helper methods in place *first* built a foundation that presented a user with consistent app behavior. I could then build on top of that foundation to make the user interface/experience nicer. Ratpack style.

For example, the `sinatra-flash` gem allows use of a `flash` hash that we can save messages to. In my `/login` route, I check to see if the user exists and if the user can `authenticate` (a method given to us by the `bcrypt` gem). If not, we save a message to our flash hash and present that message to the user in the associated view:

![auth](../images/sinatra/flash_message.png)

Another thing I learned was the power of `<label for= >` tag in forms. When I first learned about it, I didn't actually understand what it was doing and so I thought that it could be ignored. I wrote all of my forms without this tag. I ended up doing some research about the tag, and read that it is important for accessibility (and a very low effort to implement). It makes the form targets bigger!

Overall, I really enjoy Sinatra. It seems like a great framework to learn web apps on. I'm even more excited for Rails now!

[⟵   back to blog](./blog-home.html)
