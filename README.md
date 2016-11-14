# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
SQL databases are relational databases comprised of tables, whereas NoSQL are non-relational comprised of documents. One might prefer NoSQL when data consistency is not a priority, and therefore the flexibility of non-relational data structures would be optimal.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
// You need a callback function to persist the data and actually do something with it:
var results = AuthorModel.findOne({name: "Bob"}, function(){
  console.log(results);
});

```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
People.findOne({name: "Andy"}, function(andy){
  andy.wishlistItems.create({description: "Resin Laying Deer Figurine, Gold"})

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
author = Author.new(params[:name])

```
## Express

### Question #5

What is module.exports and why do we use it?

```text
This exports the variables or portions of code from one file so that it can be used from another file. For example, you would export the model in order that it would be accessible from another file containing your app code.

```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();



app.get("/things", function(req, res) {
  Thing.find({}).then(function(things){
    res.render("things-index", {
      things: things
    })
  })
})

app.get("/things/:name", function(req, res) {
  Thing.findOne({thing: req.params.name}).then(function(thing){
    res.render("things-show", {
      thing: thing
    })
  })
})

app.post("/things/specific/delete", function(req, res) {
  Thing.findOneAndRemove({name: req.params.name}).then(function(){
    res.redirect("/things")
  })
})

app.post("/things/specific", function(req, res) {
  Things.findOneAndUpdate({name: req.params.name}, req.body.thing, {new: true}).then(function(){
    res.redirect("/things" + thing.name)
  })
})



```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Aside from the fact that Express runs from a non-relational database (MongoDB), and (to my knowledge) Rails runs on relational ones (like PostgresQL or SQL), Express is unopininated, meaning it doesn't adhere to the convention over configuration mindset that is the backbone of Rails. Instead, Express allows greater freedom for developers to structure their programs/apps as they see fit. While this can (and often does) lead to complications for collaboration and restructuring, it can be a better fit for developers looking to innovate and diverge from the hive-mind approach of the greater web development community.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
This code sets you up to `npm install body-parser`, which is middleware needed to get form data and JSON data in a POST request for express applications. As mentioned above, a body-parser (RACK) is included with Rails out of the box, but unopinionated Express no longer includes in original package.
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
