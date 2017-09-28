# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are primarily relational and table based databases, whereas NoSQL database are usually non-relational or distributed databases that are document based. SQL databases have predefined schema whereas NoSQL databases have dynamic schema for unstructured data. You should use SQL databases when you have a well structured relational database. You should used NoSQL when either data is completely unstructured (videos, images, etc..) or it is semi-structured where the data has some form of hierarchy within itself (XML docs, JSON, BSON).
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"} => {
console.log(results)
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
let andy = Instructor.find({name: "Andy"})
andy.description = "Resin Laying Deer Figurine, Gold"

```

### Question 4

Convert the following create method in Mongoose to ActiveRecord...

```js
var author = new Author({name: req.body.name})
author.save(function(err){
  if (!err){
    res.redirect("/authors")
  }
})
```

```rb
# Your answer...
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
module.exports is a special object which is included in every JS file in the Node.js application by default. It is a way to make a module availaible in other files.
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get("/show", function (req, res) {
    Something.findOne({}).then(function (something) {
        res.send("GET request")
        });
    })
});

app.post("/create", (req, res) => {
    Something.create().then(something => {
        res.send("POST Request")
    })
})

app.post("/update", (req, res) => {
    Something.findOneAndUpdate().then(something => {
        res.send("PUT Request");
    })
})


app.post("/delete", (req, res) => {
    Something.findOneAndRemove().then(something => {
        res.send("DELETE")
    })
})

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is very opinionated as a back-end framework while express is not. Rails is a ORM and Express is not. Rails uses gems to manage dependencies while express uses npm. 
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Requires body-parser, returns middleware that only parses json, and configures the parser to support html forms to process user input received through a form.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
