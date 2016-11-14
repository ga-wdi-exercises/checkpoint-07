# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL, short for sequel, describes a relational database.  It is useful for more complex, schematic data.  When more flexibility is required in the construction of each document, a noSQL db is more suited.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
var results = AuthorModel.findOne({name: "Bob"});
console.log(results);
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var Andy = Instructor.findOne({name: "Andy"})
Andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"})
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
@author = Author.new(name: params[:name])
@author.save
```
## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports defines the code that is exported to the next document.  For example, if we set module.exports to mongoose, that variable alone, including all changes we make to it in the course of our js, will be carried over where it is called. Not well explained, sorry, but I know how to use it. Happy Monday.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get('/', (req, res) => {
  res.send("get")
})
app.post('/', (req, res) => {
  res.send("post")
})
app.update('/', (req, res) => {
  res.send("update")
})
app.delete('/', (req, res) => {
  res.send("delete")
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
First is the language that each is written in. Also, Rails is opinionated and Express is the wild West.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Body-parser allows us to grab the content of forms and use it with req.body.  The line containing json sets its return as a json object, and urlencoded({extended: true}) allows us to use the 'querystring' library on it, rather than 'qs' library. This allows for rich objects and arrays, for an end object more similar to json.
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
