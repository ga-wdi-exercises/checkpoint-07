# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
An SQL database is a relational DB that has a fixed structure as defined by the schema - tables have rows and columns. Good when you have well structured data that will not go through a lot of schema changes.

A noSQL database is a non-relational DB and does not require join table operations and has more flexible data format and storage formats. Useful if you have a high volume of fairly unstructured data that will go through lots of format changes.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"}, function(results){
   console.log(results);
});
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.find({name: 'Andy'}).then(function(response){
  response.wishlist_items.push({description: "resin Laying Deer Figurine, Gold"})
}
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
author = Author.new(author_params)
author.save
redirect_to_authors_path(@author)
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
It is a special object that allows chunks of code (our 'exports') to be accessed and used in different sections or modules of our application. We would use it to access certain functionality from different files of our app.
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get('/', (req,res) => {
   console.log('GET');
 })

 app.post('/something', (req,res) => {
   console.log('PUT');
 })

 app.post('/something/:id', (req,res) => {
   console.log('POST');
 })

 app.delete('/something/:id', (req,res) => {
   console.log('DELETE');
 })

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is a server framework that is built to be modeled like Sinatra. Express allows for more freedom in being able to build a back end app in comparison to Rails because the Rails format is very structured and the Express back end uses JavaScript while Rails uses Ruby. Rails unlike Express is built around the Model, View, Controller.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
the require('body-parser') is creating the middleware code that is running between the receiving of the request and responding

app.use(bodyParser.json()) is parsing the text as a json

app.use(bodyParser.urlencoded({extended: true})) gets immidieately fired as a key-value pair in json that will return true to be able toexecute the code
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
