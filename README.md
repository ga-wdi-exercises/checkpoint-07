# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
NOSQL (Non-Relational DB) => Has no explicit one-to-one, one-to-many, or many-to-many
SQL - opposite of above ^^
Your answer...
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = {
  index() {
    AuthorModel.find({name: "Bob"} => {
    console.log(results);
  });
// Your answer...
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var studentsController = {
  show() {
    Student.find({}, (err, students) => {
    console.log(students);
    })
  }

studentsController.show({name: "Andy"})
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
var author = new Author(name: "req.body.name")
# Your answer...
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports allows other files such as (seed.js, schema.js, models.js, and index.js) to use collections or variables declared in current file.
Your answer...
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
//INDEX
app.get('/random', function (req, res) {
  Random.find({}).then(function(randoms) {
    res.send('GET ME - INDEX ROUTE');
  });
});
// Find ONE
app.post('/random/:name', function (req, res) {
  Random.findOne({name: req.params.name}).then(function() {
      res.send('POST ME - SHOW ROUTE')
  });
});
// Update it
app.put('/', function (req, res) {
  Random.FindOneAndUpdate({name: req.params.name}, req.body.random, {new: true}).then(function(random) {
    res.send('UPDATE ME - SHOW ROUTE');
  });
});

// Delete it
app.delete('/', function (req, res) {
  Random.FindOneAndRemove({}).then(function() {
    res.send('DELETE ME - INDEX ROUTE')
  });
});

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express => middleware
Rails => backend framwork with built in functionality for easy compiling and reusability.
Your answer...
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
app.use(bodyParser.urlencoded({extended: true}))=> Parses text as URL encoded data for webpage routing and allows easy use to req.body.

app.use(bodyParser.json())=> Parses json and allows easy use to req.body
Your answer...
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
