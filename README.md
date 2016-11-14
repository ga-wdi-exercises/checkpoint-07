# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
A SQL database organizes information into tables that are connected to one another through relationships (i.e. a SQL database is relational) and enforces a strict structure via table schemas. The information inside a noSQL database is not organized through relationships and is not necessarily normalized through the use of schemas. A NoSQL database would be good to use when you may have non-uniform data or are prototyping (faster/easier to set up).

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
// The mongoose .find query is used to retrieve multiple documents from a database based on a given condition. The above code would return an array of author models (although there may only be one result in that array). Additionally, 'results' in the above example is currently storing only the query, not the output of the query (for which a callback or promise would be necessary). The correct code for retrieving a single document and storing it to a variable is:
var result
AuthorModel.findOne({name: "Bob"}).then((author) => {
  result = author
}).catch((error) => {
  console.log(error)
})
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: 'Andy'}).then((andy) => {
  andy.wishlistItems.push(new WishlistItem({description: "Resin Laying Deer Figurine, Gold"}))
  andy.save().catch((error) => {
    console.log(error)
  })
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

```
## Express

### Question #5

What is module.exports and why do we use it?

```text

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text

```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Your answer here
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
