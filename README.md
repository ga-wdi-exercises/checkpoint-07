# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL database is a relational db whereas NoSQL database is a non-relational or distributed db
SQl db are table based databases whereas NoSQL dbs are document based -  key - value paired
NoSQL databases fits better for hierarchical data storage as it follows key-value pair way to store databases and they are preffered for large data set
SQL dbs are used to complex query intensive enviornment
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
const Author = mongoose.model("Author",AuthorSchema)

var results = Author.find({name: "Bob"}
    console.log(results)

```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var result = Instructor.findOne({name: "Andy"})
      console.log(result)
      result.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})

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
post '/author' do
  @author = Author.create!(params[:name])
  redirect "/authors"
end


## Express

### Question 5

What is `module.exports` and why do we use it?

```text
module.exports is used to make the module accessible across different files
eg: model is defined in a file and we use module.export {model} so that this model can be reffered in other files
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get('/', function(req,res) {
  a.find({})
  res.render("index")

})

app.post('/', function(req,res) {
  a.create(req.body.a)
  res.redirect("/")
})

app.post('/', function(req,res) {
  a.findOneAndUpdate({})
  res.redirect('/')
})

app.post('/delete',function(req,res){
  a.findOneAndRemove({})
  res.redirect('/')

})

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails use postgrsql and ruby
Rails use active record as ORM
Rails have convention over configuration
Rails generate all the required dependencies
easy functions and manipulation

Express  use mongodb and node js
Express use mongoose as ORM
have to install the dependencies you need

```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Parse incoming request bodies in a middleware before your handlers, available under the req.body property
app.use(bodyParser.json()) basically tells the system that you want json to be used
A new body object containing the parsed data is populated on the request object after the middleware . This object will contain key-value pairs, where the value can be a string or array (when extended is false), or any type (when extended is true).
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
