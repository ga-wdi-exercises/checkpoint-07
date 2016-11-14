# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```

SQL databases are relational whereas NoSQL databases are non-relational or distributed.  SQL databases have a set number of tables and rows of data usually defined in a schema file.  NoSQL databases are a collection of key value pairs and documents without a standard schema file.  SQL databases are better in situations where the dada needs to be deeply defined and organized.  NoSQL databases are better for storing "big data," large data sets which need to be combed through more generally.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);


```

```js

var results = AuthorModel.find({name: "Bob"}, function(){
  console.log(results);
})

```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js

var andy = Instructor.find_by(name: "Andy")
var wishlist_items = andy.create(description: "Resin Laying Deer Figurine, Gold")

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

@author.name.create(name: "J.K. Rowling")

```
## Express

### Question #5

What is module.exports and why do we use it?

```text

module.exports exports the variable to a file which can be used independently.  You would use it to export a model to be imported by a piece of code calling it.  

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/", function (req,res){
  res.send("Harambe")
})

app.post("/:id", function(req, res){
  res.render("post", deadGorilla)
})

app.delete("/page/:name/delete", function(req, res){
  Page.findOneAndRemove({name: req.params.name}, req.body.page, {new: true}).then(function(){
    res.redirect("/page")
  })
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```
Rails is designed to encourage working within a pre-existing framework designed to be the best fit for a developer.  It was designed with best practice opinions in mind.  Express is dynamic and unopinionated.  Express is left entirely up to the developer to use and manipulate.  Express utilizes Node.js whereas Rails utilizes Ruby.  

```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
This code allows you to use the program installed by 'npm install body-parser', which is middleware (bridge between front end and backend) needed to receive form and JSON data in code able to be used.
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
