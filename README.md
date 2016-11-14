# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```SQL databases are "relational" and use tables for for the data where NoSql databases are "non-relational" and document based. A project where SQL would be ideal is when you want your data to have relationships or is not going to be represented correctly from just key value pairs.  NoSql is best for projects where your data may change over the course of development since there is no rigid schema.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
// Your answer...
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
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

```
## Express

### Question #5

What is module.exports and why do we use it?

```It allows us to export code from one file to another. We can export part of it or all of it.

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```Express: "Wild Wild West" - You don't have to follow a certain set of      rules to make it work.
Express is faster than rails.
Web Sockets
NPM vs Gems
Harder to test

Rails: Ruby is a very powerful and expressive language
Very opinionated framework you must follow the "rails way"
Migrations
Slower than Express
Easier to test

```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```
Body Parser extracts the body portion of an incoming request stream and exposes it on req.body to make it easier to use the information.

Parses the text as JSON and exposes the resulting object on req.body.

Parses the text as URL encoded data (which is how browsers tend to send form data from regular forms set to POST) and exposes the resulting object (containing the keys and values) on req.body.
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
