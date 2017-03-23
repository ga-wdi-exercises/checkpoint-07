# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A SQL database is relational: It has tables
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
AuthorModel.find({name: "Bob"}).then(results => {
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
Instructor.findOneAndUpdate(
  {name: "Andy"},
  {$push: {wishlist_items: {description: "Resin Laying Deer Figurine, Gold"}}}
)
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
@author = Author.new(author_params)
@author.save
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
In node.js, we use module.exports when we want one file ('importer.js') to include data or logic from another file ('exporter.js'). In exporter.js, we add something of roughly this form: `module.exports = {key1: value1, key2: value2, key3: value3}`. Then, in importer.js, we add something like `const exporter = require('./exporter.js')` (this path assumes that they are in the same directory). Now those key-value pairs are available for use in importer.js. For example, `exporter.key1` will evaluate to `value1`.

Why do we do this? To make our code more modular. In principle, we could put everything in one file, but this would make a nightmare out of finding things, debugging, dividing up labor, and reusing components on other projects, among other things.
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
Rails is all about "Convention over Configuration." That is, it encourages all developers to do things pretty much the same way, rather than allowing each developer to reinvent the wheel. In other words, it is "opinionated."

Express, on the other hand, is very "un-opinionated." That is, it has very few conventions, allowing a developer to configure things to her/his heart's content.

Related to this is the fact that Rails puts a lot of functionality under the hood, whereas Express does not.

Finally, Rails is fairly "batteries-included," meaning that it comes with a lot of stuff you will probably never use. Express, on the other hand, is extremely minimalist: You install packages on an as-needed basis.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
They tell Express how to extract data from forms.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
