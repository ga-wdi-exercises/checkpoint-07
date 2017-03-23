# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A SQL database contains explicit relationships (one-to-one, one-to-many, etc.) whereas a NoSQL database does not. You might use a NoSQL database when you want to be flexible and don't wish to follow a schema, and you might use a SQL database for structure. 
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"}), (err, author) => {
console.log(author);
};

```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne({name: "Andy"})
Instructor.create(req.wishlist_items)

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
``
		@author = Author.create!(author_params)
		redirect_to "/authors/#{@author.id}"
```

```

## Express

### Question #5

What is module.exports and why do we use it?

```text
Module.exports allows us to reference models in other files when creating a schema 
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/pencils", function(req, res){
	res.render("index")
    }

app.post("/pencils/new", function(req, res){
	res.render("create")
  }

app.get("/pencils/:name", function(req, res){
  		res.render("show")
    }

app.put("/pencils/:name/edit", function(req, res){
	res.render("edit")
}  


```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express uses Javascript, while Rails uses Ruby. Ruby contains a number of conventions and built-in helpers, files, and folder, while Express is typically leaner. 
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Middleware that reads a form's input and stores it as a javascript object accessible through req.body
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
