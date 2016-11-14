# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
A SQL database has defined relationships between the tables inside it and defined columns within the tables. A NoSQL database does not have relationships defined by nor are the columns static in the same way.

It is best to use a SQL database when your application is using structured data of a known format that is relational in nature. A NoSQL database is useful if your application is working with unknown or changing data or with data that has very few definable commonalities.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
// asynchronicity
var results = AuthorModel.find({name: "Bob"}).then( results => {
  console.log(results);
})
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne({name: 'Andy'}).then(result => {
  WishlistItems.create({instructor: result, description: 'Resin Laying Deer Figurine, Gold'})
})
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
@author = Author.create(author_params)
respond_to do |format|
  if @author.save
    format.html { redirect_to: authors_path }
  end
end
```
## Express

### Question #5

What is module.exports and why do we use it?

```text
This enables us to specify what part of the code of a file ought to be available for reference within another file. The value contained can be a value, an array, an object literal, a function, or all of the above stored in an object. The code in the rest of the file might do things that you don't want to make available to other parts of the application. Module.exports allows you to specify exactly what is available.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get('/authors', function(req, res) {
  Author.find({}, function(authors) {
    res.send('index')
  })
})

app.post('/authors', function(req, res) {
  Author.create({req.body}, function(author) {
    res.send('create')
  })
})

// not sure about this one and ran out of time
app.put('/authors/:id', function(req, res) {
  Author.findById(req.params.id, function(err, author) {
    author.update(req.body)
  })
})

app.get('/authors/:id', function(req, res) {
  Author.findById(req.params.id, function(err, author) {
    Author.remove({_id: author._id}, function(err) {
      if (err) {
        res.send(err)
      } else {
        res.send('delete')
      }
    })
  })
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is built on Ruby and Express is built on Node.
Rails is a very opinionated framework, Express has no opinions. This means that people will expect something to be done in particular way in Rails whereas Express is the wild west.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
The first line imports the body parser module to make it available to the rest of the file.
The second line allows the client to send requests in the form of json to the server. The body parser module will know how to handle the json requests.
The third line enables url encoded data to be set from the client to the server. The `extended: true` parameter allows for all data types to be passed in the body (otherwise only a string or array can be passed).
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
