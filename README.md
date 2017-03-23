# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are relational and table based whereas NoSQL dbs are non-relational and document or kwy-value pair based.  SQL dbs should be used when there are clear relations between data.  NoSQL dbs are faster to query because everything is stored within a single document so they provide increased performance
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.findO({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.findOne({name: "Bob"}).then((res) => {
  console.log(res);
});

```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
let andy = Instructor.findOne({name: "Andy"}).then((res) =>{
  andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"})
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
@author = Author.create!(author_params)
redirect_to "/authors"
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports is used to export methods or variables scoped within one file and then import (using require) into a separate file to be used within that file
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
// Little confused on what this is asking, so I am just taking it literally and giving just the routes and returning a response to the console when the route is hit.  

var express = require("express");
var app = express();

app.get("/authors", (req, res) => {
  res.console.log("get");
})

app.post("/authors", (req, res) => {
  res.console.log("post");
})

app.get("/authors/:name/delete", (req, res) => {
  res.console.log("delete");
})

app.post("/authors/:name", (req, res) => {
  res.console.log("update");
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is more like Sinatra in that it is a more lightweight framework.  Express uses javascript vs Rails using Ruby.  Express is more open ended where rails is very opinionated and requires naming conventions.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
line 1: importing body parser as a dependency, body parser is a middleware that extracts the body of the incoming request so it's easier to interface with

line 2: telling body parser to parse the incoming text as json

line 3: tells body parser to take the information from an html form and encode as key:value pairs

```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
