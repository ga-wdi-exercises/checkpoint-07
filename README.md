# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
NoSQL, like SQL, stores data but is a flexible alternative. You might use NoSQL if you have a less data pieces to work with. For example, information limited to just a book and author might be better suited for a NoSQL DB. But if one were to scale and create further models and associations, SQL would be better suited. It all depends on the data requirements.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

This is a Mongoose Query. It needs a callback.

```js
var results = AuthorModel.find({name: "Bob"}, results) => {
console.log(results);
}
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = InstructorModel.findById({name: "Andy"}, andy)
andy.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"}, wishlist)
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
author = Author new
author.name = "Hank"
author.save
```

or

```rb
author = Author.new do |u|
  u.name = "Hank"
end
```
## Express

### Question #5

What is module.exports and why do we use it?

```text
It allows a block of code to be used in other files.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Read
app.get('/authors', function (req, res) {
})

// Create
app.author('/authors', function (req, res) {
  Author.create(req.name.author).then(function(author){
    res.redirect("/authors/" + author.name)
  })
})

// Update
app.author('/authors/:name', function (req, res) {
  Author.findOneAndUpdate({name: req.params.name}, {new: true}).then({
    res.redirect("/authors/" + author.name)
  })
})

// Delete
app.author('/authors/:name', function (req, res) {
  Author.findOneAndRemove({name: req.params.name}).then({
    res.redirect("/authors/")
  })
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails has more helpful error messaging. Express is apparently faster. Will research this more.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
"In short; body-parser extracts the entire body portion of an incoming request stream and exposes it on `req.body` as something easier to interface with."
```
via [Quora](https://www.quora.com/What-exactly-does-body-parser-do-with-express-js-and-why-do-I-need-it)

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
