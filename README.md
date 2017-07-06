# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
Your answer...
SQL database can be taxing to manipulate/store the data in our database and can, in fact, slow down our app, especially when we are dealing with complex associations. SQL is a table based databases while NoSQL databases are document based that can provide high performance, high availability and automatic scaling as far as the database is concerned.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// Your answer...
var results = AuthorModel.find_by({name: "Bob"})


```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
var andy = document.getElementByName("Andy");
var andy = wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})
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
# Your answer...
get '/authors' do
  @names = names

redirect "/authors"
end

```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
Your answer...
whenever we put module.exports in a file, all the objects or functions in the file will be accessible from another file.
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

// Your code starts here...
app.get("/", (req, res) => {
  res.render("welcome")
})
app.get("/:name", (req, res) => {
  res.send(`hello ${req.params.name}`)
})
app.post('/names', (req, res) => {
  console.log(req.body)
})
app.post("/:name/new", function(req, res){
  authors.push(req.body.name);
  var name = req.params.name;
  res.redirect('/' + name);
});

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Your answer...
Express is a backend framework written in JS language while Rails is for Ruby.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Your answer...
It is a middleware that is used to handle form submissions in Express
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
