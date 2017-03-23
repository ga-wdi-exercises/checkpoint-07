# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQl - Sequential query language -  is a method of storing data in which the schema is relational and uses a object relational modelling for presentation of database

NoSql - databases that are non-relational, and used an ODM for access of data. Object based languages -  Json file
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
 .find({}) - finds all the object key value pairs that belong to the specification given in the "{}"
var results = AuthorModel.findOne({name: "Bob"});
console.log(results);
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne({name: "Andy"}, function(err, instructor){
  if(err){
    console.log(err)
  }else{
    console.log(instructor)
  }
});
    andy.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})
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
 Adrian = Author.create(:name => 'Adrian')
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports - helps you export a module in which includes a functionality(all the functionality of a mongoose module) and definition of the module that you specified while defining your module and give you the power of CRUD over those defined modules
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get('/', function(req, res){
  res.send("home page")
})

//read
app.get('/restaurants', function(req, res){
   Restaurant.find({}).then(function(results){
     res.render(result)
    //  res.send(result)
     console.log("Show-all")
   })
})

//create
app.post("/restaurants/:name" , function(req, res){
  Restaurant.Create(name: req.body.restaurant).then((restaurant) => {
    res.redirect("/restaurants/" + restaurant.name )
   console.log('create')
})
})

//edit
app.post("/restaurants/:name" , function(req, res){
  Restaurant.findOneAndUpdate({name: req.params.name}, req.body.restaurant, {new: true}).then((restaurant) => {
    res.redirect("/restaurants/" + restaurant.name )
   console.log('edit')
})
})

//delete
app.post("/restaurants/:name/delete" , function(req, res){
  Restaurant.findOneAndRemove({name: req.params.name}.then(() =>{
    res.redirect(/restaurants)
    console.log('delete')
  })

});

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text

express - Javascript based - there is no such thing as convention over configuration. you can do the way you want things.

Rails - ERB based language - Always "convention over configuration"

```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
body-parser - helps is used in-order to read HTTP Post data
            - is a piece of express middleware that reads a forms input and stores it as a javascript object accessible through req.body

var bodyParser = require("body-parser")
1. requires a module named body-parser to be loaded, for this to work we first have to save in our app(npm install --save body-parser)

app.use(bodyParser.json())
2. tells the app to make use of body-parser

app.use(bodyParser.urlencoded({extended: true}))



```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
