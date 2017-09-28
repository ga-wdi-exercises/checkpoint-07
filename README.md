# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases uses relational tables to organize its records. Its table columns are pre-defined, and the relationship between tables need to be defined as well. Navigation is done with SQL commands, but an ORM can be used to tie it to the server backend models.

NoSQL databases are organized as collections of documents, and does not follow a relational structure. Although schemas can be defined, its not required for documents in a collection to all follow a specific structure. This is makes complex relationships and scaling much easier in NoSQL databases. It uses an ODM to be interact with your server backend models.     
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
The method 'AuthorModel.find({})' is used to return all documents that correlate with the parameters of your query. 'AuthorModel.findOne' will return the document with name Bob.
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
let andy = Instructor.findOne({name: "Andy"})
andy.wishlist_items.push[{description: "Resin Laying Deer Figurine, Gold"}]
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
@author = Author.new(author_params)
@author.save
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
'module.exports' is used when we separate our concerns to different directories in Express(Node.js). Whatever we define to be exported in the module, will then be available when we require that module in a different directory or module.  
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()



var person = new Person({name: "Bob"})


app.get('/', (req, res) => {
  res.send("Get Index / READ")
})

app.post('/', (req, res) => {
  Person.create(req.params.name)
  res.send("Post Index / CREATE")
})

app.post('/:name', (req, res) => {
  Person.findOneAndUpdate({name: req.params.name}, req.body.person, {new: true})
  res.send("Post Person.name / UPDATE")
})

app.post("/:name/delete", (req, res) => {
  Person.findOneAndRemove({name: req.params.name})
  res.send("Delete Person.name / DESTROY")
})


```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is very opinionated and strongly urges the developers to follow its conventions. The benefits are that its quicker to set up simply following procedures, and its conventions stay consistent throughout projects and developers.

Express is un-opinionated and grants the developer freedom in how to structure the backend. The benefits are that developers can work with their style, make decisions on what to include and what to leave out for optimization.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Allows for parsing of the json object that is submitted through the params hash.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
