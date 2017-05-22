# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
Sql databases are relational. The tables relate to each other via foreign keys. NoSQL are non-relational and don't require a schema, however, one can embed data in order to create relationships.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?


```js
var results = AuthorModel.findOne({name: "Bob"})
  console.log(results);


```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
.find returns an array. to get the specific object use either findOne() or results[0].
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
let andy = Instructor.findOne({name: "Andy"})
andy.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})
```

```js
let andy = Instructor.findOne({name: "Andy"})
let item = new wishlist_item({description: "Resin Laying Deer Figurine, Gold"})
andy.wishlist_items.push(item)
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
@author = Author.new(author_params)  //defined in a separate private function
if save!
  redirect(@author)
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
Your answer...
it's a way organizing our app by passing the different parts (of the app) to each other using the 'requires'
function. It's a way to organize our javascript instead of having 1 giant file.  

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get('/', function (req, res) {
  res.send('hello world')
})

app.post('/', (req, res) => {
  res.send('postage')
})


app.put('/', (req,res) => {
  res.send('update')
})

app.delete('/',(req,res) => {
  res.send('delete')
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails has a lot more functionality 'out of the box', whereas express is quite minimalist and requires installing middle ware to gain whatever functionality you might require. Middleware or different packages are equivalent to gems in ruby. A ruby style framework is considered 'opinionated' whereas express and sinatra are not because they don't rely on pre defined configuration.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
These lines enable a piece of middleware that lets you extract user input from a field on on the webpage.  
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
