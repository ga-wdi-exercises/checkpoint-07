# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL is basically a relational database management system where as NoSQL is a non relational database.  NoSQL is flexible and can be used for non uniform data.  Basically its good to use NoSQL when dealing with less complex associations.  SQL is good for more closely associated models that rely on one another.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
If I had to change something though I may change find to findOne because findOne returns a single document


### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
let andy = Instructor.findOne({name: "Andy"})
andy.wishlist_items.save({description: "Resin Laying Deer Figurine, Gold"})

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
@author = Author.create (params [:name])
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
Its a way of managing dependencies to keep things organized. Assigning module.exports particular values can explicitly define the object that will be brought in when another file requires a file from which we are exporting
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
Rails is opionated software. It makes assumption that there is the best way to do things. and its designed for you to do so.  Express is unopionated and fast.  Its a minmalist web framework using javascript instead of ruby.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
These are codes neccesary to implement body parser. body-parser is a piece of express middleware that reads a form's input and stores it as a javascript object accessible through req.body.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
