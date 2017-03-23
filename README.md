# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL is a relational database structure. Meaning that it stores data in a table with columns and rows showing relationships.
NoSQL is a non-relational database that store data in JSON documents and it contains key/value pairs.
These methods of storing data are alternatives to one another and their use is dependent on the type of data the user wants stored. SQL is good for structured data if the data that's inputed has the consistent properties. NoSQL is better used for more complex or nested data.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
You would need a call back function in order for the results to return something.

var results = AuthorModel.find({name: "Bob"}, (err, authors) => {
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
var andy = Instructor.findOne({name: "Andy"}, (err, instructor) => {
  console.log(andy)
})

var deer = new Wishlist_item(description: "Resin Laying Deer Figurine, Gold")

deer.save((err, wishlist_item) => {
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
It is the object that's returned as a result of a require call. We use this to internally scope functions. Essentially, we define our functions in a separate js file and use module.export to call those functions in another file.
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
app.put('/example', function(req, res) {
  res.send('Put')
})
//DELETE
app.delete('/example', function(req, res) {
  res.send('Delete')
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
With Express we have a lot of freedom in how we structure our application, its routes, resources, and assets (folders/files, how to load different files, managing dependencies, etc). Ultimately, Express is better for fast single page apps or ones that are more interactive.
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
Your answer...
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
