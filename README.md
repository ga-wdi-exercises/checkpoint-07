# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
NoSQL DB doesn't have any relationships or schema. NoSQL DB are great for fast, small, robust data systems where you don't need any relationships (no one-to-one, one-to-many) and all the data is in one place. SQL is built around relationships - you should use SQL when you have data that

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
There isnt any callback in where we can send the results to.

```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Model.findOneAndUpdate(name: "Andy", {wishlist_items: "Resin Laying Deer Figurine, Gold"})

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
author = Author.new(name: "Janet") // to create a new instance of Artist object

author.save // to save to our database
```
## Express

### Question #5

What is module.exports and why do we use it?

```text
We use this line to make our file 'exportable', meaning we can call the file from anywhere else in our application, as a global variable.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/", (req, res) => {
  res.send("Hello, get")
})

app.post("/:id", (req, res) => {
  res.send("hello, post")
})

app.put("/:id", (req, res) => {
  res.send("hello, put")
})

app.delete("/hello/:id", (req, res) => {
  res.send("Hello, delete")
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
There really isn't any difference - both are backends that make creating APIs quick and easy. I would say that Express is lighter and maybe faster than Rails but I don't think there's too much of a difference beyond personally preference.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
on the first line, the package Body Parser is called to be required and being saved as a var bodyParser
The 2nd line makes bodyparser handles json post requests, this can have many options but there isn't being used on this line.
The last line is optional - this configures the parser to support html forms. The urlencoded takes options as well, The extended option allows to choose between parsing the URL-encoded data with the querystring library (when false) or the qs library (when true).
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
