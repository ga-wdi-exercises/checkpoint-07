# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL is a relational database with more rigid rules and stores data in tables.
NoSQL is non-relational database that stores data as documents and is better for scaling up.
SQL is probably better used for more complex data ralationships whereas NoSQL is better suited to larger, data heavy application.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.findByName({name: "Bob"})
console.log(results)
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
app.get('instructor/:name', function(req, res) {
  Instructor.findOne({ req.params.name}).then(function(candidate) {
    res.render('instructor-show', {
      instructor: instructor
    });
  });
});
```

### Question 4

Convert the following create method in Mongoose to ActiveRecord...

```js
var author = new Author({name: req.body.name})
author.save(function(err){
  if (!err){
    res.redirect("/authors")
  }
})
```

```rb
def create
  @author = Author.create(author_params)
  redirect_to author_path(@author)
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
It is a way to reference models in other files so that we don't have to retype the same code multiple times
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get("/", (req, res) => {
  res.send("Get")
})

app.post("/", (req, res) => {
  Test.create(req.body.test).then(test => {
    res.send("Put")
  })
})

app.post("/", (req, res) => {
  res.send("Post")
})

app.post("/", (req, res) => {
  Test.findOneAndUpdate({test}, req.body.candidate, {new: true}).then(test {
    res.send("Delete")
  })
})



```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is a very opinionated framework with strict rules on how to execute certain things.  Express is unopinionated in that there is no set structure on how you organize your app.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
It requires the middleware 'body-parser'
Returns middleware that only parses json
Returns middleware that only parses urlencoded bodies

```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
