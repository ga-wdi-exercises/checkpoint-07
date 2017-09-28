# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
- NoSQL- No explicit One-to-One, one-to-many and many-to-many relationships.
- SQL- Use of One-to-One, one-to-many and many-to-many relationships.
- SQL databases uses SQL ( structured query language ) for defining and manipulating the data.  - In NoSQL database, queries are focused on collection of documents.

```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// Your answer..
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```
```js
// Your answer...
var Instructor = InstructorModel.find({name: "Andy"})
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
Your answer...: module is a variable that represents current module and exports is an object that will be exposed as a module.
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

// Your code starts here...

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Your answer: Rails is opinionated and express isn't.Frameworks that leverage inference and "convention over configuration" are called opinionated. Rails does this so therefore rails is opinionated.
Express allows a lot of freedom in how we structure our application, its routes, resources and assets etc. Meaning we have to do more ourselves. Which makes Express un-opinionated. Therein lies the differences.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Your answer: var bodyParser..- is used so we can reference bodyParser later.
app.use...- is used to configure the parser to support html forms.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
