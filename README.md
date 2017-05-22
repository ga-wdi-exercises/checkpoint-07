# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
Your answer...
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
Instructor.findOne({name: "Andy"}).then(function(instructor){
    res.json(instructor)
  });

Instructor.create(req.params.wishlist_items).then(function(instructor){
  res.json(instructor)
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
@author = Author.create(:name)
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
`module.exports` is used in regards to the seperation of concerns; instead of putting all of your code in one file, files are wrapped in `module.exports` in order for their variables to be used within seperate files.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/", function(req, res){
  console.log("index")
})

app.post("/new", function(req, res){
  console.log("new")
})

app.put("/edit", function(req, res){
  console.log("update")
})

app.delete("/edit", function(req, res){
  console.log("delete")
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Well first, Express uses Javascript while Rails uses Ruby. Additionally, Rails is more opinionated than Express is, meaning developers are given more freedom but less structure when using Express as a backend framework. Rails has more strict guidelines.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
The first line allows us to handle AJAX requests with JSON bodies. It will run a request through JSON before providing a response (I think).
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
