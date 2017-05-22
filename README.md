# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```
SQL databases used relational tables and rows to store data. NoSQL databases are a collection of data and no relations except when specified.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js

var results = AuthorModel.findBy(name:"Bob");
console.log(results);
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findBy(name:"Andy")
andy.wishlistItems.create(description: "Resin Laying")
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
@author = Author.create(name: "name")
redirect_to author: @author
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
It help us contain our code and the ability to provide only the bits that are needed at a certain file.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get('/students', function (res, req) {
  console.log(res)
})
app.get('/hello/:name', function (res, req) {
  console.log(res)
})
app.delete('/hello/:name', function (res, req) {
  console.log(res)
})
app.put('/:hello', function (res, req) {
  console.log(res)
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails out of the box very configured backend frameworks that gives a lot a function but at times it is limited.
Express is a light weight and flexible backend frameworks, it is much more customizable uses the same language of the web JS.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
The first one  will not accept traditional post requests and renders Json only.
urlencoded will accept traditional HTTP requests.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
