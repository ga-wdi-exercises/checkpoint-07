# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
NoSQL database is a non-relational database which does not require one-to-one, one-to-many, and many-to-many relationships. You use NoSQL if you want a flexible database which does not require schema. Also NoSQL is faster than SQL because data is all in the same place.
You use SQL if your app requires relational database because even though you may still be able to enforce consistency using schemas, you have to make queries to retrieve data connected through a relation.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.findOne({name: "Bob"});
console.log(results);
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
let andy = Instructor.findOne({name: "Andy"});
andy.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"});
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
@author = Author.new
@author.create!(author_params)
redirect_to @author, notice: "New author created"
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
You can assign particular values to module.exports. Whatever you assign to module.exports will be exposed as a module by setting up using "require()".
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/checkpoint", function(req, res){
  checkpoint.find({}).then(function(checkpoint){
    res.render("checkpoint")
  });
});

app.post("/checkpoint", function(req, res){
  Checkpoint.create(req.body.checkpoint).then(function(checkpoint){
    res.redirect("/checkpoints/" + checkpoint.name);
  });
});

app.put("/checkpoints/:name", function(req, res){
  checkpoint.findOneAndUpdate({name: req.params.name}, req.body, {new: true}).then(function(checkpoint){
    res.render("checkpoint")
  });
});

app.delete("/api/checkpoints/:name", function(req, res){
  checkpoint.findOneAndRemove({name: req.params.name}).then(function(){
    res.json({msg: "success"})
  });
});

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Your answer...
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
