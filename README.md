# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
Sql - table based and NoSQL- document based.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
AuthorModel.find({name: "Bob"}).then(function (results) {
  console.log(results)
})

```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
let andy = Instructor.find({name: "Andy"}).then((description) => wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})
})
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
def new
  @authur = Author.new
end

def create
  author = Author.create!(author_params)
  redirect_to "/authors"
end

```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
this is object included in every JS file in Node.js app by default, where module is variable that represents current module and exports is an object that will be exposed as a module

we use this because it allows us to export values, objects and styles from Node.js modules.
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get('/', (req, res) => {
  res.send("hola")
})

app.post('/posts', (req, res) => {
  console.log("hola")
})

app.post("/posts/:comments", (req, res) => {
  posts.findOneandUpdate({req.params.comments}), req.body.posts, {new: true}) res.redirect('/posts/' + posts.comments);
})

app.post("/posts/:comments/delete", function(req, res){
  posts.findOneandRemove({req.params.name}).then(function(){
    res.redirect('/posts');
  })
})
```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Express - faster and more flexibility
Rails - slower and convention over config
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
var bodyParser = require("body-parser")-- requires bodyParams as bridge between the system and the db app?  (i think this is the write answer but i need clarification )

app.use(bodyParser.json()) - tells the system you want to use json

app.use(bodyParser.urlencoded({extended: true}))- form submission

```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
