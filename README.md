# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL database would store the data as tables. NoSQL database would store the data in documents and collection form.
I would use NoSQL in many projects since it is a little faster and I could have more freedom using it. I might also use SQL database when working on a rails application that would include many complicated relationship, in that case I personally prefer SQL database....
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorSchema.findOne({name: "Bob"})
console.log(results)...
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne({name: "Andy"})
andy.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})...
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
@author = Author.new(name: @name)
if author.save
  redirect_to "/authors"
end...
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
module.exports allow the data to be accessed by other files. We use this technique to direct information needed to the right files where they are being used....
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get("/", (req, res) => {
  var voters = Voters.find({})
  res.render("voters-index", voters: voters)
})

app.post("/", (req, res) => {
  Voters.create(req.body.voters).done(voter => {
    res.redirect("/")
  })
})

app.get("/:id", (req, res) => {
  var voter = Voters.findOne({_id: req.params.id})
  res.render("voters-show")
})

app.post("/:id", (req, res) => {
  var voter = Voters.findOne({_id: req.params.id})
  Voters.findOneAndUpdate({_id: req.params._id}, req.body.voter, {new: true}).then(voter => {
    res.redirect(`/${req.params.id}`)
  }).fail(err => {
    console.log(err)
  })
})

app.post("/:id", (req, res))
  Voters.findOneAndDelete({_id: req.params._id}).then( => {
    res.redirect("/")
  })
```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Express backend frameworks is a lot more customizable than Rails which is a good advantage for someone with a clear picture of what exactly they want to build, express also makes it a little easier as far as writing less code and working with less files. On the other hand, Rails conventions limits the developer freedom by it does keep the developer on track with all the conventions. Also, Rails beats Express by far with their amazing error handling pages....
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
We are defining the body-parser in the first line so it could be used on this file. We are then asking it to read the request page in json in order to identify the information. On the third line, we are asking body-parser to bring all the nested object, if this is not set to true then we will be parsing strings and arrays. ...
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
