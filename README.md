# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
NoSQL: non-relational database
  -uses documents and collections instead of rows and tables
  -makes it easier to handle and send data between client and database
  -faster, more flexible
  -automatic scaling
SQL: relational database
  -make queries to get data thats connected through a relation
  -explicit relationships
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
if you're finding just one instance then you need to use .findOne; you would console.log(author) instead of results
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js
Instructor.findOne({name: "Andy"}, (err, instructor)=>{
  console.log(instructor)
})

Instructor.create({name: "Andy", description: "Resin Laying Deer Figurine, Gold"}, (err, instructor)=>{
  instructor.save((err, instructor)=>{
    if(err){
      console.log(err)
    }
    else {
      console.log(instructor)
    }
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

class Author < ActiveRecord
def change
  create_table :authors do |t|
  t.string :name
end
end
end

Author.destroy_all

Author.create!(name: "")
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
it is a reference to the current module/object and exporting it to another file when you do "require"
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get('/', (req, res) =>{
  res.send("hello world")
})

app.post('/', (req, res)=>{
  Model.create(req.body.model).then((model)=>{  
  res.send("post created")
})
})

app.post("/:name", (req, res)=>{
  Model.findOneAndUpdate({name: req.params.name}, req.body.model, {new:true}).then((model)=>{
    res.send("updated")
  })

})

app.post("/:name/delete", (req, res)=>{
  Model.findOneAndRemove({name: req.params.name}).then(()=>{
    res.send("deleted")
  })

}

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
-Express:NodeJS::Sinatra:Ruby
-Express is not as strict as Rails and much lighter weight, and faster
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
body parse is used in order to read POST data HTTP requests in express; it is middleware that read's a input from a form and stores it as an object which is access by req.body
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
