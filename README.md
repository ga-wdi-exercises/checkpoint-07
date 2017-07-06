# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are relational databases which mean they are useful when tables have relationships such as
many-to-many or one-to-many.  NoSQL databases are lighter and more flexible.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// We want to use a promise to ensure the code is executed after the query.  
AuthorModel.find({name: "Bob"}).then(function(results){
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
Instructor.findOneAndUpdate({name: "Andy"}, function(results){
  results.wishlist_items.push(new Item({description: "Resin Laying Deer Figurine, Gold"}))
})
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
if @author.save
  redirect_to @author
else
  redirect_to new_author_path
end
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
module.exports allows us to export code from one file to another.  We can set variables in
one file and access their value in another.
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get("/candidates", function(req, res){
  res.send("get")
})

app.post("/candidates", function(req, res){
  res.send("post")
})

app.get("candidates/:name", function(req, res){
  res.send("put")
})

app.get("candidates/:name/delete", function(req, res){
  res.send("destroy")
})

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is a very opinionated and rigid framework while express is not.  Rails comes with
many folders and conventions while express is very flexible and light.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
These lines use the middleware "body-parser" to parse data from forms to be used in a RESTful action.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
