# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL is a relational database with data in different places. Organized in tables and rows. Easier to use when you have many things nested inside of each other and defined relatioinships.

```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
AuthorModel.findOne({name: "Bob"}, function(results){
  console.log(results);
});
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOneAndUpdate({name: "Andy"}, {$push: {wishlist_items: {description: "Resin Laying Deer Figurine, Gold"}}} function(instructor){
  console.log(instructor);
})

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
Author.create(name: $stateParams.name)
  redirect_to "/authors"

```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports - allows us to separate js files by exporting their content to be used a global variable. Simply add a require('whereever exporting from') and anything you put set module.exports = to will be brought into the other js file.
separation of concerns
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/", function(req, res){
  Model.find({}, (models) => {
    console.log("all our models: " + models)
  })
})

app.get("/models/:name", function(req, res){
  Model.findOne({name: req.params.name}, (model) => {
    console.log("found this model": model)
  })
})

app.post("/models/:name/new", function(req, res){
  Model.create(req.body.newModel).then((newModel) => {
    console.log(newModel + " was created")
  })
})

app.post("/models/:name/delete", function(req, res){
  Model.findOneAndRemove({name: req.params.name}).then((res) =>{
    console.log('model was deleted')
  })
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is less opinionated and lighter weight. More freedom in the structure of the app, routes, resources, and managing dependencies, but Rails is more structured and required a certain way and progress of things.

Express is more adaptable and rails is more rigid.


```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
allows us to use forms in our application to collect information so we can create new models. particularly using req.body.(whatever variable). This allows us to extract the information from the form to send to the backend and store it in our db there.

bodyParser.json = handles json post requests
urlencoded = handles form submissions.

require('body-parser')- allows our app to use the dependency and configured it to do so.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
