# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A SQL database carries relations while a NoSQL database has no relationships or dependencies
NoSQL databases are more focused on key-value pairs and SQL databases are more based on tables,
rows, and columns. A NoSQL database is good when being used with mongoose to avoid latency. And an
SQL database is good when being used with Rails.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"}, function(err, docs) {
  console.log(docs);
});
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
this.andy = Instructor.findOne({name: "Andy"})
this.create = () => {
  this.wishlist_items.$save().then(() => {
    $state.go("show", {andy: andy.description})
  })
}
```

### Question 4

Convert the following create method in Mongoose to ActiveRecord...

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
redirect_to_authors_path(@author)
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
module.exports allows us to be able to export code from one file into another.
This allows for the files to linked easier and data to pass through more seemlessly
and allows for more methods to be called within the files allowing for less repetition.
```

### Question 6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

// Your code starts here...
app.get('/', (req,res) => {
  console.log('GET');
})

app.post('/random', (req,res) => {
  console.log('PUT');
})

app.post('/random/:id', (req,res) => {
  console.log('POST');
})

app.delete('/random/:id', (req,res) => {
  console.log('DELETE');
})
```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is a server framework that is built to be modeled like Sinatra. Express
allows for more freedom in being able to build a back end app in comparison to
Rails because the Rails format is very very structured and the Express back end uses
JavaScript while Rails uses Ruby. Rails unlike Express is built around the Model, View, Controller.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
what the require('body-parser') is doing is creating the middleware code that is
running between the receiving of the request and responding
app.use(bodyParser.json()) is parsing the text as a json
appuse(bodyParser.urlencoded({extended: true})) it gets immidieately fired as a
key-value pair in json that will return true to be able to execute the code
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
