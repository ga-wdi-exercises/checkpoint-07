# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
NoSQL is a non-relational database. It's more flexible than SQL database, scalable and is generally faster. In NoSQL all the data is stored in JSON objects. SQL databases with tables and columns, however, are easier to understand, and has a long history of support and tools.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"}, () => {
  console.log(results);
})
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// JS is asynchronous, meaning that most likely console.log will fire before the results of the .find methods will finish running, which would then print nothing. Console.log must be either used either inside of a callback or inside of a promise.
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
app.put("#", (item, res) => {
  Instructor.findOneAndUpdate({name: "Andy"}, item.body, {new: true}, (docs) => {
    console.log(docs);
  })
})
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
author = Author.create(:name => params[:name])
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
It exports a variable with the values that were already assigned from one file to another. We then can use it as dependency and have all the values and properties available.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get("/index", (req, res) => {
  Thing.find({}, (things) => {
    res.render("index", {things})
  }
})

app.get("/show/:name", (req, res) => {
  Thing.findOne({name: req.params.name}, (thing) => {
    res.render("show", {thing})
  })
})

app.post("/index", (req, res) => {
  Thing.create(req.body.thing, (thing) => {
    res.redirect(`/index/${thing.name}`)
  })
})

app.post("/index/:name", (req, res) => {
  Thing.findOneAndUpdate({ name: req.params.name }. req.body.thing, { new: true }, (thing) => {
    res.redirect(`/index/${thing.name}`)
  })
})

app.get("/index/:name/delete", (req, res) => {
  Thing.findOneAndRemove(req => {
    res.redirect("/index")
  })
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
// Express is much more like Sinatra than Rails. Rails has it's way, and it's the only way. If you don't do what it wants, it's not going to agree. Express is like Sinatra(and after studying Express I have a newfound appreciation for it), in a way that yeah you can follow this convention, but it doesn't really care. It's customizable and has way less conventions that you may or may not choose to follow. It's modular and does require more setup than just rails s, but it's a worthwhile trade-off.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
// bodyParser.json() parses text as JSON and shows the resulting object in the body.
// bodyParser.urlencoded({extended: true}) parses text as URL encoded data, and shows the resulting object in the body.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
