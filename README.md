# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A SQL database will usually have tables that require relationships while a NoSQL database doesn't need relationaships. Also you can't use join tables in NoSQL
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(AuthorModel)
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findById(name: "Andy")
var andy.wishlistItems = ne
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
get 'authors' do
  @authors = Authors.all
  erb: "authors/index"
end
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
A special object which is included in every js file in the Node.js application by default. Module is a variable that represents current module and exports is an object that will be exposed as a module
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get("/", function(req, res){
  res.render("./index");
});

app.post("/candidates", function(req, res){
  Candidate.create(req.body.candidate).then((candidate) =>{
    res.redirect("candidates/" + candidate.name)
  })

  destroy: function(req){
    AuthorModel.findOneAndRemove(req, function(err, docs){
      if(err){
        console.log(err);
      }
      else{
        console.log(docs);

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is a heavy framwork meaning that when creating an application with rails it assumes that you will need a lot of files and will create them.

Express is a lean framework meaning that it will start you off with the bare minimum and you can add as needed.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
app.use(bodyParser.json()) - Handels json post requests
app.use(bodyParser.urlencoded({extended: true})) - handles form submissions
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
