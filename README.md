# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A SQL database is a relational database that follows a more rigid structure and requires schemas/ stores data in tables, while a NoSQL database is non-relational, is organized into documents and collections, and allows for greater flexibility. NoSQL databases scale out better than relational databases and are preferred for web applications, while SQL databases are preferred for enterprises because of better security models and mature data storage.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
The Mongoose queries are asynchronous, so we want to include a callback that will print the author model to the console, to ensure that the query has finished first.

AuthorModel.find({name: "Bob"}, (results) => {
  console.log(results);
})
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: "Andy"}).then((andy) => {
  var item = new wishlistItem({description: "Resin Laying Deer Figurine, Gold"})
  andy.wishlistItems.push(item)
})
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
@author = Author.new(name: params[:name])
@author.save
redirect_to authors_path
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
module.exports allows us to essentially export an object from one file to other files, making the variables global. This is very useful because we can separate our js files and keep our code more organized.
```

### Question 6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get("/", (req,res) => {
  console.log("Show")
})

app.post("/", (req,res) => {
  console.log("Create")
})

app.put("/", (req,res) => {
  console.log("Update")
})

app.delete("/", (req,res) => {
  console.log("Destroy")
})

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Your answer...
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
body-parser is middleware that extracts the body of an incoming request and exposes it as req.body to make it easy to interact with in express.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
