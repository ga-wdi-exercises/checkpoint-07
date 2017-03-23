# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
Your answer...
Some differences would be NoSQL has schema flexibility and is very fast. As well also use object orientated databases. NoSQL would be used for front end development, it works well with JS development. Where as SQL is used for a lot of back end development like rails.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
let results = AuthorModel.find({name: "Bob"}).then((author)=>{
   console.log(author);
 })
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
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
@travis = Author.new(name:"Travis")
```rb
# Your answer...
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module exports takes the encapsulated code in the module and allows this code to be utilized across other files.
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
Your answer...
```express is a fast minimalist web framework
for node.js. Ruby is optimized for easy usage thus making it easier to work with. So essentially one is faster while the other is easier to comprehend.
### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Your answer... I do believe this allows express to handle form data.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
