# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases have data stored in tables with predefined schema while NoSQL has unstructured data stored in documents, with a dynamic schema.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// Your answer...
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
 var andy = Instructor.find({name: "Andy"})
 andy.wishlist_items.push({description: "Resin laying Deer Figurine, Gold"})

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
@author= Author.new(author_params)


```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports makes it possible for us to save a snippet of code and be able to call that in other application files to use said code.  It is used to keep our code dry and less repetitive.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/authors"), function(req, res){
  res.render("GET")
}
app.post("/authors"), function(req, res){
  res.render("POST")
}
app.put("/authors/:id"), function(req, res){
  res.render("PUT")
}
app.delete("/authors/:id"), function(req, res){
  res.render("DELETE")
}
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is a much more conventional framework. For example in rails it looks for specific files in specific directories to do a specific job, while express you could just put it all in random files and it will work.  Ruby also runs sequentially while express runs asynchronous where callbacks are needed.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
The first line is creating code 
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
