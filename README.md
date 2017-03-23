# Week 10


<!-- test tests test  -->
## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL is a relational database, meaning they store data in tables and rows to represent the relationships within and between models. In non-relational data bases, like NoSQL, data is represented in JSON form.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// You would want to have the author model set outside the method and then set the above find method as a function and pass in bob as a parameter:

var AuthorModel = Schema.AuthorModel

function findByName(bob) {
  AuthorModel.findOne({name: "Bob"})
  console.log(results)
}


```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Instructor.findone({name: "Andy"})
//wishlist_items.create({description:"Resin Laying Deer Figurine, Gold""})
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
author.create!(key: value)
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
It allows yo to reference schema models in other files by requiring the schema.js file
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/:name", (req, res) => {
  res.send(`hello ${req.params.name}`)
})

app.post("/", (req, res) => {
  res.send("can post")
})

app.post("/model/:name/delete", function (req, res)){
  Model.findOneAndRemove(name: req.param.name).then(function(){
    res.redirect("/model")
  })
}

app.post("/model/:name", function (req, res)){
  Model.findOneAndUpdate({name: req.param.name},req.body.model, {new:true})
    res.redirect("/model" + model.name)  
  )}

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
The major thing is that Express in not as opinionated as Rails and its a lot lighter weight (you can add only as needed)
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Configures/ requires body-parser to be used by the app (body parser takes the data in HTML form and makes it JSON so express can use it). line 2 handles JSON post requests, and line 3 handles form submissions
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
