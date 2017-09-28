# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are relational while NoSQL are nonrelational. SQL databases are typically table based and organized in rows of data. NoSQL databases are organized into collections of documents that hold key-value pairs and do not require strict schemas like SQL databases.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
AuthorModel.find({name: 'Bob'}).then(results => {
  console.log(results)
})
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
//Instructor.findOne({name: 'Andy'}).then(andy => {
  //andy.wishlistItems.create(description: "Resin Laying Deer Figurine, Gold')
//})

Instructor.findOneAndUpdate({name: 'Andy'}, {$push: {wishlistItems: (description: 'Resin Laying Deer Figurine, Gold)}})
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
@author = Author.new(name: params[:name])
@author.save? redirect_to authors_path 
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
module.exports makes specified data from the page its called available to other pages in the directory.
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

//create
app.post('/new', (req, res) => {
  Something.create(req.body.something).then(() => {
    console.log('create')
  })
})
//read
app.get.('/:thingName', (req, res) => {
  Something.findOne({ thingName: req.params.thingName }).then(() => {
    console.log('read')
    })
  })
})
//update
app.post('/:thingName', (req, res) => {
  Something.findOneAndUpdate({ thingName: req.params.thingName }, req.body.something, { new: true }).then(() => {
    console.log('update')
  })
})
//destroy
app.post('/:thingName', (req, res) => {
  Something.findOneAndRemove({ thingName: req.params.thingName }).then(() => {
    console.log('destroy')
  })
})

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is highly opinionated and does most of the configuration for the user. Express is much less opinionated and more minimal in it's design. Express requires the user to do all of the configuration but allows for much more control and flexibility in the organization of files.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Line 1: requires body-parser, a middleware that parses information from incoming requests.
Line 2: tells body-parser that you want to parse json.
Line 3: tells body-parser that you want to use its more complex qs library that can parse nested objects.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
