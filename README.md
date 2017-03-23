# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL database: a relational database - great to use when dealing with complex domain models (relational tables). Downside: slows down our app.
noSQL database: non-relational database (document based) - great to use when working with a flexible data model, that involves similar but different objects.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
function findByName(author) {
  Author.findOne({name: author}, function(err, author) {
    if(err) {
      console.log(err)
    } else {
      console.log(author)
    }
  })
}
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
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
def new
  @author = Author.new
end

def create
  @author = Author.create!(author_params)
  redirect_to authors_path
end

private
def author_params
  params.require(:author).permit(:name,)
end
end
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports is used when we'd like to make something within our file publicly accessible to anything (required) outside the file.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var parser   = require("body-parser");
var app = express();


var Movie = mongoose.model("Movie")

 // show all movies
app.get("/movies", function(req,res) {
  Movie.find({}).then( (err, movies) => {
    if(err) {
      return res.send(err)
    } else {
      res.send("Movies!")
    }
    movies: movies
  })
})

// show each movie
app.get("/movies/:name", function(req,res) {
  Movie.findOne.({name: req.params.name}).then( (movie) => {
    if(err) {
      return res.send(err)
    } else {
      res.send("Movie")
    }
    movie: movie
  })
})

 // add a movie (assuming there is a form to create a movie)
 app.post("/movies", function(req,res) {
   Movie.create(req.body.movie).then( (movie) => {
     res.send("Created")
   })
 })

  // delete a movie
  app.post("/movies/:name/delete", function(req, res) {
    Movie.findOneAndRemove({name: req.params.name}).then( () => {
      res.send("Deleted")
    })
  } )

  // update a movie
  app.post("/movies/:name", function(req, res) {
    Movie.findOneAndUpdate({name: req.params.name}).then( () => {
      res.send("Updated")
    })
  })

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is a backend framework that supports Node.js / JavaScript front-end language, and uses Mongoose as database with Mongo.
Rails is a backend framework that supports Ruby front end language, and uses SQL database with ActiveRecord.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Renders seed data.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
