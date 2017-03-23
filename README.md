# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL is a relational database, NoSql is a non relational database. Sql have been the traditional databases for decades. SO Sql is the go to source typically one would use SQL for large applications that had a specific need and specific relationships. With mongo/nosql it takes a far more distributed modular approach towards getting specific data in specific way, that being said NoSQL is useful because it can incorporate both sql and nosql stuff. Nosql is often used for gaming . SQL for larger corporation databases.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
let results = AuthorModel.findOne( 'results', {name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
because there should have been given two arguments inside the findOne
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb

@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// Your answer...
let andy = new Instructor.findOne('Instructor', {name: "Andy"})
andy.wishlist_items.create('schemaValue', {description: "Resin Laying Deer Figurine, Gold"})
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
author.create!
# Your answer...
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
it allows us to export all of the functions that we may need to use in
another file.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/candidates", function(req, res) {

    Candidate.find({}).then((candidates) => {
        res.render("candidates-index", {
            candidates: candidates
        });
    })

});

app.post("/candidates", (req, res) => {

        Candidate.create(req.body.candidate).then((candidate) => {
            res.redirect(`/candidates/${candidate.name}`)
        })
    })
    
    app.post("/candidate/:name", (req, res) => {
    Candidate.findOneAndUpdate({
        name: req.params.name
    }, req.body.candidate, {
        new: true
    }).then((candidate) => {
        res.redirect(`/candidates/${candidate.name}`)
    })
})

app.delete('/api/recipes/:recipe', (req, res) => {
    Recipe.findOneAndRemove({
        recipe: req.params.recipe
    }, () => {
        res.json('/recipes')
    })
})


```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
First off, Rails is all about convention, and Express has far more freedom. Express and node are often faster because theyre lighter weight, this is important when devleoping SPAs( less middleware).
However with the express freedom we have to be more proactive about what tools we are going to use because they are not explicitly told/given to us on a fresh init.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Body parser does pretty much what it says, it parses the entire body of the html document making it easier to take apart and reassemble how one would like.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
