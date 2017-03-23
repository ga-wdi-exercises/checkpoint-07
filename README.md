# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A SQL Database is an object-relational-database while a NoSQL Database is non-relational. There are no explicit relationships between in a NoSQL db, but they CAN be replicated.

A SQL Database would be useful if you have lots of uniform data that consistently follows the same Schema(s).

A NoSQL Database would be useful for non-uniform data or if you want sub-information (such as comments) to be grouped with their parent object without needing to make extra queries and retrievals.


```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.findOne({ name: "Bob" });
console.log(results);

```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
andy = Instructor.findOne({ name: "Andy" })
andy.wishlist_items.push({ description: "Resin Laying Deer Figurine, Gold" })
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
@author = Author.create(author_params)
unless author_params
  redirect_to authors_path
end
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports allows us to create global variables that can be used across our multiple JS files
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/api/items", function(req, res){
  res.rend("index")
  console.log("Get allows you to Read a the items from the API");
})

app.post("/api/items", function(req, res){
  Item.create(req.body).then(function(item){
    res.json(item)
  })
  console.log("Post allows you to Create new items in the API");
})

app.delete("/api/items/:name", function(req, res){
  Item.findOneAndRemove({ name: req.params.name }).then(function(){
    res.json({ success: true })
  })
  console.log("Delete allows you to Delete items from the API");
})

app.put("/api/items/:name", function(req, res){
  Item.findOneAndUpdate({ name: req.params.name }, req.body, { new: true }).then(function(item){
    res.json(item)
  })
  console.log("Put allows you to Update existing items in the API");
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Well first things first, Express uses JavaScript instead of Ruby.

While Rails is VERY opinionated and follows Convention over Configuration, Express is much lighter weight and more flexible.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Your answer...
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
