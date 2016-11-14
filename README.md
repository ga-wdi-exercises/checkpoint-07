# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL databases are relational, whereas NoSQL databases are non-relational.  You would use NoSQL databases when the data it contains doesn't have the same type of properties.  SQL would be used when you have data with the same type of properties.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
var results = mongoose.model('Bob', AuthorModel);
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

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

```
## Express

### Question #5

What is module.exports and why do we use it?

```text
Module.exports takes all functions related to a specific line of code and places it into a file.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get('/', function (req, res) {
  res.send('GET request to the homepage')
})

app.post('/', function (req, res) {
  res.send('POST request to the homepage')
})

app.put('/user', function (req, res) {
  res.send('Got a PUT request at /user')
})

app.delete('/user', function (req, res) {
  res.send('Got a DELETE request at /user')
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Unlike Rails, Express isn't opionated.  Express uses client-side JavaScript.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
We need to install middleware in order to get form data and JSON data in a POST request for express applications.  The solution is body parser.  The lines of code do the following, configure app to use body parser, handle Json post request, and handles form submissions.
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
