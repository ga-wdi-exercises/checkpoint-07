# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A sql database is a relational database that uses tables and one-one, one to many, and many to many relationships to structure the stored information. A NOSQL database is a database that instead of using "tables" takes information that is stored in BJSON as documents which contain "collections " that would be the representation of tables.

Using a NOSQL database can be an advantage when there is no structure or undetermined relationships to the data and you are already JSON objects on the front. SQL might be ideal when data integrity is crucial and the data will be consistent throughout the project.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
we need to make sure there is either a promise or a call back fxnction because js is asynchronous. 
let results = Author.findOne({name: "Bob"}, (err, author) => {
  (err) ? console.log(err) : console.log(author);
})
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
let andy = Instructor.findOne({name: "Andy"})
andy.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"})
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
@author.create({name: params[:name]})
redirect_to author_path(author)
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
it creates an object that is returned in lieu of a require statement so the object may be used through out the application when required
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get('/', (res, req) => {
  res.send("GET")
}

app.post('/foo', (req,res) => {
  res.send("POST");
})

app.put('/foo/:id', (req, res) => {
  res.send("PUT")
})

app.delete('/foo/:id', (req, res) => {
  res.send("DELETE")
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is a Javascript based server framework built on top of node.js that allows for server side compiling and allows for more customization around your project. You can design it based to your specifications and customization  where as in rails and using ruby, you must follow convention over configuration when planning your design. Rails makes a lot more decisions for you and therefore requires certain structure.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
var - requires the app to load in the node module called body parser
app1 - allow the app to use body parser package to allow json posts
app2 - allow the app to handle form submissions coming in utilizng body parser
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
