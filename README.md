# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL database has relationship as NoSql database does not. NoSql database is used with mongoose to avoid latency.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
app.get("/authors/:name", function{req, res}){

}
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
function findByname(name) {
  Instructor.find({name: name}, (instructors) => {
    console.log(instructors)
  })
}
`

### Question 4

Convert the following create method in Mongoose to ActiveRecord...

```js
var author = new Author({name: req.body.name})
author.save(function(err){
  if (!err){
    res.redirect("authors")
  }
})
```

```rb
@author.name.new("Author")
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
Module.exports allows us to import code from one file to another. When you want an object returned to require a function instead of just properties with object and then module.exports is used.
```

### Question 6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get('/', function(req, res){
  res.send('hello world');
});

app.Post('/api/car', function(req, res){
  Car.create(req.body).then(function(food){
    res.json(food)
  });
});


app.put('/api/car', function(req, res){
  Car.findOneAndUpdate({shop: req.params.shop}, req.body, {new: true}).then(function(car){
    res.json(cars)
  });
});

app.put('/api/car', function(req, res){
  Car.findOneAndUpdate({shop: req.params.shop}, req.body, {new: true}).then(function(car){
    res.json(cars)
  });
});


```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Express contains just Javascript and rails is under ruby and different language and doesnt use Javascript
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Need body-parser and we can reference it
app.use(bodyParser.urlencoded({extended: true})) = It configures the parser to support html forms.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
