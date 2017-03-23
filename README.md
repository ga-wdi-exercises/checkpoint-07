# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are RDBMS; whereas NoSQL databases are primarily non-relational or distributed database. You would use a SQL if you data is table based and a NoSQL database if you want a document based, key-value pair, or graph database.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// it needs a callback
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
// var instructor = [Andy]
// instructor.find({name:Andy})
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
# Author.create(:name => 'Bob')
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
<!-- the utility of having module.exports is that you can encapsulate code in a file that can then be utilized in other files-->
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// app.get('/', function(req, res) {
//   res.send('Hello World');
// });
// app.patch('/:name', (req, res){
// res.render("show")
// });
// app.post("/new", (req, res)
// res.redirect('/')
// });
// app.delete('/:name', (req, res){
// res.redirect('/')
// });

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
<!--Express differs from Rails most notably from being less opinionated. Express allows you more freedom to set up your skeleton how you would like. Rails operates with a MVC framework and Express is a MVVM framework. There seems to be endless debate on which one is "better" but both have their strengths and weaknesses.  -->
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
<!-- body-parser extracts the entire body portion of an incoming request stream and exposes it on req.body as something easier to interface with. (Answer found @ "https://www.quora.com/What-exactly-does-body-parser-do-with-express-js-and-why-do-I-need-it")-->
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
