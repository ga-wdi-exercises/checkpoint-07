# Week 10

## Mongoose

### Question 1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
A sequel database contains information that follows a specific format. This kind of database may be used when storing items in a store. A noSQL database is a database that doesn't follow a specific format. You can store entire javascript objects in these types of databases. Hospitals may tend to store their patient records in a NoSQL database
```

### Question 2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.findOne({name: "Bob"})
console.log(results)
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// Your answer...
```

### Question 3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code...

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
const andy = Instructor.findOne({name: 'Andy'});
andy = andy.wishlistItems.create({description: "Resin Laying Deer Figurine, Gold"})
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
@author = Author.create({name: params['name']})
@author.save!

redirect_to authors_path
```

## Express

### Question 5

What is `module.exports` and why do we use it?

```text
module.exports allows us to import code from other files. What ever is wrapped in the curly brakets after module.exports can be used on what ever page requires it.
```

### Question 6

Write one Express route for each of the four CRUD actions.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express")
var app = express()

// Your code starts here...
app.get('/authors', (req, res)=> {
    res.send('GET Read')
})

app.post('/authors', (req, res)=> {
    res.send('POST Create')
})

app.put('/authors/:name', (req, res)=> {
    var author;
    Author.findOne({name: req.params.name}, (err, author)=> {
        if(err){
            console.log('Author doesn't exist')
        } else {
            author.name = req.body.name;
            author.save((err)=> {
                if(err){
                    res.send(err)
                } else {
                    res.send('PUT Updated')
                }

            })
        }

    });

})

```

### Question 7

Describe the differences between Express and Rails as backend frameworks.

```text
Express is a minimalist framework designed for developer configuration. The developer is given the option to import the modules they would like to use in their application. Rails is designed for convention. There are many set practices and procedures the developer is expected to follow when creating a rails app.
```

### Question 8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text

```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
