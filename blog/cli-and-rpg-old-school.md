# CLIs and RPGs: an old-school interface for an old-school game
#### May 2020

This is a rundown of my first project for the Flatiron School software development bootcamp. You can check out a demo of the project [here](https://www.youtube.com/watch?v=KdRx_dLqikA) and the code [here](https://github.com/mkopsho/dnd-companion).

## dnd-companion

I built a CLI application for folks who like to be the role of dungeon master in Dungeons and Dragons games but haven't committed the ruleset to memory.

The app takes and presents data from [https://www.dnd5eapi.co/](https://www.dnd5eapi.co/) to a would-be DM. I'm pretty fortunate to have found a public and complete DnD API that is [well-maintained](https://github.com/bagelbits/5e-srd-api) and has an [active community](https://github.com/bagelbits/5e-database) of folks that nurtures and maintains its accuracy.

The app itself does these high-level things:

1. Crawls the API resources of a given endpoint and parses JSON.
2. Collects attributes and instantiates DnD objects from that JSON.
3. Organizes and displays data!

## Crawling resources
When a user spins up the app, they have created a new instance of the `CLI` class, which handles all of the menu behavior. They are immediately greeted by this title card and several menu options:

![dnd-companion](../images/cli/title_card.png)

If they choose any of the menu items (except for "Exit"), a method is called which will parse the user input for the resource and tee that resource off to the appropriate class method. These methods call other methods in an `API` class that do the heavy lifting of getting API responses and parsing the JSON in those responses.

## Collecting attributes and instantiating objects
Now that we have some JSON to play with, we can start grabbing the information that we want to flesh out our object attributes. Each menu item listed above has its own class to establish a clear dilineation between objects. They also have unique attributes; for example, a single `spell` object looks like this when created:
```
=> #<Spell:0x00007fd84fa9b6c0
 @casting_time="1 action",
 @components=["V", "S", "M"],
 @concentration=false,
 @description=
  "A shimmering green arrow streaks toward a target within range and bursts in a spray of acid. Make a ranged spell at
tack against the target. On a hit, the target takes 4d4 acid damage immediately and 2d4 acid damage at the end of its next turn. On a miss, the arrow splashes the target with acid for half as much of the initial damage and no damage at the end of its next turn.",
 @duration="Instantaneous",
 @higher_level=
  ["When you cast this spell using a spell slot of 3rd level or higher, the damage (both initial and later) increases by 1d4 for each slot level above 2nd."],
 @klasses=["Wizard"],
 @level="2",
 @materials="Powdered rhubarb leaf and an adder's stomach.",
 @name="Acid Arrow",
 @range="90 feet",
 @ritual=false,
 @school="Evocation">
```
Other data -- like `equipment`, `conditions`, and `monsters` -- get their own unique attributes.

## Getting dat data!
Now, the fun part! We can look at each of these objects in a way that makes sense, like looking at spells by class *and* level:

![dnd-companion](../images/cli/spells.png)

Or equipment stats:

![dnd-companion](../images/cli/equipment.png)

Or monsters by challenge rating (CR)...:

![dnd-companion](../images/cli/monster1.png)

...and their relevant info:

![dnd-companion](../images/cli/monster2.png)

Awesome! These all get handled by the CLI class, which houses methods that iterate through the appropriate list of objects and displays the data that fits our user's criteria (and formats it too!).

## Observations had and lessons learned
### Plan, plan, plan! (and limit scope)
I spent the weekend before the project was due pondering the design of this project but never committed anything to paper, and that was probably a mistake. I had a baseline "MVP" in mind, which was to get and display information about conditions, spells, and equipment. After that was done, however, I started branching out into monsters and started a character generator. While I'm happy with the results of working on the `Monster` class, I ended up shuttering the character generator because it was very complex and I wouldn't be able to finish it in time. I spent a few hours on this when I could have been refactoring and refining my code to make it truly polished!

### Refactor, refine, and stay DRY
As I was writing code, I started to realize how repeatable a lot of this code was. I ended up writing a lot of repeated code throughout my application in the first couple of days in order to get things up and running. This approach actually worked out for me because I got my application working ASAP and was able to dedicate a good chunk of time to refactoring. Of the code I refactored, here are the highlights:
1. Building a module with class methods to extend into my other classes. [1](https://github.com/mkopsho/dnd-companion/commit/7c67470a1bbffeacb2259bd26d42b8afa5b6ef3e)
2. Writing a single method in the `CLI` class to handle object generation based on user input. [1](https://github.com/mkopsho/dnd-companion/commit/7c67470a1bbffeacb2259bd26d42b8afa5b6ef3e)
3. Converting all occurrences of empty array declaration + .each to .map. [1](https://github.com/mkopsho/dnd-companion/commit/ba44386693d744c6103c0e3df036b5afe9db38c2) [2](https://github.com/mkopsho/dnd-companion/commit/4f6f2842091675d383c7a027f69b89e6b2217b3e)
4. Using `send` to automatically assign instance variables and object attributes on initialize. [1](https://github.com/mkopsho/dnd-companion/commit/b706424a624bea52a1304dfab1b1bd9c8cd2ac1f)

Refactoring was a surprisingly peaceful process that I thoroughly enjoyed!

[⟵   back to blog](./flatiron-blog.html)
