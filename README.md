# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text

Basically SQL databases are relational databases. No SQL databases are non-relational databases. SQL databases uses table based db's , NOSQL databases use document based db's.

```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
If we want to get an author with name "Bob", mongoose method must be different.
We use ".findOne" method to retrieve an author with a name "Bob" instead of ".find".
We also need a callback function because of asynchronicity. First we want to retrieve data and then display that.

var results = AuthorModel.findOne({name: "Bob"}).then ((err, results) => {
  if (err) {
    console.log(err)
  }
  else {
    console.log(results)
  }
})

```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne({name: "Andy"})
andy.create({wishlist_items.description: "Resin Laying Deer Figurine, Gold"});

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
var author = Author.create!(name: "Tarik")

```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
module.exports helps us to use partial or all the codes from another file. We use it
because it is more dry. We don't need to create variables again and again.
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get("/restaurants", (req, res) => {
  res.send("Read")
})

app.post("/restaurants", (req, res) => {
  res.send("Create")
})

app.post("/restaurants/:name", (req, res) => {
  res.send("Update")
})

app.post("/restaurants/:name/delete", (req, res) => {
  res.send("Delete")
})

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
The main difference between Express and Rails is being opinionated. Rails was opinionated that means there were mostly "convention over configuration". We can describe Express as un-opinionated because we have a lot of autonomy to structure our app.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
bodyParser helps us to make CRUD via forms. It helps us retrieve params from forms.

First line is to use bodyParser in our app. We write that code after doing npm install body-parser.

In second line we want body-parser to handle JSON post requests.

In last line we want body-parser to handle form requests.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
