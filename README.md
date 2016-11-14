# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

``
NoSQL DB means that there are no explicit one to one, one to many or many to many relationships.  While a SQL DB is broken down in to tables, NoSQL on the other hand is organized by collections.  Additionally, documents in NoSQL are the equivalent to rows in SQL.
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

```text
module.exports allows code to be transferred from one file to another by making the contents a global variable
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/index", (req, res) => {
  res.render("Welcome page");
});

app.post("/create", function(req, res) {
  Thing.create(req.body.create).then(thing => {
    res.redirect(`/create/${thing.name}`)
  });
});

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is a more opinionated framework where there are more rules and it is fairly structured.  Express on the other hand is much less structured and provides the capability to build an application in any sort of a number of ways.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Your answer here
Express does not by default handle information from an HTML form.  For that to occur, it is necessary to utilize a form of "middleware" known as body-parser.  Therefore the previous lines are instructing the application to use body-parser to accept json data.
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
