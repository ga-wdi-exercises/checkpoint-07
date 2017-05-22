# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```The main difference is SQL is a relational database and NoSQL is not. NoSQL allows more flexibility in storing data (in collections, not tables).
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.findBy({name: "Bob"});
console.log(results);
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
var andy = Instructor.find_by({name: "Andy"});
andy.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})
```

```js
var andy = Instructor.find_by({name: "Andy"});
andy.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})
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
@author = Author.create (:name)
```

## Express

### Question #5

What is module.exports and why do we use it?

```Module.exports helps with separation of concerns. We use it to reference files.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/", (req, res) => {
  res.send("GET");
});

app.post("/", (req, res) => {
  res.send("POST")
})


```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```Rails = much more opinionated and structured. Express flexible and light for web development.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```Parses app data in JSON and urlencoded. 
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
