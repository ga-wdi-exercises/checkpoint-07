# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL: Very ordered/rigid - great for uniformly structured data
NoSQL: Doesn't need a schema, flexible faster - great for data that isn't all the same structure
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.findOne({name: "Bob"});
console.log(results);```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = AuthorModel.findOne({name: "Andy"});
andy.wishlist_items.push("Resin Laying Deer Figurine, Gold")
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
var author = Author.new(name)
author.save
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
It's used to be able to reference models and other info in other files.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/", () => {
  console.log("read")
})
app.post("/new", (req, res) => {
  Thing.create(name: req.body.params).then(() => {
    console.log("create")
  })
}
app.post("/:name", (req, res) => {
  Thing.findOneAndUpdate(name: {req.params.name}, body: req.body.thing, {new: true}).then(() => {
    console.log("update")
  })
}
app.post("/:name", (req, res) => {
  Thing.findOneAndRemove(name: {req.params.name}, req.body.candidate, {new: true}).then(() => {
    console.log("destroy")
  })
})

//This question seemed a little weird. Hope this is what y'all wanted!
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is best for single-page apps (faster, less backend to load), while Rails is structured more uniform and is easier to build from scratch.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Body parser reads the body of incoming messages and interprets it as whatever we tell it to interpret it as - in this case, it is turning the requests into JSON and URLencoded data.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
