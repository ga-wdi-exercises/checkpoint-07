# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```
SQL DBs have information that are placed into table and to reference/link information between tables you create a relationship between them. NoSQL DBs do not have tables, are faster, do not have relationships, and have a data limit.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
var results = AuthorModel.find({name: "Bob"} function(err, students){
  console.log(students);
})
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findByOne({name: "Andy"})
  .then(req.params.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"}))
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
author = Author.create({
  name: "mark"
  }
  redirect_to authors path
  )

```
## Express

### Question #5

What is module.exports and why do we use it?

```
it allows us to export information from a file so we can say
"var x = require('module.export name')" and use that information in other files

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/posts", function(req, res){

})

app.post("/posts", function(req, res){
  Post.create(req.body.post).then(function(post){
    res.redirect("/posts/" + post.name)
  })
})

app.post("/posts/:name", function(req, res){
  Post.findOneAndUpdate({name: req.params.name}, req.body.post, {new: true}).then({
    res.redirect("/posts/" + post.name)
  })
})

app.post("/posts/:name", function(req, res){
  Post.findOneAndRemove({name: req.params.name}).then({
    res.redirect("/posts")
  })
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```
Rails is opinionated and wants you to organize files in a very specific way. Express does not care about how you organize your files.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
var bodyParser requires the bodyParser module
bodyParser.json converts data into a json object
urlencoded lets configure the parser to support html forms


```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
