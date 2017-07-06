# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL is relational database in which the relation is explicitly defined. And this relation make it our database rigid
in order to make sure the relationship. E.g. Postgresql
NoSQL is no relational database, its good for random data in which there is no strict relation. But if we need relation
also we can implement using embedded documents. E.g. Mongo
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// find is used to find all documents, not for a single document. So the correct way will be:
var results = AuthorModel.findOne({name: "Bob"},(err,results)=>{
  if (err){
    console.log(err);
  }
  else{
    console.log(results)
  }
})
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne({name: "Andy"})




```

### Question 4

Convert the following create method in Mongoose to ActiveRecord...

```js
var author = new Author({name: req.body.name})
author.save(function(err){
  if (!err){
    res.redirect("/authors")
})
}
```

```rb

def new
  @author = Author.new
end
def create
  @author = Author.create!(name: name)
end
redirect_to authors_path

```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
// We use module.exports to export/reference models defined in one page and use it in other pages
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.listen(4000, () => {
  console.log("app listening on port 4000")
})
app.get("/", function(req, res){
  res.render("index",{})
});
app.post("/:name/delete", function(req,res) {
  Students.findOneAndRemove({name:req.params.name}).then(()=>{
    res.redirect("/")
    })
})
app.post("/:name/edit", function(req,res) {
  Students.findOneAndUpdate({name:req.params.name},req.body.student,{new:true}).then(()=>{
    res.redirect("/"+ student.name)
    })
})
```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
// Express is un-opinionated framework meaning we have freedom in configuration and structuring our application.
// In other hand, Rails is opinionated framework which means prefer "convention over configuration".
// Express uses node.js.In other hand, Rails uses Ruby.
// Express uses ODM(Object Data Mapping) .In other hand, Rails uses ORM(Object Relation Mapping).
// Express uses Mongoose as ODM.In other hand, Rails uses ActiveRecord as ORM.
// Express uses Mongo as database.In other hand, Rails uses Postgresql for database.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
// The first line is used to configure the application to use body parser module
// The second line used to handle AJAX request with JSON bodies
// The third line used to handle form submissions and to make the form properly work

```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
