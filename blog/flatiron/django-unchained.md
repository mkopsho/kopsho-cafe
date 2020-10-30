# Django Unchained
## Messing with Django, GraphQL, and React
#### October 2020

## Striking Out
> `strike out`, *verb*
> 1: to enter upon a course of action
> 2: to set out vigorously

It's been about 3 weeks since I [graduated from coding bootcamp](./flatiron/trials-and-tribulations.html) and I've hit the job search hard. I'm tracking all job leads in a Trello board, using a spreadsheet to track contacts/code commits/blog posts, and leveraging Flatiron's extensive resources and my career coach to manage it all.

While job hunting is my #1 priority, I also want to keep learning and building things with a similar intensity to the bootcamp. This is hard to do as I'm not an expert in other languages or frameworks, I don't have a daily structure for learning, and I'm not even sure what to learn. It's time to strike out on my own!

Fortunately my job search was able to help guide my discipline; each listing has its own set of minimum and bonus requirements that the hiring company is looking for in a candidate. A frequent requirement that I saw was experience with a modern cloud computing platform like AWS or GCP, which spurred my purchase of the AWS Certified Solutions Architect - Associate [Udemy course](https://www.udemy.com/course/aws-certified-solutions-architect-associate/). This course is intended to equip students with the knowledge to get the associate certificate, which I intend to do.

Aside from modern cloud computing platforms, I wanted to learn more languages, frameworks, and interesting or newer ways of building technology. My collection of potential jobs covers the gamut of technology, so I figure I should at least dabble in a bunch of them while entering the field. Enter Python, Django, and GraphQL. I wanted to create a barebones Django backend which supported a React frontend and used GraphQL to ferry data back and forth.

## Django!
Django is commonly referred to as "Python's equivalent to Rails". I've already [dabbled](./flatiron/rails-the-great-humbler.html) with [Rails](./flatiron/slaying-trout-with-json.html) a [bunch](./flatiron/react-conventions-and-stewardship.html), so I felt confident in my ability to figure Django out.

And because Django has a rich community, I did just that! First of all, the Python community has many tools that help users create independent virtual environments so that their Python versions, packages, and other miscellany stay scoped to the project that they're trying to build. I decided to use [pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv):
```
pyenv virtualenv 3.6.10 django-app
pyenv activate django-app
```
If my virtual environment was appropriate activated, my terminal prompt prepends itself with the name of the current environment that I'm in. This locks my Python version to the one I created the environment with (3.6.10). This also means that any packages I install via `pip` will stay independent to that environment, which makes dependency management a breeze.

To actually start my Django app, I needed some packages:
```
pip install django==2.1.4 graphene-django==2.2.0 django-filter==2.0.0
```
We're installing [graphene](https://graphene-python.org/) here to give us a nice library to play with GraphQL in our Django app.

And, like Rails, Django provides some helpers:
```
django-admin startproject django-app
cd django-app
python manage.py migrate
python manage.py runserver
```
If you've built a Rails app before, you likely know what these do: sets up our project's file structure, runs initial database migrations, and runs a webserver!

Django has the concept of `INSTALLED_APPS`, which is a list of applications in `settings.py` that are enabled in our overall Django app. We also need to let graphene know where to find the schema.
```
INSTALLED_APPS = (
    # Default packages...
    'graphene_django',
)

...

GRAPHENE = {
    'SCHEMA': 'hackernews.schema.schema',
}
```
Django also has a Rails equivalent to [Resources](https://apidock.com/rails/ActionController/Resources/resources) simply called `apps`. We can make an `app` with the following:
```
python manage.py startapp links
```
This is very similar to Rails' resource generators in that it will provide you with some boilerplate MVC code, like `links/models.py`, `links/view.py`, etc. In order to define our `Links` model, we need to define it:
```
class Link(models.Model):
    url = models.URLField()
    description = models.TextField(blank=True)
```
This looks very similar to a Rails model definition (but a bit more verbose!).

Remember that `INSTALLED_APPS` list from before? Well, since `links` is an app, we need to add it there:
```
INSTALLED_APPS = (
    # Add after the `graphene_django` app
    'links',
)
```
And, as with every change made to our data model, we will need to migrate our database:
```
python manage.py makemigrations
python manage.py migrate
```
Whew! Now that all that setup is out of the way, let's move onto GraphQL

## Graphs!

## React!
