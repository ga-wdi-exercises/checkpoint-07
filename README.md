# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
NoSQL database is non relational database.this means no explicit one to many and many to many relationship.
SQL database has relationship one to many or many to many.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
needs callback function
var results = AuthorModel.find ({name:"Bob", (err, results)=>{
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

Instructormodel.find({name: "Andy"}, function(err, name){
    res.render('/', {

    });
});
andy.wishist_item.create(discription: "rsisn Laying Deer", function (err, results) {

        res.send(results);
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



```

## Express

### Question #5

What is module.exports and why do we use it?

```text
A reference to the current  module. In particular module.exports is the same as the exports object.

The exports variable is initially set to that same object so in the module code you would usually write something like this:
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/", (req, res) => {
  res.send("Hello World");
});
app.post("/:yes",(req, res) =>{
  res.render("hello world");
})


```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is a minimal and flexible Node.js web application framework that provides a robust set of features for building web apps. Express works with a myriad of HTTP utility methods and middleware that allows developers to create robust APIs quickly and easily.

```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text

```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
