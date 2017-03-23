# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

//ANSWER//
``SQL, which include programs like MySQL & PostgreSQL is relational.  NoSQL, which includes programs like Firebase & MongoDB are non-relational.  
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// Your answer...
//ANSWER//
Model.findById(someId, callback)
Because we need to console.log the proper string.
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
//Answer??
var Andy = InstructorModel.findOne(Andy, {"Resin Laying Deer Figurine, Gold"}, callback )
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
# Your answer...

//Answer//
class Authors < ActiveRecord::Base
  has_many :books
end

```

## Express

### Question #5

What is module.exports and why do we use it?

```text

//Answer//
<!-- Module.exports allow us to separate our js files by exposing their contents as one global variable. We use them because defining routs can be very tedious.  module exports allow for more granular control. -->

```

### Question #6

Write one Express route for each of the four HTTP methods.


Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.


```js
var express = require("express");
var app = express();

// Your code starts here...

//Answer//
app.get('/locations', function (request, response) {
  var cities = ['Caspiana', 'Indigo', 'Paradise'];
  response.send(cities);

app.post('/locations', function (request, response) {
    var cities = ['Caspiana', 'Indigo', 'Paradise'];
    response.send(cities);

app.put('/locations', function (request, response) {
        var cities = ['Caspiana', 'Indigo', 'Paradise'];
        response.send(cities);  

app.delete('/locations', function (request, response) {
            var cities = ['Caspiana', 'Indigo', 'Paradise'];
            response.send(cities);
});
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is part or "the mean stack" and associated with Javascript-based frontends.  Rails is a backend Associated with Ruby.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
// Answer//
It enables bodyParser, a form a middleware. Middleware is code that runs in between receiving the request and responding. Body-parser used to be included to Express, but they took it out.And so we need to install middleware in order to get form data and JSON data in a POST request for Express applications.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
