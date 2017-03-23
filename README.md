# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL is a relational database with separate tables within the database. NoSQL is document based without the tables. Instead NoSQL uses documents which can still have one-to-many and many-to-many relationships either through embedding documents or using keys. SQL uses an ORM whereas NoSQL uses an ODM.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"}) => {
  console.log(results);
};
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js

// Not sure which one is closest.


Instructor.findOne({name: "andy"}, (wishlist_items) => {
  wishlist.populate('wishlist_items')
})

Andy.wishlist.push(wishlist_items);


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
# Your answer...
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports is required to make modules or chunks of code from one application file available to other application files. This allows us to separate the application into files based on their function or responsibility and not having to duplicate code in other sections of the application.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/", (req, res) => {
  res.render("GET");
})

app.post("/", (req, res) => {
  res.render("POST");
})

app.put("/author", (req, res) => {
  res.render("PUT");
})

app.delete('/author', (req, res) => {
  res.render("DESTROY")
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
As a backend framework Rails is very structured and rigid in that structure. It is opinionated and complains when you do things just slightly different from what it wants. Express on the other hadn is more open and provides the developer more freedom. Express is also Javascript which allows the developer to maintian a single language front-end and back-end.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
body parser allows NodeJS to intake form data from a front end app. The urlencoded tells bodyparser the format in which it will be receiving the for data.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
