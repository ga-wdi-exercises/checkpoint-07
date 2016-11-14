# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
Your answer...
SQL databases use a "relational" model of data. Explicit relationships between
models are defined (User has_many Groups). This makes it really easy to query
data along the lines of those relationships. You can represent some pretty
complicated data like this.

NoSQL DBs such as Mongo use "document" based data structures. It's all stored
using JSON-like structures (BSON, or Binary JSON in the case of Mongo). NoSQL
gives us a lot more options in terms of how data can be stored. This can work
better for certain kinds of web applications. It allows for certain efficiencies
 in speed and storage. Data can be SHARDED for super performance .
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
Mongoose queries are asynchronous. You would need to set up a callback or promise in order to use that data.
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: "Andy"}, (err, andy) => {
  if (err) throw (err)
  andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"})

  andy.save(err => {
    if (err) throw (err)
  })
})

// How'd I do? I'm still SUPER shaky on Mongoose...
```



### Question #4

Convert the following create method in Mongoose to ActiveRecord.

```js
var author = new Author({name: req.body.name})
author.save(function(err){
  if (!err){
    res.redirect("authors")
  }
})
```

```rb
@author = Author.create!(author_params)
redirect_to author_path(@author)
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
It exposes portions of code to be used by the rest of a Node application. This
allows for MODULARITY in our code. Can give seed data their own file, but still
reference easily elsewhere in the app.

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get('/', (req, res) => {
  console.log("GET")
})

app.post('/donuts', (req, res) => {
  console.log("POST");
})

app.post('/donuts/:name', (req, res) => {
  console.log("this is really a PUT");
})

app.delete('/donuts/:name', (req, res) => {
  console.log("DELETE");
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is all about modularity. The core package only takes care of the minimum
 to get up and running with a server. The rest is handled with other modules
(such as body-parser) to take care of additional functionality. With Express
you'll be configuring most things manually, much closer to something like Sinatra
than Rails.

With Rails, the key concept is "Convention over Configuration". Rails expects you
to build your app in a certain way, and if you do so, it will come together
with a lot of help from Rails.

Express is also a Node framework, while Rails is for Ruby.

```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
1. It includes the 'body-parser' module so that Express can tell what's going on in form submissions
2. The next line specifies that we want to work with data as JSON
3. The final line lets us get info as nested JSON, `{user: {email: "foo", ... }}` rather than `{ user[email]: "foo", ...}`
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
