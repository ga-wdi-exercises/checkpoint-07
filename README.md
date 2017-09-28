# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

SQL: is a relational table. If you delete something in one table, have to delete the same row in connected table. Because of the relations, it can slow down the application. More likely to be used in Ruby

NoSQL: database that doesn't have to have relations. Used when data requirements aren't clear of if you're dealing with a lot of unstructured data

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
console.log(results.name)
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: 'Andy'}).then(function(response){
  response.wishlist_items.push({description: "resin Laying Deer Figurine, Gold"})
}
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
author = Author.new(name: params[:name])
author.save
redirect_to "authors_path"
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
it exports code found in one file and makes it available to every other file in the same project
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get("/", function (req, res){
  Item.find({}).then(function(items){
    res.render("Get Method")
  })
})

app.post("/items", function (req, res){
  Author.create(req.body.name).then(function(){
    res.send("Create method")
  })
})

app.post("/items/:name", function (req, res){
  Item.findOneAndUpdate({name: req.params.name}, req.body.item, {new:true}).then(function(item){
    res.render('Update method')
  })
})

app.post("/items/:name/delete", function(req, res){
  Item.findOneAndRemove({name: req.params.name}).then(function(){
    res.render('Delete method');
  });
});

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is very minimalist and doesn't make you follow its conventions. Rails is very opinionated and makes you follow its conventions*/
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
it allows you to get access to the data when you type app.post()
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
