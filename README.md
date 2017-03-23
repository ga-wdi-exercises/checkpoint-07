# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A SQL Database is a relational database, meaning that tables can have one-to-many or many-to-many relationships to each other. It consists of tables, and each table has columns and rows.
A NoSQL database is made of documents. Each document is made of fields and values. NoSQL databases don't need to have a schema, also it could have. Relations between documents doesn't exist, although it can be made.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
Because JS is an asynchronous language, console.log might run before the variable evaluates. We can fix it be adding the console.log as a call back or as a promise. Here is as a promise:
AuthorModel.find({name: "Bob"}).then( (author) => {
  console.log(author);
})
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.find({name: "Andy"}).then( (instructor) => {
  instructor.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})
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
@author = Author.create!(author_params)
redirect_to author_path(@author)
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
It's a tool to encapsulate the code from one document, and package it to be used by other documents. We use it to give our code access to code from other documents.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get('/schools', (req, res) => {
  console.log("Get")
})

app.post('/schools', (req, res) => {
  console.log("Post")
})

app.post('/schools/:name', (req, res) => {
  console.log("Update")
})

app.get('/schools/:name/delete', (req, res) => {
  console.log("Delete")
})


```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is written in Rudy, while Express is written in JS and runs in the NodeJS environment through the v8 engine.
Rails is very opinionated, while Express is minimalist non-opinionated.
Express communicate better with front-end JS and APIs, because it has very similar syntax.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
The first line requires body-parser as a dependency
The second line uses body-parser to format json requests.
Th third line uses body-parser to catch data submitted in html forms.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
