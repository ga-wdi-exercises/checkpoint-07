# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are relational databases. Tables are defined with specific schema, and each record is stored in a row. Records in different tables can be linked together using a foreign key. You would use a SQL database if you need to have a strict schema that all entries need to follow, and if you want to keep related data separate from each other (not directly nested within the parent element, but stored within a separate table.)

NoSQL databases are non-relational. Instead of tables, information is stored in a collection. Instead of single records being stored in a row, they are stored in a document. Documents do not have to follow a specific schema, pre-defined schema. Data does not have to be linked together or nested using a foreign key - it can be nested directly within the document it is related to.
You would use a noSQL database if you have entries that have different properties and do not follow a rigid schema.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results)


```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
We would need to put the console.log command within a callback function.
var results = AuthorModel.find({name: "Bob"}, (err, results)=> {
  console.log(results)
})
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findby({name: "Andy"})
andy.push(wishlist_items.save({description: "Resin Laying Deer Figurine, Gold"}))
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
Module.exports is used to define the dependencies that the application will require to run.
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
1. Express uses JavaScript, Rails uses Ruby
2. Rails provides us with pre-determined routes based on our models and their relationships. In Express, we define our routes.
3. Rails provides us with a Gemfile for our dependencies. In Express, we use module.exports to define our dependencies.
4. Rails provides a robust framework and file structure when a new project is initiated. Express does not provide this - you create a .js file and build your application out from there.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Body parser is a third party middleware that allows us to process information that is provided through forms. It allows us to retrieve the information from a form via a post request. 
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
