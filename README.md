# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL is a table based database while NoSQL is more of a document! So its relational Db vs Non-relational databsea!
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
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

```
## Express

### Question #5

What is module.exports and why do we use it?

```
Module.exports allow to use pieces of codes in other files part from the file you havewritten your code originally!
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// GET method route
app.get('/', function (req, res) {
  res.send('GET request to the homepage')
})

// POST method route
app.post('/', function (req, res) {
  res.send('POST request to the homepage')
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```
I guess one of the biggest diffrence in between them is that ruby is an opinionated framework where as node isnt! So I guess while ruby is expecting you to build your code in a certain way, such as using activeRecord; in node, you have to make more of a setup and tailor it to your needs! Node is more of an anarchist place to code, because there are almost non rules!
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```
body parser is basically encoding whatever request you are making to your server, and passsing it as either json or other formt.
the above lines of code are basically telling your node/express document to use body parser and encode to json and url!
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
