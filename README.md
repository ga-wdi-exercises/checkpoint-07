# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL DB, and when you might use each.

```text
A SQL database is a relational database in which entries are organized in tables where each item has it's own row and unique identifier. Relational databases can be used to store data for just about any project you might come across. A NoSQL database is -- quite simply -- one that does not use the tables mentioned above to store data. As a result, NoSQL databases can often be significantly faster when dealing with huge amounts of entries.
```

### Question #2

What's wrong with this mongoose code and how might we fix it?
(Hint: Assuming there is a document with a name of "Bob", why is results not an author model on the second line?)

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

```js
// Needs a callback
AuthorModel.find({name: "Bob"}).then((err, res) => {
  if (err) { console.log(err) }
  else if (res) { console.log(res) }
})
```

### Question #3

Convert the following ActiveRecord sequence to Mongoose:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOneAndUpdate({name: "Andy"}, {wishlist_items: "Resin Laying Deer Figuring, Gold"}, {new: true}).then(res {
  console.log(res)
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
@author = Author.create!({name: params[:name]})
```
## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports is a node method that allows you to access modules from separate files within your app. We use it to make our apps more "modular" (i.e. breaking a program up by individual functions or purposes), which is one of the strengths of NodeJS.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get('/', (err, res) => {
  if (err) { console.log(err) }
  else if (res) {
    res.send('Read')
  }
})

app.post('/', (err, res) => {
  if (err) { console.log(err) }
  else if (res) {
    res.send('Create')
  }
})

app.put('/:id', (err, res) => {
  if (err) { console.log(err) }
  else if (res) {
    res.send('Update')
  }
})

app.put('/:id', (err, res) => {
  if (err) { console.log(err) }
  else if (res) {
    res.send('Destroy')
  }
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Language-wise, Rails is written in Ruby and Express in JavaScript. In terms of functionality, Rails is an opinionated framework in which controller names, models, routes, etc., need to be named following specific conventions to match assumptions made by the runtime. Express is very much the opposite, where "rules", for lack of a better term, do not exist.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
Body-parser is Node middleware that provides helper methods to parse incoming data. It can handle JSON, Raw Text, and URL-Encoded Form data. The example above sets up body-parser to parse JSON requests as well as URL Encoded requests.
```

### If you finish early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
