# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
contrast:
SQL:    structured, relational, tables, explicit foreign keys
NoSQL:  unstructured
compare:
  sql/db/table/record == nosql/db/collection/document
i will start thinking about nosql for storing logs & histories from apps like httpservers, nodemon, mongod, sinatra  
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
    no callback function
    // orig:
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```
> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// new:
var results = AuthorModel.findOne({"name": req.name}, function(err, docs){
    console.log(results);
    return results;```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

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
# Your answer...
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
takes
code/methods/behaviours/functions and makes them available to other
code; similar to
inheritability in OO code, where another
class or interface can
extend or
implement
ref:  http://stackoverflow.com/questions/16213495/how-to-implement-inheritance-in-node-js-modules
      http://stackoverflow.com/questions/26309012/how-to-subclass-a-node-js-module
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
Rails is an entire framework, provides persistence/model;
Express is more like an intermediary, that doesnt 'model'
Most of the stuff i found compared Rails to Node.  Equestrian compared
Node as javascripts equiv to Javas JVM, i.e.
js:node :: java:JVM
other stuffs:
Rails:
 has built-in support for CSS and JavaScript pre-processing
 very opinionated, convention over config
Express:
 less opinionated, lots more files and connections necessary bw them that i had a hard time understanding and need to draw me some pictures when time permits

```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
parse user input
.json:  reads a forms input and stores it as a javascript object accessible through req.body
.urlencoded:  Parses the text as URL encoded data (which is how browsers tend to send form data from regular forms set to POST) and exposes the resulting object (containing the keys and values) on req.body.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
