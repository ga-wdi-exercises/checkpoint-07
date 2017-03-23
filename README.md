# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```
SQL is a strict and rigid relational database system using tables to structure and store information - best for complex models; NoSQL is a flexible and scalable non-relational database system that structure and stores information in JSON documents - best for simple models with similar but different objects.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js

var results = AuthorModel.find({name: "Bob"}, (err, results) => {
  console.log(results);
})

```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne({name: "Andy"}, (err, instructor) => {
  console.log(instructor);
})

var wishlistitems1 = new WishListItems({description: "Resin Laying Deer Figurine, Gold"})
andy.wishlistitems.push(wishlistitems1)
andy.save((err, instructor) => {
  if(err){
    console.log(err);
  } else {
    console.log(instructor + "was saved!");
  }
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

@author = Author.new(params[:name])
if @user.save
  redirect_to @user
else
  render 'error'
end    

```

## Express

### Question #5

What is module.exports and why do we use it?

```text

Module.exports allows us to separate our js files by exposing their contents as one global variable. The global variable isn't assigned until we require the file.  It keeps our js code clean and modular.

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is a very structured and opinionated framework; Express is much less opinionated, lighter weight and has a much more flexible structure.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text

Body-parser is middleware which is code that runs in between receiving the request and responding.

// configure app to use body parser
var bodyParser = require("body-parser")

//handles json post requests
app.use(bodyParser.json())

// handles form submissions
app.use(bodyParser.urlencoded({extended: true}))

```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
