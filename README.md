# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A NoSql database is a non-relational database and allows for faster querying because data is denormalized. It is also more flexible because a schema does not need to be followed. A SQL database is a relational database and is used to establish one-to-many and other types of relationships between data.
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
We use .findOne to find a specific model, .find would return all of the models.

var results = AuthorModel.findOne({name: "Bob"}, callback)
console.log(results)
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne({name: "Andy"})
var andy.wishlistItems.create(description: "Resin Laying Deer Figurine, Gold")
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
  @author = Author.new
end

def create
  @author = Author.create!(name: params[:name])
  redirect_to authors_path(@author)
end
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
module.exports allows us to define the object being brought in by require().
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get("/", (req, res) => {
  res.send("Get");
})

app.post("/persons", function(req, res){
  Person.create(req.body.person).then((person) => {
    res.send("Post");
  })
});

app.post("/persons/:name", function(req, res){
  Person.findOneAndUpdate({name: req.params.name}, req.body.person, {new: true}).then((person) => {
    res.send("PUT");
  });
});

app.post("/persons/:name/delete", function(req, res){
  Person.findOneAndRemove({name: req.params.name}).then(function(){
    res.send("Delete");
  });
});
```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails relies on convention over configuration and is a heavy framework. Many needed programs are included such as middleware. Express is suppose to be a light framework that allows a high level of custom configuration. Express has the advantage of being able to use Javascript on the backend.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
body-parser is a middleware that is needed to talk between the front-end and back-end frameworks in Javascript. The lines above require the use of it and allow data to be sent as json in the first .use and as html in the second .use.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
