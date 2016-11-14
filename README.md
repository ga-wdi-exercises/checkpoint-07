# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL databases are relational in that they use individual tables that define models and relationships.  

Non-sql database are typically document based.

NoSQL db are normally have restrictions on max file size but are quicker and simplier to interface with.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
The issue is that the results should not be logged immediately after as in the example above. as the find might not have completed.  It should be be done as a callback.
var results = AuthorModel.find({name: "Bob"}, function (err, db_articles) {
  if(err) {
    console.log(err)
  }
  else {
    console.log(results);
  };
});



```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = {  Instructor.find({name: "Andy"}, (err, instructors) => {
  andy.wishlist_items.create({ description: "Resin Laying Deer Figurine, Gold" }, (err, wishlist) => {
    if (err){
      console.log(err);
    }

  });
});

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
 var @author = Author.create(name: req.body.name);

```
## Express

### Question #5

What is module.exports and why do we use it?

```

module.exports is used to identify ( or expose ) those items you wish to make visible in scope to another module.  A corrisponding Require statement is used to import the definition of the exported item.

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

/// GET m
app.get('/', function (req, res) {
console.log('This might be the Welcome View')

})

// POST method  create for records in Candidates table
app.post('/candidates', function (req, res) {
console.log('This might create request ')
})

app.get('/:id', function (req, res) {
console.log('This might be the show ')
})

// POST method route
app.post('/:id/delete', function (req, res) {
console.log('This might delete request ')
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text

```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text

var bodyParser = require("body-parser")  Used to import the code into this scope to reference in this module.

app.use(bodyParser.json()) Returns middleware that only parses json not HTML.

app.use(bodyParser.urlencoded({extended: true})) configure the parser to support html forms.
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
