# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A SQL database is a relational database and is table based. A NoSQL database is non-relational database is document and collection based.

NoSQL is flexible, fast and allows the developer more creativity vs a SQL database which is strict on following convention over configuration.

```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.findOne({name: "Bob"})
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// Because we have already told it in which model we want to look for the document
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
//
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
class Author
def create
 @author = Author.create!(author_params)
  redirect_to "/authors/#{@author.id}"
end
end
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
It allows us to export code from one file to another
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

// app.get("/", (req, res) => {
// res.render("GET")
// })


```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails has a set convention to the way it orders files where as Express gives you more flexibilty in how the files are named, where they are placed and how many you use.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
This requires the body-parse package so it can be referenced later
 It also configures the parser to support html forms


```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
