# Week 10

## Mongoose

### Question #1

Describe the differences between a SQL and NoSQL database, and when you might use each.

```text
SQL databases are relational, so items on different tables can be linked by a join table. NoSQL are document based, so they are more flexible about how data is entered, but not designed with the rigid structure of tables to make the data conform to a specified structure as well.
```

### Question #2

What's wrong with this Mongoose code and how might we fix it?

```js
var results = AuthorModel.find({name: "Bob"});
console.log(results);
```

> Hint: Assuming there is a document with a name of "Bob", why does `results` not contain an author model on the second line?

```js
var results = AuthorModel.find({name: "Bob"}, function(results, err) {
  if (err){
    console.log(err);
  }else{
    console.log(results);
  }
});
// Your answer...
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
def create
  @author = Author.new(author_params)
  @author.save!
  redirect_to @author
end
```

## Express

### Question #5

What is module.exports and why do we use it?

```text
module.exports is what we use to make models, schema, seeds, and other data available to other js docs that have `require` constants. It tells the program what specifically needs to be lifted from the exporting doc and imported where required.
```

### Question #6

Write one Express route for each of the four HTTP methods.

Then, make each route respond with a one-word string containing the RESTful action that would most likely be associated with this route.

```js
var express = require("express");
var app = express();

// Your code starts here...
app.get("/cookie", function(req, res){
  Cookie.findOne({ name: req.params.cookie }).then(function(cookie){
    res.json(cookie)
  })
})

app.post("/cookie", function(req, res){
  Cookie.create(req.body).then(function(cookie){
    res.json(cookie)
  })
})

app.delete("/cookie", function(req, res){
  Cookie.findOneAndRemove({ name: req.params.cookie }).then(function(){
    res.json({ success: true })
  })
})

app.put("/cookie", function(req, res){
  Cookie.findOneAndUpdate({ name: req.params.cookie }, req.body, { new: true }).then(function(cookie){
    res.json(cookie)
  })
})
```

### Question #7

Describe the differences between Express and Rails as backend frameworks.

```text
Rails is opinionated, express is not. Because of this, rails is simpler, but not as flexible. Rails is designed to work with ActiveRecord and SQL databases, and while it can be adapted to work with a NoSQL database, Rails does not encourage this practice. Express requires more thought and effort to set up, since the developer needs to make choices about the architecture from the outset. We have worked with Express with a mongo database, which is document based, not relational, which calls for a different ORM and schema structure. 
```

### Question #8

What do the following lines of code do?

```js
var bodyParser = require("body-parser")
app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: true}))
```

```text
This code brings in the `body-parser` node module. body-parser used to be a part of the core node installation, but was removed, so it needs to be explicitly brought in. body-parser allows the app to take data input on the front end and send it to the back end as json, and to change to json data to utf-8 charaters for optimal viewing.
```

### If You Finish Early...

Take a look at these [front end developer interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/README.md)
