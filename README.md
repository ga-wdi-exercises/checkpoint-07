# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```
SQL is for relational databases and NoSQL is not. You would use a SQL database for a model that belongs to another model.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"});
console.log('last_name');
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var Andy = Instructor.findOne({name: "Andy"})
Andy.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})
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
@author = @authors.new
@author.create!(author_params)
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports allows us to separate js files and use the same variables from one file to another.
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

app.delete("/", (req, res) => {
  res.send("DELETE")
})

app.put("/", (req, res) => {
  res.send("PUT")
})


```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is a Javascript framework that uses noSQL and Rails is a Ruby framework that uses SQL.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
var bodyParser = require("body-parser")-so we can reference body-parser
app.use(bodyParser.json())-converts bodyParser to json
app.use(bodyParser.urlencoded({extended: true}))-supports HTML forms
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
