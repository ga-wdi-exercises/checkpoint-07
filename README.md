# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL databases are used when there are relationships involved, i.e. doctors and patients. It stands for Structured Query Language.  NoSQL is used when there is not a relationship between the data and you just want to store it.  For NoSQL you would use collections instead of tables.

```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
The syntax "AuthorModel", that would not be the correct name.  If you are trying to find a document with the value "Bob" for the key "name" in an author collection.
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.find_by({name: "Andy"})
var wishlist_items = Wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})

### Question #4

Convert the following create method in Mongoose to ActiveRecord.

```js
var author = new Author({name: req.body.name})
author.save(function(err){
  if (!err){
    res.redirect("authors")
  }
})
```rb
@author = Author.new
@author = Author.create(author_params)
redirect_to authors_path
```
## Express

### Question #5

What is module.exports and why do we use it?

module.exports is used to export information from one file to another. For example, if you want create a model and schema and saved it to Schema.js, if you would like to use it in your seed.js file you would need to export the model and schema, which would be done use module.exports.

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get('/', function(req,res) => {
  res.send("Get")
})

app.post('/:type', function(req,res) => {
  res.render("post",
  puppies
)
})

app.put('/:type', function(req, res) => {
  res.render("update",
  puppy)
  })

app.delete('/:type', function(req,res) => {
  Puppy.findOneAndRemove(req.body.puppy)
  res.send("delete")
  res.redirect('/')
  })

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

Express is runs on node.js and is written in javascript.  Rails is written in Ruby and uses embedded ruby files not html.  Rails talks to ActiveRecord while Express talks to mongoose.  

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

Body Parser is used when you want to submit a post request and form in express. It creates middleware.
"var bodyParser = require("body-parser")" is requiring or adding body-parser to the file and "app.use(bodyParser.json())" is allowing json to be rendered. It returns middleware that only parses json. "app.use(bodyParser.urlencoded({extended: true}))" returns middleware that only parses urlencoded bodies. The extended option allows you to choose between parsing the URL-encoded data with the query-string library when false, or the qs library when true.

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
