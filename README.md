# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
(Had to google this)

SQL databases are relational databases while NoSQL databases are non-relational databases.
    You would use an SQL over a NoSQL database when you're dealing with data that is structured
    and unchanging; If you're only working with consistent data, then there is no use of working with
    a system that supports a variety of data types.

    You would use a NoSQL over an SQL database when you're trying to rapidly deploy a product.
    This way, if you need to make frequent updates to the data structure, there wont be a lot of downtime between production versions since NoSQL data doesn't need to be prepared ahead of
    time.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.findOne({req.name: "Bob"});
console.log(results);
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.find({name: "Andy"})
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
def create
  @author = authors.create(author_params)
  redirect_to authors_path
end

private
def author_params
  params.require(:name).permit(:name)
end
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports is used to export model data so it can be used in all of our files. If we did not do this, we would have to create the models in all of our files in which we use the models.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

(Had to refer to past lessons/exercises)

app.get("/", function(req, res){
  res.render("checkpoints");
  console.log("Get/Read");
});

app.post("/checkpoints", function(req, res){
  Checkpoint.create(req.body.checkpoints).then(function(checkpoint){
    res.redirect("/checkpoints/" + checkpoint.name);
    console.log("Post/Create");
  });
});

app.post("/checkpoints/:name", function(req, res){
  Checkpoint.findOneAndUpdate({name: req.params.name}, req.body.checkpoint, {new: true}).then(function(checkpoint){
    res.redirect("/checkpoints/" + checkpoint.name);
    console.log("Update/Edit");
  });
});

app.post("/checkpoints/:name/delete", function(req, res){
  Checkpoint.findOneAndRemove({name: req.params.name}).then(function(){
    res.redirect("/checkpoints")
    console.log("Delete/Destroy");
  });
});
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is a backend framework based on Sinatra and uses JavaScript as its' core language while Rail's core language is Ruby. This makes express easier to deal with since you can use the same language throughout, causing less headaches since the syntax will be the same throughout your whole program.

Rails is also an SQL database while Express is a NoSQL database
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
This code is used to get input from form fields in a MongoDB program since MongoDB does not accept form requests automatically.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
