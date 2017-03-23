# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are relational in nature and are rigid in how it is structured. There are clearly defined relationships, and each table (and SQL DBs use tables) has specific architecture to its data.  SQL Databases can be used in pretty much any project, although it isn't always the idea solution.  It's probably the right choice when the data is highly structured and that structure is generally unchanging.  It's also probably a good idea if you want separation of data, as there are multiple tables.
NoSQL databases, on the other hand, are non-relational, and have all the data (as objects...or documents) lumped together in one location.  The schema is highly fluid, and there is little to no rigidity and the data you can put into it.  This allows for faster searching, and often times one query will do when in a relational database it would take many queries and joins.  This type of database is well suited for a project that has fluid requirements.  Things can change on a dime, and so the database can handle those changes.  It's also scalable as changes in a NoSQL database are no problem, whereas the rigid structure of a SQL database would create cascading effect with single changes that might cause difficulty.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// The asynchronous nature of JS, it is not "waiting" for the response to the request to find the object/document with the name of "Bob".  As a result, at the time of the console.log, the code is probably waiting for a response, therefore the variable 'results' references no object, which means it is undefined.  The simple solution is the utilize a callback function, although I am partial to using .then().  It should be noted that mongoose queries are not actually fully-fledged promises (as per documentation), and actually returns queries, so a .catch() and what not wouldn't work, although .then() is built in.  So we can use that to create a good query:
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

// Right off the bat, it looks as thought wishlist_items is an array of items, so a simple findOneAndUpdate is probably not ideal.  Here's my take...
Instructor.findOne({name: "Andy"}).then((error, result) =>{
  if(error){
    throw(error)
  } else {
  result.wishlist_items.push({description: "Resin Laying Deer Figurine, Gold"})
  result.save
  }
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
@author = Author.create!({name: params[:name]}) #although in this case I would probably use author_params and define that in a private
redirect_to author_path(@author) #assuming routes are properly set up
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports lets us export an object that contains data we wish to pass on to the rest of the NODE application via "require".  This allows us to have more modular code with multiple, separated files, while allowing items to be accessed amongst each other.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
const express = require("express")
const app = express()

app.get("/", (req, res)=>{
  console.log("GET")
})
app.post("/puppies", (req, res)=>{
  console.log("POST")
})
app.post("/puppies/:id", (req, res)=>{
  console.log("PUT")
}
app.delete("/puppies/:id", (req, res)=>{
  console.log("DELETE THE PU- this is pretty morbid.")
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is a NODE framework whereas Rails is for Ruby.
Express is highly modular, expecting most of its functionality to come from modules imported in, such as handlebars, body-parser, among other things.  It's a lightweight, un-opinionated framework that allows a high degree of variability and customization whereas Rails expects convention over configuration.  Rails is highly opinionated, that is it has very specific guidelines as to how to write things, so it ends up being very rigid (rails is an apt name).  It's easy to use, but not as forgiving on novel thought.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Adding the body-parser module so Express knows how to handle form data (body-parser is middleware that takes incoming form requests and parses it in a specified manner for us).  In this case, we are telling body-parser we want to read incoming requests as JSON objects, and the third line allows for rich objects and arrays to be encoded into the URL-encoded format.  That is, it allows things that are not just strings or arrays in.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
