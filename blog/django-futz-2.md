# Django Futz pt.2
## Messing with Django, GraphQL, and React
#### November 2020

Welcome back! In [part 1 of this series](./django-futz-1.html), we set up a totally new Django app with all of its dependencies, the `graphene-django` package, a data model, and some dummy data to play around with. In this post, we'll be going through some basic [GraphQL](https://graphql.org/) functionality by comparing it with REST and running some example queries.

## GraphQL vs. REST
If you've ever built a web application before, you likely know how to build an API. If you know how to build an API, you likely know what REST is and [why it's important](https://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven). Indeed, has helped to widley standardize how most applications talk to each other and set expectations for developers to comply with a REST-like model.

To me, GraphQL is very similar to REST insofar as its usage: anywhere that you use REST, you can use GraphQL. The major differentiator, in my novice mind, is that GraphQL allows you to only query an API for what you need, and that API will return only what you've asked for. This is best illustrated by two examples.

### REST
In a typical web app backend -- Rails in this case -- I can write a controller (or view, if you're using Django) action to render some data, e,g.,
```
def index
  parks = Park.all
  render json: parks
end
```

So long as it's accessible, I can hit that endpoint in a browser (at `http://localhost:3000/parks` by default) which will give me all of my `Park` objects, as json:
```
[
  {
    "id": 1058,
    "name": "Abraham Lincoln Birthplace National Historical Park",
    "description": "For over a century people from around the world have come to rural Central Kentucky to honor the humble beginnings of our 16th president, Abraham Lincoln. His early life on Kentucky's frontier shaped his character and prepared him to lead the nation through Civil War. The country's first memorial to Lincoln, built with donations from young and old, enshrines the symbolic birthplace cabin.",
    "state": "KY",
    "image": "https://www.nps.gov/common/uploads/structured_data/3C861078-1DD8-B71B-0B774A242EF6A706.jpg",
    "list_id": null,
    "created_at": "2020-10-06T17:58:57.187Z",
    "updated_at": "2020-10-06T17:58:57.187Z"
  },
  {
    "id": 1059,
    "name": "Acadia National Park",
    "description": "Acadia National Park protects the natural beauty of the highest rocky headlands along the Atlantic coastline of the United States, an abundance of habitats, and a rich cultural heritage. At 3.5 million visits a year, it's one of the top 10 most-visited national parks in the United States. Visitors enjoy 27 miles of historic motor roads, 158 miles of hiking trails, and 45 miles of carriage roads.",
    "state": "ME",
    "image": "https://www.nps.gov/common/uploads/structured_data/3C7B45AE-1DD8-B71B-0B7EE131C7DFC2F5.jpg",
    "list_id": null,
    "created_at": "2020-10-06T17:58:57.200Z",
    "updated_at": "2020-10-06T17:58:57.200Z"
  },
...
```

And in order to grab this on my JavaScript frontend I need to make a typical API call, in this case using `fetch()`:
```
fetch('http://localhost:3000/parks')
  .then((parks) => {
    return parks.json()
  })
  .then((data) => {
    parks.forEach((park) => {
      park.render()
    })
  })
  .catch(error => {
    console.log(error)
  })
```

This should look like pretty standard behavior; we are retrieving **all** of the `Park` objects from our backend by querying that `index` endpoint, converting it to json, then running some looping code to render each park in our frontend.

### GraphQL
The foundations of GraphQL are very similar to the above REST approach, except we can query for only the things we want. For example, if we only wanted the `id` and `image` from each `Park` object, we'd use this query:
```
query {
  parks {
    id
    name
    image
  }
}
```

Let's dissect this query a little bit:
- `query` is an [operation type](https://graphql.org/learn/queries/#operation-name) that is commonly used when retrieving data. We can also use the `mutation` operation type if we wanted to change, or mutate, the data (this should remind you of GETs, POSTs, DELETEs, etc.).
- `parks` is our collection of objects that we define in a controller or view,
- `id`, `name`, and `image` are [fields](https://graphql.org/learn/queries/#fields) from each `park` object whose data we want returned to us.

And so, this would be our response:
```
[
  {
    "id": 1058,
    "name": "Abraham Lincoln Birthplace National Historical Park",
    "image": "https://www.nps.gov/common/uploads/structured_data/3C861078-1DD8-B71B-0B774A242EF6A706.jpg"
  },
  {
    {
    "id": 1059,
    "name": "Acadia National Park",
    "image": "https://www.nps.gov/common/uploads/structured_data/3C7B45AE-1DD8-B71B-0B7EE131C7DFC2F5.jpg"
  },
...
```

So we're doing much of the same stuff as we did in that more traditional REST approach, but we're *only querying for the data we need* and receiving *only that data* in the response. This can be very helpful in terms of predicting what data will be retrieved and help to minimize the amount of frontend code you need to loop and sort through your data.

[⟵   back to blog](./blog-home.html)
