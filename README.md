# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are relational databases whereas NoSQL databases are non-relational databases.  Typically an SQL database is used with tables whereas a NoSQL database uses  collections and documents based.  NoSQL provides more flexibility because there is less structure.  An example of a NoSQL would be MongoDB.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"}.then((author))=>{
  console.log(results));
}

```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: andy}).then((err, res))=>{
  if(err){
    console.log(err);
  } else{
    console.log(res);
  }
result.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold" })
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
It allows us to export code from one file to another.   We use it to separate our js files by exposing their content as one global variable.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
// had to check last nights homework for assistance with this one.
var express = require("express");
var app = express();

const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.render("got");
});

app.get("/champions", (req, res) => {
  res.send("posted");;
});

app.get("/champions/id:", (req, res) => {
  res.send("updated");;
});

app.get("/champions/id:", (req, res) => {
  res.send("deleted");
});

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is much less opinionated and is lighter weight than rails.  Express gives you more freedom in how you structure your application.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
The first line configures the app to use body-parser.  I think it should use const instead of var just to stay consistent with the material from the lessons.  The second line handles the json put request, and the third handles the form submissions.  The "body" in body parser is similar to that of params, but params is used exclusive for URL parameters in express.

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
