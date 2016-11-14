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

```js
No idea, I will research.
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Some idea, but I will research.
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
No idea. I will research.
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

Need to review and research all things Express.

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
Parses the body as JSON.
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
