# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
Your answer...
SQL - A relation (table) in a relational database is divided into set of rows and columns. A Tuple stands for a row in a database table that is retrieved using a query.

NoSQL-it may not require fixed table schemas, usually avoid join operations, and typically scale horizontally.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
AuthorModel.findOne({name: "Bob"}, function)
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.find({name: 'Andy'});

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
@author = Author.find(params[:id])
@author.update(author_params)
redirect_to @author
```
## Express

### Question #5

What is module.exports and why do we use it?

```text
moduele.exports is the returned object, when the require call is submitted.
The use  is that you set properties on the exports object in a .js file that you then import using require().
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
Not alot differences, rails have more files to to keep up with. Express is little fast than rails. Rails uses ruby and express uses node.js. But both gives same result.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
var bodyParser = require("body-parser")
= The bodyParser object exposes various factories to create middlewares. All middlewares will populate the req.body property with the parsed body, or an empty object ({}) if there was no body to parse (or an error was returned).


app.use(bodyParser.json())
= The json function takes an option options object


app.use(bodyParser.urlencoded({extended: true}))
= Returns middleware that only parses urlencoded bodies.

```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
