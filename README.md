# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
  The difference between the two is that SQL(ORM) is a relational database while NoSQL(ODM) is a non-relational database. Which means that there is no explicit one to one, one to many, or many to many database.

  You may use want to use NoSQL over SQL because it's flexible(you don't have to use a schema), fast(data is denormalized), and if we use javascript on both ends, it's easier.

```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
// Your answer...
```

### Question #3

Convert the Ruby and ActiveRecord code below into Javascript and Mongoose code:

```rb
@andy = Instructor.find_by(name: "Andy")
@andy.wishlist_items.create(description: "Resin Laying Deer Figurine, Gold")
```

```js

Instructor.findOne({name: "Andy"}, (err,obj) =>{
  console.log(obj)
})

var wishlist_item1 = new Wishlist_Items({description: "Resin Laying Deer Figurine, Gold"})
// add wish list to instructor collection
andy.wishlist_items.push(wishlist_item1)
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
def create
  @author = Author.find(params[:author_id])
  @author = @author.create!(author_params)

  redirect_to author_path(@author)
end
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
We use it to connect our current page with our other files and to separate our concerns.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

app.get('/', function (req, res){
  res.send('Hello World!')
})

app.post('/', function (req, res){
  res.send('Got a POST request')
})

app.put('/user', function (req, res) {
  res.send('Got a PUT request at /user')
})

app.delete('/user', function (req, res) {
  res.send('Got a DELETE request at /user')
})

```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Express uses javascript while Rails uses ruby.
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
It allows you to use body-parser. Which is middleware. It is a code that runs in between receiving the request and responding. It helps us get and send info for forms.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
