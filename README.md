# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
NoSQL is a no relational database (no relationships, 1-1 or 1 to many etc). Use NoSQL for flexibility and faster process time. Use SQL for structure and when you need relations.   
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.findOne({name: "Bob"})
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
var andy = Instructor.findOne({name: "Andy"})
andy.wishlist_items.create({description: "Resin Laying Deer Figurine, Gold"})
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
@author = Author.new(body_params)
if @author.save!
  redirect_to @author
else
  redirect_to root_path, alert: "error"
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
Encapsulated code in a special object that can be utilized in other files.
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

app.get("/pets", (req, res)=>{
  res.send(`hello world`)
})

app.post("/pets", (req, res)=>{
  Pet.create(req.body.pet).then((pet)=>{
    res.redirect(`/pets/pet.name`)
  })
})

app.post("/pets/:name", (req,res)=>{
  Pet.findOneandUpdate({name: req.params.name}, req.body.pet, {new: true}).then(()=>{
    res.redirect(`/pets/pet.name`)
  })
})

app.post("/pets/:name/delete", (req,res)=>{
  Pet.findOneandRemove({name: req.params.name}).then(()=>{
    res.redirect(`/pets`)
  })
})
```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is un-opinionated and more flexible/freedom, Rails is opinionated and has conventions with lots of default files on initial setup. Express is lean framework, Rails is not.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Bring in the body-parser middleware we installed into our file to use and store this to a variable to reference throughout the file. Second line is to handle json post request. The third line is to handle form submissions. 
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
