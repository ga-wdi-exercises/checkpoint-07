# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are called as relational databases and NoSQL are non-relational.  SQL databases store their data primarily in tables where NoSQL store their data in documents.  The schema in NoSQL are dynamic and SQL has predetermined schema.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// I'm not completely sure about this, but I think this is the correct answer because just using find will return all documents that have the name: "Bob"
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
let andy = Instructor.findOne({name: "Andy"})
andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"})
andy.save()
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
@author = Author.create(name: params[:name])
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
It allows us to export code from one file to another. One of the benefits of doing this is that it limits what information is available on the global scope
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/persons", (req, res) => {
	Person.find({}).then((persons) => {
		console.log("read")
	})
})

app.get('/person/:id', (req, res) => {
	Person.findById({id: req.params.id}).then((person) => {
		console.log("read")
	})
})

app.post("/persons", (req, res) => {
	res.json(req.body).then(() => {
		console.log("update")
	})
})

app.post("/persons", (req, res) => {
	Person.create(req.body.person).then((person) => {
		console.log("create")
	})
})

app.post("/persons/:id/delete", (req, res) => {
	Person.findOneAndRemove(id: req.params.id).then((person) => {
		console.log("delete")
	})
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express shares more similarities with Sinatra than it does with Rails.  With that being said, one of the key differences is of course the language it is written in.  I would say the more importatn difference is that it is less opinionated than Rails, which gives us more flexibility.  With that flexibility, comes more set up and configuration
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
This code imports body-parsers which is a middleware.  Body parser allows us to receive user input through forms. The 3rd line allows configures the parser to support HTML forms
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
