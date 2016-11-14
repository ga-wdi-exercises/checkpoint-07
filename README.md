# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
The main difference between a SQL and NoSQL db is the relationships can it hold.
In a NoSQL db, there is no explicit one-to-one or one-to-many relationship, as there is in a SQL db. This allows for more flexibility. In cases where I need more flexibility, and speed (since its all the same place), I would use a NoSQL db, while if  I need a more uniform approach, I would use SQL.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js

```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
andy = Instructor.findOne({name: "Andy"})
andy.create({description: "Resin Laying Deer Figurine, Gold"})
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
module.exports is used when we want to apply a "connection or link" between two files in node. Module encapsulates related code into a single unit of code, which can then be exported to be used in other files.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/", (req, res) => {
  res.send("GET")
})
app.get("/new", (req, res) => {
  res.render("SENDING US TO FORM PAGE")
})
app.post("/new", (req, res) => {
  Url.create blah blah
  res.send("POST")
})
app.post("/url/:short/delete", (req, res) => {
  Url.findOneAndRemove blah blah
  res.send("DELETE")
})
app.post("/url/:short", (req, res) => {
  Url.findOneAndUpdate blah blah
  res.send("PATCH")
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
In my personal experience, Express allows for more flexibility. While in rails, Schemas are created and therefore structurally more rigid. This means, if the project requires more pivoting, its a bit more work in migrating changes to the tables. Another big difference between the two is the conventions. Rails was created based on the assumptions of what the everyday developer needs. While Express allows for a more "personalized" approach.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
After an npm install of body-parser, we begin to "use" in in our application. Without the require, body-parser is not in use. The next line allows us to parse JSON data. The final line allows us for form submissions in our application.

```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
