# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A SQL database stores information in rows and columns within a table.  It adheres to a rigid format, and is good for complicated nested data structures.  A NoSQL database stores information in documents within collections.  It is a more flexible format, and is beneficial when customization and flexibility are desired, and when there aren't multiple levels of nested data. 
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
it should just be
var results = Author.find({name: "Bob"});
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.find({name: "Andy"})

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
@author = Author.create(params[:name])
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports makes available the code we need in another file.  we use it since we can't just use script tags to link files together
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

def "/index" {
	console.log("put")
}

def "/index/new" {
	console.log("post")
}

def "/index/id/edit" {
	console.log("patch")
}

def "/index/id/delete" {
	console.log("delete")
}

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is a highly opinionated framework (there is the idea that there is a best way to do things and there are built in functions that will help you if you follow the right conventions).  It is rigid (you must follow the conventions) and not lightweight (a ton of files are included).  The language used with it is Ruby.  

Express on the other hand is very minimalistic and flexible.  The philosophy is only include what you need. Very little is provided initially with the idea that the developer can bring in whatever additional tools they require.  The language used with it is Javascript. 
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
the first line brings in body-parser so you can use data from forms, and sets it to a variable called bodyParser
the second line initializes bodyParser

```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
