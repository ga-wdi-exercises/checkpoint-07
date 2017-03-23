# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are Relational Databases while NoSQL are non-relational or distributed database. SQL databases are tables and NoSQL are document based. You would use SQL for Rails applications and NoSQL when working with the MEAN or MERN stack.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"}, function(author){
  console.log(author);
});
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: "Andy"}).then(err, docs){
  if (err) {
    console.log(err);
  } else {
    results.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"})
    result.save
  }
})
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
# Your answer...
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
it lets us export an object that contains data we wish to pass on the rest of the NODE application. It allows us to have more modular code with multiple, separated files, while allowing items to be accessed amongst each other.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/", function(req, res){
  console.log("GET");
})

app.post("/something", function(req, res){
  console.log("POST");
})

app.post("/something/:id", function(req, res){
  console.log("PUT");
})

app.delete("/something/:id", function(req,res){
  console.log("DELETEd");
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is a NODE framework and Rails is for Ruby
Express if very flexible and gets it from the modules imported in. It is a very lightweight and not opinionated. Rails is the oppisite Rails is highly opinionated and has very specific way to  write things.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text

```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
