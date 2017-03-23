# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL (Structured Query Language) is a programming language that is used to manage data in relational database’s. Where as, NoSQL is a database that provides a mechanism for storage and retrieval of data which is modeled in means other than the tabular relations used in relational databases.

I'd use SQL to managed anything that I'm looking to build with C.R.U.D. functionality. I might use NoSQL for an app that I have users using a ton of C.R.U.D. functionality that won't impact any of the other data in the database.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthoModel.findOne({ name: "Bob" });
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js

```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
andy = Instructor.findOne({ name: "Andy"})
andy.wishlist_items.push({ description: "Resin Laying Deer Figurine, Gold" })
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
unless author_params
  redirect_to authors_path
end
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports gives us the ability to create global variables that can be used across all of our JS files.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/api/items", function(req, res) {
  res.rend("index")
  console.log("Get allows you to read all of the items from the API")
})

app.post("/api/items", function(req, res) {
  Item.create(req.body).then(function(item){
    res.json(item)
  })
  console.log("Post allows you to create new items in the API")
})

app.delete("/api/items/:name", function(req, res) {
  Item.create(req.body).then(function(item){
    res.json(item)
  })
  console.log("Delete allows you to delete all of the items from the API")
})

app.put("/api/items/:name", function(req, res) {
  Item.findOneAndUpdate({ name: req.params.name}, req.body, { new:true}).then(function(item){
    res.json(item)
  })
  console.log("Put allows you to make sure all of your items are updated in the API")
})
  console.log("Put allows you to make sure all of your items are updated in the API")
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express uses Javascript vs using Ruby. Where as, Rails follows the convention over configuration. We like to use express because its flexible and lighter.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
This is telling the app to use body-parser and configure it to work with the html in the document. Body-Parser is a middleware that runs between the HTML forms and Express which allows express to post the form's HTML content as json. This literally allows them to take html from the body and turn it into json data so express can post it to the api.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
