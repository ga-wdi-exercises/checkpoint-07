# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
Your answer...
```
*SQL databases are table related databases where as NoSQL databases are document related databases*


### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// Your answer...
```
The reason for this is because

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
```
*var mongoose= require("./db/connection");

var Instructor = mongoose.model("Instructor");*


  *var Instructor = new Instructor({name: req.body.name})
    instructor.save(function(err){
      if(!err){
        res.redirect("instructors")
      }
    }
  }*




  Instructor.find({}).then(function(instructors){
      instructors: instructors
    });

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
# Your answer...
```
Author.create(req.body.author).then(function(author){
  res.redirect("/authors/" + author.name;)
});


## Express

### Question #5

What is module.exports and why do we use it?

```text
Your answer...
```
*module.exports is a special object included in Node.js. Module is a variable that is represents a module, and exports is an object exposed as a module. module.exports allows us to export code from one file to the next.*

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get('/'),function(req,res) {
  res.send('hello world')
}

app.post('/'),function(res,req){
  res.send('my name is luisa')
}

app.put('/'),function(res,req){
  res.send('good morning')
}

app.patch('/'),function(req,res){
  res.send('nice to meet you')
}
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Your answer...
```

Rails generator installs dependencies when project is created. So, only one command is needed for it.
Express-npm start
rails- rails s

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Your answer...
```
This is required to process the user input that is received through a form.

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
