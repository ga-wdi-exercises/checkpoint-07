# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL is a relational database structure. Meaning that it update and retrieve datas.
NoSQL is a non-relational database that store data in JSON documents and it contains key/value pairs.
SQL is good for structured data if the data that's inputed has the consistent properties. NoSQL is better used for more complex or nested data.

```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"}, (err, authors) => {
  console.log(results)
})

You need callback.
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne({name: "Andy"}, (err, instructor) => {
  console.log(andy)
})

var wish = new Wishlist_item(description: "Resin Laying Deer Figurine, Gold")

wish.save((err, wishlist_item) => {
  if(err){
    console.log(err)
  }else{
    console.log(wishlist_item)
  }
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
author = Author.create(name: => "author's name")
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports is one of require method that by assigning particular values to it, we can explicity define the object that will be brought in when another file requires() the file from which we are exporting.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

//GET
app.get('/', function(req, res) {
  res.send('Get')
})

//POST
app.post('/', function(req, res) {
  res.send('Post')
})

//PUT
app.put('/random', function(req, res) {
  res.send('Put')
})

//DELETE
app.delete('/random', function(req, res) {
  res.send('Delete')
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Expree is more open world to structure our application. Express is better for fast single page apps.

Rails goes through middleware to process and requires GEMS to process and respond to requests.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Telling express to use body-parser and to look at all incoming data as a json object
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
